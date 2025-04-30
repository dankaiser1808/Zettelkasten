---
id: 1746040560-aws---nacl-and-secgroups
aliases:
  - AWS - NACL and SecGroups
tags: []
---

# AWS - NACL and SecGroups

NACL act as firewall and includes rules for inbound and outbound traffic. The NACL can therefore specify which traffic leaves and enters a subnet.

Security Groups on the other hand operate on the instance level and define inbound and outbound rules.

NACL are stateless and require both inbound and outbound specified for an request for example. Security Groups are stateful, which means we can define an inbound rule for example HTTP and the response will automatically be associated to the inbound traffic and therefore allowed.

Security groups can only specify allowing rules, since they do not allow any traffic by default. NACL on the other hand can define allow and deny rules.


