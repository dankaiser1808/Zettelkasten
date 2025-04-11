---
id: 1744326057-systemd-targets
aliases:
  - Systemd Targets
tags: []
---

# Systemd Targets

Systemd based operating systems do not use this classical approach. In systemd, runlevels are replaced by targets which define the level that we want to set temporarily or by default for system boot.

|Traditional Runlevel|systemd Target|
|---|---|
|0|`poweroff.target`|
|1|`rescue.target`|
|2, 3, 4|`multi-user.target`|
|5|`graphical.target`|
|6|`reboot.target`|

This command enables the GUI so the system boots into the graphical mode.
```bash
sudo systemctl set-default graphical.target
```
