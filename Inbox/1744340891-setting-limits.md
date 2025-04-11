---
id: 1744340891-setting-limits
aliases:
  - Setting Limits
tags: []
---

# Setting Limits

We can set user or group limits by navigating into /etc/security and edit the limit.conf file. In here, we can add rules as follows:

<domain> <type> <item> <value>

With this, we could use the nproc item to limit a users maximum running processes which is widely used to prevent fork bombs.

[[fork bombs]]
