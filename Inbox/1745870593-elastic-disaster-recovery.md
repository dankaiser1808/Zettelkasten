---
id: 1745870593-elastic-disaster-recovery
aliases:
  - Elastic Disaster Recovery
tags: []
---

# Elastic Disaster Recovery

The elastic Disaster Recovery service provides us with the ability to use the AWS cloud for our services in case of a disaster where a failover is needed. Having two infrastructure setups running at the same time is very cost intensive and not practicle.

DRS uses the following components:

1. Replication Agent
This agent is installed on the on-premise instances and monitors the disk of the instance. It communicates with the DRS service to register the on-premise servers that should be replicated. It sends the data of the disks to the next component, the replication server.

2. Replication Server
The Replication Server is a EC2 instance that receives the replication agents data and stores it in different EBS volumes. For each disk it will created a dedicated EBS Volume. This process happens in the so called staging area and those resulting volumes will be used by the upcoming component.

3. Recovery Instance
Like mentioned, this instance represents the on-premise instance in the cloud in case of an failover. It mounts the EBS volumes that represent the state of the on-premise instances.

This setup gives us the possibility to run in the cloud and also move back to the on-premise instance and replicate the cloud data back to the on-premise instances.

Worth mentioning is that the sync runs in real-time. 

DR Use Cases are mostly those major three:
- On-premise to cloud
- Other Cloud to AWS
- AWS Region to Region
