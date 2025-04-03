#consume

## Eso integration argocd

- Let’s make our lab a little bit more secure. Today, I’m going to share with how to use the external secrets operator to dynamically create and update your secrets which are stored in an external vault. For the third party vault, I use OnePassword. Before we can jump into how everything works together, I’ll would like to briefly introduce each technology we are going to utilize and then bring them together. We will use the argocd secret as our example and I’ll show you how to deal with the chicken and egg problem it introduces.

### One Password Connect 

Let’s start with OnePassword and setup our vault where we will store our secrets.

  

First, we will install the OnePassword cli tool and create the vault that we will use to store our passwords. 

  

  

Next, we need to use bcrypt to encrypt our argocd admin password since the argocd requires a hashed value for it. We can now save the secrets inside our vault. 

  

The next step contains the accessibility of our vault. We need to generate the needed secrets and enable access to the vault through the OnePassword api. 

  

  

After everything is set up, we can install the OnePassword Connect server that will handle the communication between the OnePasswords API and our Cluster. The connect server acts as a proxy which has the ability to cache the secrets it retrieves from the api. This gives us two main benefits:

1. Less api calls 
2. If OnePassword faces downtime we can still use the secrets from the onepw connect server. 

The OnePassword connect server needs the generated secure json file that we created to establish a save connection. We will create a kubernetes secret inside the OnePassword namespace.

We this, our connect server is ready to go.

  

1. External Secrets Operator:

  

The next in line is our external secrets operator. After deploying the helm chart we have to decide what type of SecretStore we would like to use. ESO gives us two options:

1. ClusterSecretStore
2. SecretStore

  

The name is already telling us the main difference of those two components, one is cluster, the other namespace scoped.

  

For simplicity we will use the cluster store, but we’ll add the  SecretStore in the future as a security improvement. Nevertheless, I will cover how to use the SecretStore in the future.

  

Our Cluster SecretStore needs an api token to be able to communicate with our connect server. Let’s create the secret for it:

—> 

  

So far so good. 

Know we need to create the actual external secrets we want to retrieve from our vault. For this, let’s create the external secrets manifest:


  

Be aware of the mapping of those values.

Here’s a comparison from onepasswords desktop tool and the external secret. Make sure to name the keys properly. 

  

Witz this we should be able to retrieve our external secret. Make sure to deploy those manifests in your cluster and you’re all set! 

  

Some might have already figured that we have a typical chicken and egg problem for this particular example. The argocd-server password is needed for the argocd-server to start. If the secret is not created, the server will fail to start.  If you followed my last posts about my argocd setup, you will remember that we use multiple values files for our helm chart deployments. Here’s a short reminder:

Example 

  

Inside the common values we specify that argocd should create the secret itself. We deploy this, and create all the needed dependencies for the eso and op connect manifests. After that, we’ll deploy another argocd version, where we specify the actual values we want to have. See that we disable argocd secrets creation, since we don’t want argocd to override our secrets (just in case). 

  

Now we should be able to retrieve all kinds of secrets from our vault! 

  

Next, I’ll cover how to use