---
id: 1746031314-directory-service
aliases:
  - Directory Service
tags: []
---

# Directory Service

Active Directory is created by Microsoft to manage all users and their permissions to applications, services, networks and many more.

Directory Service is Amazons managed Active Directory service. It can be operated in the following modes:

Simple AD Mode:
Lightweight variant of Active Directory, does not come with all MS AD features. It is designed to run in isolation, so it does not work with another AD simultaneously 


Managed Microsoft AD
Actual implementation of MS AD. Integration to create a so called trust relationship between an cloud and on-premise AD instance.

AD Connector
If we already have a AD running ourselves and we don't want to deploy one in the cloud, we can use the AD Connector mode to proxy the traffic to the on-premise instance from the cloud Directory Service. This is quiet useful if we want to easily connect AWS services to the AD without running one in the cloud.

