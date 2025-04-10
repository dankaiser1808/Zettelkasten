
in between RDS and Compute Instances to limit open connections to the DB. Proxy handles and throttles connections to keep DB save, and proxy reuses open connections. 
Less connections means improved performance for DB compute resources, proxy is fully managed and can shift to another DB instance when failover occures.

## AWS Redshift

AWS Data Warehouse solution

- Fully managed petabyte-scale Data Warehouse Cloud Service
- Enterprise Class DB Query and management system
- Supports Client Connection with BI, Reporting, Data and Analytic Tools
- Efficient Storage and Optimum Query performance

## AWS Redshift Serverless

- more dynamic for the costs since Redshift full capacity for RedShift main will be always charged. (CostSaving)
- Optimal Cluster Usage of resouirces
- On demand Data Warehouse Service

## DynamoDB 
- Managed Service
- NoSQL Database

DynamoDB Streams:
- Optional for DynamoDB 
- We can create Stream Records that will capture any event on our DynamoDB like delete, create update and these will be stored as a Stream Record with a timestamp and a DB reference.
- Stream Records lifetime of 24h
- Can be combined with lambda 

Let's say every new user should get a welcome message after registration. We can add this event as a stream record, connect this type of event as a trigger for lambda and send a welcome message through lambda to the new user.


### Dynamo DB Table Classes

We have a Standard Table Class and the Standard Infrequent Access Table Class. The second one is optimized for costs handling infrequently accessed data, like logs, order history or other old data.

Each table offers different pricing for storage and IOPS.


DynamoDB Feature Overview:
- Can store Key value pairs or Document based Data Models
- Serverless
- Read and Write from global regions.
- On Demand BackUp and Restore
- Read Write Capacity Modes

DynamoDB Accelerator (DAX)
- Fully managed Caching Services
- Can run in a DAX Cluster with Cache Nodes (Leader, Follower replicas)
-  Performance boost
- Highly Scalable Caching Solution
- Fully Managed
- Ease to Use
- Flexible, we can decide how many cluster for which and how many tables we want to use

OpenSearch
- Build on top of ElasticSearch for structured logging and log aggregation
- can be serverless
- OpenSearch Ingestion
	- Provides some kind of collector  like OTEL or FluentBit
	- Those collected data will be injected in a OpenSearch Ingestion Pipeline and stored in Amazon OpenSearch Service Domains

AWS OpenSearch Features
- Application Analytics
- Anomaly Detection
- Cross-Cluster Replication
- 3 PB storage
- SQL Query syntax
- Trace Analytics
- Sends data to Cloudwatch
- AWS CLoudTrail
- Amazon Kinesis
- S3
- IAM
- Lambda DynamoDB
- Amazon Quicksight (Data visualization of OpenSearch Data)


OpenSearch Use Cases:
- Monitor and Debug Data
- Personalized Search
- Security Information and Event Management