---
id: 1745880754-aws-snow-family
aliases:
  - AWS Snow Family
tags: []
---

# AWS Snow Family

Is a family of physical storage devices to physically bring data to an AWS data center or retrieve it from there.

It is often used where quick transfer is really important or the amount of data is so extensively large that sending the data over the network would be to slow or to cost intense.

The physical devices are very durable and portable providing high security for the storage units.

The physical devices provide NFS endpoints to integrate with NFS.

We can also install EC2 instances on those devices to run data processing data processing tasks (On board computing)

All data that is stored on the snow family devices is encrypted with a 256 bytes KMS encryption key.

The main attraction of this product is offline data migration.

Every device is tamper proof and can be tracked and therefore easily located.

AWS will also wipe the device completely so that the customers data can not be obtained after transfer is over.

Products and Use Cases:
- AWS SnowBall Edge
- SnowCone

Good to store data and work in extreme environments like ships, military station or airplanes. 

- AWS SnowBall
Suitecase sized with compute or storage optimized hardware when computing or storage use cases are needed.

AWS Snowmobile:
is a large truck that is used to move hundreds of petabytes of data from a company to the AWS data centers.

