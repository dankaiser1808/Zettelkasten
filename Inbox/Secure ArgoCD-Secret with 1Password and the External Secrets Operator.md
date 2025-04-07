#substack
## Let’s focus a little bit more on security

Today, I’m going to show you how to use the External Secrets Operator (ESO) to dynamically create and update Kubernetes secrets stored in an external secrets manager.

We’ll start with the 1Password Connect Server, move on to the External Secrets Operator, and finally look at a real-world example where ESO reads from the external vault and manages Kubernetes secrets for us.

In this case, we’ll automate the ArgoCD admin secret, and I’ll walk you through how to handle the classic _chicken-and-egg problem_ it introduces.

## Requirements

If you want to follow along, make sure you have a valid 1Password account and an already created vault. I really like 1Password - I’ve been using it for years as my personal password manager on all my devices. The annual cost is about $36, which is a great deal for the security and convenience it provides.

## One Password Automation Workflow 

1Password defines an automation workflow as a process that allows developers and DevOps teams to securely retrieve and manage secrets, integrating them into your automation system of choice.

We're going to use the 1Password Connect Server as part of our [automation workflow](https://developer.1password.com/docs/connect/) and use it to read secrets via their external API.

### Install the CLI

First, install the 1Password CLI. We'll need it to create several required objects for the Connect Server and the External Secrets Operator:

```
brew install --cask 1password-cli
```

### Create the Connect Server object

Before deploying the Helm chart, we need to define the Connect Server and the vaults it will access:

```
op connect server create homelab-connect --vaults HomeLab
```

This will generate a 1password-credentials.json file on your client, which is required for the Connect Server deployment.

> Tip: You can grant access to multiple vaults with the `--vaults` flag.

This command will generate a _1password-credentialsd.json_ credentials file on your client device, which will be mandatory for our connect server helm deployment. Notice that _--vaults_ can include more than just one vault, we can add multiple vaults for our connect server if needed.

My personal preference is to store the initial credentials needed for setup in a separate vault from the secrets used by ESO in our Homelab. This improves security and follows the separation of concerns principle.

Create a second vault called InitHomeLab and save the 1password-credentials.json file there. 1Password makes this easy with built-in file storage.

```
OP_CREDENTIALS_PATH="op://InitHomeLab/1password-credentials/1password-credentials.json"

kubectl create ns "onepassword" --dry-run=client -o yaml | kubectl apply -f -

kubectl create secret generic op-credentials -n "onepassword" \
--from-literal=1password-credentials.json="$(op read "$OP_CREDENTIALS_PATH" | base64)"
```

What’s happening here:

- We create a namespace.
    
- We read the credentials file directly from the vault.
    
- We base64-encode it manually and inject it into Kubernetes as a secret.
    

> Kubernetes already base64-encodes secret values, so double-encoding is usually unnecessary. However, this is a current 1Password quirk, and the manual encoding is required for things to work correctly.

Create the umbrella Helm chart like this:

```
apiVersion: v2
name: onepassword
type: application
appVersion: "1.0"
version: 1.0.0
dependencies:
  - name: connect
    version: 1.17.0
    repository: https://1password.github.io/connect-helm-charts
```

