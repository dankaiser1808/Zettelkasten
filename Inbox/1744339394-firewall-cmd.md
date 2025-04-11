---
id: 1744339394-firewall-cmd
aliases:
  - Firewall-cmd
tags: []
---

# Firewall-cmd


Firewalld-cmd is the primary command line tool for firewalld. We can use it to the current status of firewalld, apply new ingress or egress rules of our system.

To add a port permanently, we can run the following command:
```bash
firewall-cmd --permanent --add-port 3100/tcp
```

