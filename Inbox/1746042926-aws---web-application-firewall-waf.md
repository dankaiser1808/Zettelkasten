---
id: 1746042926-aws---web-application-firewall-waf
aliases:
  - AWS - Web Application Firewall (WAF)
tags:
  - aws
  - consume
---

# AWS - Web Application Firewall (WAF)

WAF is a firewall that is placed in front of the web application to protect our app from various threats like cross site scripting or SQL injection attacks.

It inspects the packages send over HTTP and ensures that these are save, operating on layer 7 of the OSI model.

We have to define rules, so called WEBACL. Those rules are going to be applied on web requests and determine which are allowed and which not.

It is positioned in front of the actual api gateway or even load balancer.


