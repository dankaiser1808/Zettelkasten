---
id: 1745948843-aws-organizations
aliases:
  - AWS Organizations
tags: []
---

# AWS Organizations

Organizations potentially have more than one AWS Account. For example, multiple Teams in a company have different AWS Accounts. This adds complexity for the following tasks:

- Billing
- Account Management Overhead
- Difficult in Scaling
- Inconsistent Security Controls
- Limited Resource Sharing

For those reasons, Amazon created AWS Organizations. It simplifies the management of multiple AWS accounts

The organization receives a root account. Under this root account we can build a hierarchy for different sub accounts.

We can apply Service Control Policies which define what is allowed by the sub account and the users inside the account

We can utilize it with SSO for user login.

