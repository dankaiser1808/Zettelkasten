#aws #consume 

Caching solution minimize response times, reduce the amount of queries towards the database, less operations for the database. 


Cache stores the db data in memory for fast access and response instead of the db. Sits between db and server. 

Good for data that does not change too frequently.


ElastiCache is Amazon fully managed cache solution.
We don't have to worry about the infrastructure.


Two different caching engines:
- Redis
- MemCacheD

Can run as a Cache Cluster running multiple nodes. Each node can have a type with different resources for the node. On top of that, we define Cluster Parameter Groups which define the overall configuration for our cache cluster. The next layer is the cache security group where we can define inbound and outbound rules who can access the cache.

We can also define a subnet group where the clusters should be placed in.

Redis provides us with the following benefits:
- Read Replicas 
- Data Persistency
- Encryption at Rest
- Redis provides Pub/Sub messaging system (look more into that)

MemCacheD: 
- Multi AZ Deployment
- Auto Discovery can automatically add and remove nodes
- Data distribution and sharding between multiple nodes

We can use it as a cache or ephemeral data storage.

Use Cases:
- To reduce database related burden like caching, reduct I/O 
- Real-Time Application Data Caching
- Storing sessions
- Real-Time Leaderboards 

Basically minize the amount of db accesses for data that doesn't change too often.
Minimize latency and response times.

## Memory DB for Redis

