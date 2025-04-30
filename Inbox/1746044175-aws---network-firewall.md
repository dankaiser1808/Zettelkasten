---
id: 1746044175-aws---network-firewall
aliases:
  - AWS - Network Firewall
tags: []
---

# AWS - Network Firewall

Is a firewall that protects against traffic entering and leaving a VPC.
We have to define it ourselves by creating firewall endpoint that is created in its own subnet.

It can only protect services that are deployed outside of its own subnet. The other subnets will send the data to the network firewall endpoint. Based on self defined rules, the requests will be blocked. We also have to define the route tables ourselves to make this setup work.

For incoming traffic, the gateway has to forward to the firewall subnet, which inspects the package and then redirects to the private subnet of the EC2 instance.

For outgoing traffic, the private subnet would route to the firewall subnet, which inspects the data and then blocks it or forwards it to the Gateway.

We can use it with a transit gateway which connects multiple VPC and on premise networks together.

