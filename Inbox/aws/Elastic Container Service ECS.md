---
id: Elastic Container Service ECS
aliases: []
tags: []
---

#consume #split

Amazon provides their own container orchestration solution to dynamically run containers on multiple hosts. A container orchestration tool is the environment that manages all your containers. Part of it's responsobilities are deploymrent, load-balancing, container communication, restarts and reschedule on host failure. Containers are independent isolated units where we can run our applications. They are based on linux cgroups and namespaces.

ECS is Amazon fully managed container orchestration service that manages, scales containerized applications.

Can run on Fargate or EC2 Instances.

migrating from ECS to other cloud providers can be more difficult since ECS is not an open source service, it's a, amazon only.


ECS is good if we need a quick and easy alternative to run our applications, instead of utilizing high complex tools like Kubernetes.

ECS has two launch types, EC2 and Fargate. These just specify the compute resources, where our containers will be placed.

ECS does NOT run containers itself, it just acts as a control plane where to run them.

If we use EC2 as our target, we have to take care of installing the needed software on the EC2 instances by ourselves. This means installing docker and the ECS agent, configure firewalls and patch the instances when needed.

This provides us with full control over the infrastructure.


With Fargate, AWS is taking care of the underlying infrastructure. 
Fargate follows a serverless architecture and will actually create the needed servers where we run our containers.

You only pay for what you use.

EC2:

- provides more flexibility and control
- Servers are always running 
- manage all resources by yourself

Fargate:
- Don't have to manage resource
- pay for what you use
- more convenient, less control


ECS TASK is the smallest running unit in ECS, similar to an Kubernetes pod, that runs a container.

ECS TASKS Definition

Tasks are the actual configurations that ECS uses to run a container. It contains information about where to find the container, how much resources to use and so on. 

It is basically a blueprint for the container we want to run.


ECS Service ensure that a certain amount of tasks runs at all times, similar to a ReplicationSet deployment in Kubernetes. It also monitors the state of the running tasks and ensures rescheduling it onto different hosts on the event of failures.

A LoadBalancer Instance will forward the requests to the containers. We need to create this one ourselves.




