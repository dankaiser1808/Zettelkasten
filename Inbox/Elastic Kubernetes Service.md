Amazon gives us the option to run a Kubernetes cluster using EKS. EKS will manage and create and configure the master nodes, also known as control plane nodes. We don't have to take care of managing all Kubernetes controllers, api servers, proxies and scheduler and so on.

EKS will take care of managing all of those resources and follows best practices and takes over takes like creating backups of etcd.

We still need to manage our own Worker Nodes.

With EKS, we need to specify where the worker nodes should be created. 
We can use one of the following three options:

- Self-managed nodes
	- Users provide EC2 instances for the nodes
	- worker node components have to be installed ourselves
		- Kubelet
		- Kube-Proxy
		- container-runtime
	- Updates and Security patches
- Managed node group
	- We still need to manage EC2 instances but in an easier way
	- Special EKS optimized AMI's from Amazon
	- Streamlined process throughs EKS API for simpler lifecycle management of the nodes.
	- Every node is part of an Autoscaling group provided by EKS, so we don't have to worry about scaling.
- Fargate
	- creates worker nodes dynamically following a serverless architecture
	- we don't manage instances ourselves
	- Fargate will ensure optimal EC2 size based on container specs



To create an EKS cluster we have to provide the following information:
- Clustername and K8s version
- IAM role for cluster (since it integrates with various services inside AWS)
	- provisioning nodes
	- secrets
	- storage
- VPC and subnet
- security group rules for the cluster

Creating Worker nodes depend what we decide to use. For a node group for example:
-  Create a nodegroup
- Select EC2 instance type
- Define min/max number of nodes
- Specify EKS cluster we want to connect the nodes to.


We can create a EKS cluster either with:
- AWS CLI
- Eksctl
- IaC like Terraform




