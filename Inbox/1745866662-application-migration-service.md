---
id: 1745866662-application-migration-service
aliases:
  - Application Migration Service
tags: []
---

# Application Migration Service

This services performs the heavy lifting of creating the AWS infrastructure based on the discovery service.

It comes with integrated applications to migrate that normally need a lot of manual steps and are heavily error prone, for example SAP, ORACLE or SQL Server.

It comes with the Following features to ensure a structured and planned migration process:

- Assess on-premise environment
  - Analyze dependencies
  - Create Migration plans
- Replication and Data Sync
  - Syncs the Data from the on-premise services to the AWS cloud to keep it up to date.
- Automated Cutover and Testing
  - Handles the actual move from on-premise to cloud minimizing downtime during the migration
  - Comes with build in testing features to ensure reliability and functionality of the migrated application.


The automated testing workflow is as follows:
1. Installed discovery agents register to MGN through the API
2. Creates EBS volumes based on on-premise server disks (Staging Area)
3. Migrates Resources (Creates EC2 instances using the EBS volumes.)

Good to mention is also that this service can help between migration of AWS regions of AWS services instead of on-premise infrastructure migration.
