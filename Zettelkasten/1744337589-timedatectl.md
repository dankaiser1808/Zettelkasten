---
id: 1744337589-ubuntu-adjust-timezones
aliases:
  - Timedatectl
tags:
  - #linux
---

# Timedatectl

To adjust the timezone of the current system, we can utilize the *timedatectl* command.

```bash
timedatectl set-timezone <NAME OF TIMEZONE>
```

- status: gives us the current information of the systems timezone configuration
- list-timezones: gives us a list of available timezones

For more detailed options we can use --help to get a list of flags we can use.

