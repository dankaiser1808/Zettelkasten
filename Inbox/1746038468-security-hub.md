---
id: 1746038468-security-hub
aliases:
  - Security Hub
tags: []
---

# Security Hub

Main portal to obtain security information about GuardDuty, Inspector, Macie, CloudWatch events, Lambda and other external security tools.

All their finding can be send to security-hub and we can see all security related information in a central dashboard.

Security Hub can scan resources and check for compliances best practices.

With this level of centralization, it makes it easier for us to prioritize findings.

A common use case looks like this:

1. GuardDuty, Inspector, Macie findings send to security-hub
2. security-hub sends notification and event get triggered
3. Event triggers either a lambda, step functions or System Manager

