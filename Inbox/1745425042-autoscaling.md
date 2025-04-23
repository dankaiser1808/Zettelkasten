---
id: 1745425042-autoscaling
aliases:
  - Autoscaling
tags: []
---

# Autoscaling

Autoscaling defines the automation of creating and destroying instances based on certain criteria.
It contains policies that define the minimum, desired and maximum Instances that should be running.
We can either set manual policies or dynamic policies. Dynamic Policies can be split into three types:

- target tracking: Scaling based on certain system metrics
- Step Scaling: Set Cloudwatch alarm --> customize ramps based on specific metric > 60% and < 70% ... 
- Simple Scaling: Only fixed value without any complex rules. > 50% 5 fix Instances +

Another way to handle autosclaing is the usage of scheduled scaling, which will scale the instances in a certain time frame. This comes in handy for predictable workloads.

Autoscaling integrates with LoadBalancers, Cloudwatch for alarms and metrics, SNS for event messages and EC2 instances scaling.
