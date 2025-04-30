---
id: 1746040342-aws---secretsmanager
aliases:
  - AWS - SecretsManager
tags: []
---

# AWS - SecretsManager

External Store that offers us to store our secrets and credentials in the secrets manager. This makes it easier for our application to access the secrets without hard coding them in our application.

Secrets are encrypted through KMS keys and the secrets are stored as JSON.

We can utilize others services like lambda to rotate our secrets in the manager for more security.


