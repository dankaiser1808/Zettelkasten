---
id: 1745951920-systems-manager
aliases:
  - Systems Manager
tags: []
---

# Systems Manager

Helps us to create a systems inventory for all of our servers either in AWS, other cloud providers, on-premise data centerns and IOT Fleets.

The systems-manager provides us with a centralized control unit that can group the servers/resources and automates tasks for those servers. It manages system updates and gives us operational insights of the systems. Additionally, we can manage the configurations of the servers, the secrets and use remote access through a browser or cli.

Systems manager has a lot of different features, we can group them in the following categories:

### Application Management

- Application Manager:
  helps us to group our servers into an application.
  One application might have a three tier architecture and is defined by three servers.
  The Application Manager groups those servers together and helps us troubleshoot
  issues.
- Parameter Store:
  External Secret Store

### Change Management

- Change Manager:
  Ensures a streamlined process of changes applied to resources and infrastructure
  components.

- Automation:
  Can help us to automate certain tasks like attaching IAM roles to EC2 instances.

- Change Calendar:
  Lock or enable changes in specific time windows.

- Maintenance Windows:
  Define winddows where updates should be applied to minimize user effected during the maintenance window.

### Node Management

- Compliance:
  Scans our servers for patch compliance and configuration inconsistencies

- Inventory:
  Creates a report of all of our servers managed by Systems Manager

- Session Manager:
  Securely connect to the servers

- Run Command:
  Apply commands and configurations on different servers without manually login
  through ssh.

- State Manager:
  Ensure that the server are on the specified configuration as specified

- Patch Manager:
  Automates the process of patching managed instances

- Distributor:
  Distributes software packages to the instances

### Operation Management

- Incident Manager:
  When an alarm occurs, we can create a SNS and trigger the Incident Manager which
  takes care of alarming certain people or initiate a predefined response plan that
  define more detailed what to do during an incident.

- OpsCenter:
  Provides a centralized dashboards where we can see pending operational tasks like which services need a patch. It alerts us about those instances.