Since we’re using ArgoCD’s Git directory generator (as covered in [my previous post](#)), we just commit this chart and let ArgoCD handle the deployment.

The Connect Server acts as a proxy with two big benefits:

1. Caching → Fewer API calls to 1password.com
    
2. Resilience → If 1Password is down, we can still use the locally cached secrets
    

## External Secrets Operator

https://external-secrets.io/latest/api/spec/#external-secrets.io/v1beta1.SecretStoreProvider

The [core idea of the ESO](https://external-secrets.io/latest/) is to connect with an external secrets manager, fetch secrets, and inject them as Kubernetes Secrets.

### Choose your SecretStore type

- ClusterSecretStore → Cluster-scoped
    
- SecretStore → Namespace-scoped
    

We’ll use ClusterSecretStore here for simplicity (I’ll cover SecretStore in a future post with the security benefits it provides). If you want to use the ClusterSecretStore in a production environment, make sure to [minimize RBAC permissions](https://external-secrets.io/latest/guides/security-best-practices/).

### Create the Connect Token

Before deploying ESO, create a token so it can authenticate with the 1Password Connect server:

```
op connect token create onepassword-connect-token --server homelab-connect --vault HomeLab
```

Save the token in your InitHomeLab vault, then create a Kubernetes secret from it:

```
OP_CONNECT_TOKEN=$(op read "op://InitHomeLab/onepassword-connect-token/password")

kubectl create secret generic onepassword-connect-token -n eso \
  --from-literal=token="$OP_CONNECT_TOKEN" \
  --dry-run=client -o yaml | kubectl apply -f -
```

### Helm Chart for ESO

We have to provide an umbrella chart the same way we did for the 1Password Connect chart:

```
apiVersion: v2
name: eso
type: application
appVersion: "1.0"
version: 1.0.0
dependencies:
  - name: external-secrets
    version: 0.12.1
    repository: https://charts.external-secrets.io
```

### Define ClusterSecretStore

```
apiVersion: external-secrets.io/v1beta1
kind: ClusterSecretStore
metadata:
  name: one-secretstore
  annotations:
    argocd.argoproj.io/sync-wave: '1'
spec:
  provider:
    onepassword:
      connectHost: http://onepassword-connect.onepassword.svc.cluster.local:8080
      vaults:
        HomeLab: 1
      auth:
        secretRef:
          connectTokenSecretRef:
            name: "onepassword-connect-token"
            namespace: "eso"
            key: "token"
```

Watch closely at the provided host. The helm chart of the OnePassword Connect server comes already with a service that we can use to access the proxy. If you want to learn more about Kubernetes DNS Recordss checkout the [official documentation](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/).

## External Secrets

External Secrets provide the Operator with the information of a secret that should be watched, fetched from the external secrets manager and transformed into Kubernetes secret. The operator will not only create the secret, it will also ensure that if the secrets change in the external source, to update the Kubernetes secrets accordingly. Be aware that this will not provide us with dynamically update secrets inside of our application in all cases. Secrets that are passed as environment variables always require a restart of the pod, if these are provided as files, the container application requires the logic to handle on the fly changes of these files.

## ARGOCD Admin Example

As promised, we will now use the created secret automation workflow to fetch the argocd admin secret and hand it off to ESO. ArgoCD stores the secret as an bcrypt hash, so we have to:

1. generate a password
    
2. hash it
    
3. create the ExternalSecret for it.
    

## Create the 1Password Secret

Use 1Password to generate a password and store it in the HomeLab vault.

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F47e666e4-a9b7-4059-a21f-32650b0229ee_564x354.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F47e666e4-a9b7-4059-a21f-32650b0229ee_564x354.png)

After that use install Apache HTTP Server Tools to generate a bcrypt hash:

```
brew install httpd
```

Then generate your hash:

```
htpasswd -nbBC  10 "" "$(op read op://HomeLab/argo-admin/password)" | tr -d ':\n'
```

Here’s what each flag does:

- -n: don’t write to a file, just print
    
- -b: pass password on the command line
    
- -B: use bcrypt
    
- -C 10: cost factor of 10
    
- "": no username, we just want the hash
    
- tr -d ':\n': remove the colon and newline for a clean hash
    

ArgoCD requires a Kubernetes secret called argocd-secret, where the admin password will be stored. By default, ArgoCD creates this secret and adds a couple of necessary values to it. One of them is server.secretkey, which is used for session validation.

If we don’t include this in our external secret, we’ll end up in a weird loop where both ArgoCD and the External Secrets Operator are trying to manage the same secret, constantly overwriting each other.

To avoid that, generate the server.secretkey manually using the following command:

```
openssl rand -hex 32
```

Save both generated values as follows:

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2ed71f53-ead4-4c39-9633-fa82b4fbbd2a_550x432.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2ed71f53-ead4-4c39-9633-fa82b4fbbd2a_550x432.png)

Notice that the name of the password maps to the exact name of the kubernetes secret. Also, make sure the keys contain the exact names as [expected from ArgoCD](https://argo-cd.readthedocs.io/en/latest/operator-manual/argocd-secret-yaml/).

Now we need to create the external secret that ArgoCD can reference for creation and also monitor for changes:

```
apiVersion: external-secrets.io/v1beta1
kind: ExternalSecret
metadata:
  name: argocd-secret
  namespace: argocd
spec:
  secretStoreRef:
    kind: ClusterSecretStore
    name: one-secretstore
  target:
    creationPolicy: Owner
  dataFrom:
  - extract:
      key: argocd-secret
```

With this we have all resources that we need to create our argocd-secret! But this introduces a little problem, especially if we want to setup a new or second environment of the cluster.

## The Chicken-and-Egg Problem

What happens when you bootstrap a brand-new cluster?

We’ve got a secret automation workflow that is created on top of ArgoCD to create the ArgoCD secret, but ArgoCD won’t start without the secret. Classic chicken-and-egg.

One option is to utilize a script that creates and injects the secrets beforehand… but I prefer letting ArgoCD manage it.

My solution is to simply initialize ArgoCD with it’s default values and then override the default values with the our custom values. With this, we can easily manage the whole process through ArgoCD. Check out my [ArgoCD setup post](https://dakaiser.substack.com/p/utilizing-gitops-with-argocd) how to utilize multiple values files to get a better understanding of the idea. But basically what we are doing is this:

1. Deploy ArgoCD initially with this common-values.yaml:
    
    ```
    dex:
      enabled: false
    notifications:
      enabled: false
    configs:
      params:
        server.insecure: true
      secret:
        createSecret: true
    ```
    
2. Install 1Password Connect + ESO
    
3. Override with homelab-values.yaml:
    
    ```
    dex:
      enabled: false
    configs:
      params:
        server.insecure: true
      secret:
        createSecret: false
    ```
    

Don’t worry about the disabled parameters, we’ll cover TLS, dex and notifications in our upcoming posts, but this should work for you out of the box.

And that’s it! ArgoCD is now fully integrated with a secure external secret manager.

Hope you enjoyed reading this as much as I enjoyed writing it. :)