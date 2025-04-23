---
id: 1745425699-elastic-loadbalancing
aliases:
  - Elastic LoadBalancing
tags: []
---

# Elastic LoadBalancing

Listeners and target groups

Listeners are rules where to route traffic to.
Target groups are EC2 Instances grouped where the traffic should be forwarded to.

A Target Group can have specified:
- EC2 Instances
- IP Address
- Lambda
- Other load balancers
- Health Checks

Cross zone load balancing can be enabled if needed.

Application Load Balancer works on layer 7, HTTP and HTTPS.
Network load balancer operates on layer 4.

For an ALB, rules can be specified based on the HTTP protocol. We can specify rules for header, http methods, paths or ips.


[[OSI Model]]


