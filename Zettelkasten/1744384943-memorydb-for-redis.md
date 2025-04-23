---
id: 1744384943-memorydb-for-redis
aliases:
  - MemoryDB for Redis
tags: []
---

# MemoryDB for Redis

ElastiCache and Redis work as two separate DB instances, where MemoryDB runs as a single server with caching and Redis enabled. This simplifies the overall architecture and lowers costs, since we don't run two separate servers for caching and data storage.

MemoryDB clusters follow the same architecture with a primary and replica nodes as other DB solutions.

The smallest unit in a MemoryDB Cluster is a node, which is represented by a EC2 instance.

A node belongs to a shard and a shard contains one primary and up to 5 optional replica nodes.

We can set parameter groups that are handed over to the nodes, subnet groups and Access Control Lists.

Use Cases:
- Great for web and mobile applications
- Quick access customer data
- Great for online games for sessions history and leaderboards that require massive scale
- Good for highly visited content like media streaming that need low latency and high performance
