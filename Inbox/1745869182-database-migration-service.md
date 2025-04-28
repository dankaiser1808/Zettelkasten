---
id: 1745869182-database-migration-service
aliases:
  - Database Migration Service
tags: []
---

# Database Migration Service

This service specializes on moving databases from on-premise infrastructure to the AWS cloud. It provides us with minimal downtime, zero dataloss, data synchronization in a reliable and fast way. It basically works as the equivalent to the Application Migration Service just for databases. For example, it can migrate the SQL database schema to Amazon RDS.

The first important component of this service is the DMS Fleet Advisor.
It acts as an collector that is installed on the database server and gathers information about the server to obtain a better understanding of the environment the database is running at. 

The second helpful tool it provides us, is the DMS Schema Conversion Tool, which makes it possible to move from one database engine to another and map the database schema how it is needed for the new database system.

Next, we have the Replication Instance, which is responsible to replicate the on-premise data and save it to the AWS cloud database instance. It does that by accessing an endpoint of the on-premise database.

Based on that, the next component is the replication task. It focuses on defining the Source (on-premise database endpoint) and the target endpoint. We can additionally define a migration type. This type ensures how the task will be performed:
1. Full Load (copy all data from source to target during downtime period)
2. Full Load + CDC (Copy source to target and track changes during migration period and applies these changes after migration is done.)
3. CDC Only (the actual copy process will be executed from another tool but CDC will track changes during migration process and applies them afterwards.)

