---
id: 1745879238-aws-datasync
aliases:
  - AWS DataSync
tags: []
---

# AWS DataSync

AWS DataSync is a data transfer service that we can use to synchronize our on-premise storage data to AWS cloud. It does that by using DataSync agents that utilize TLS to send the data to DataSync Discovery. We can then use this data and store it in a variety of AWS storage services. Supported are:

- Amazon EFS file system
- Amazon S3 Bucket
- Amazon FSx
- ...

We can also use syncs between multiple AWS regions instead just on-premise to cloud or between cloud providers.

The actual sync process is defined as a task which can be scheduled for a specif time.

