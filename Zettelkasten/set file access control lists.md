---
id: set file access control lists
aliases: []
tags: []
---


setfacl and getfacl are Linux commands to retrieve and set file access control list permissions.
We can use access control lists to grand permissions to specific users, groups and also remove these permissions.

```bash
sudo setfacl -m u:john:r-- /etc/hostname
```

grants read-only permission to john

[setfacl](https://linux.die.net/man/1/setfacl)
