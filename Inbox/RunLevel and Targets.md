traditional and older linux systems define runlevels which are used to initialize multiple services for each level.

0 -> shuts down the system
1 -> single user mode (used for maintenance)
2 -> Multi user mode (no networking, but depends on distro)
3 -> Multi user mode (with networking)
4 -> Undefined (custom usage)
5 -> Multi-User with GUI
6 -> Reboot

SystemD based operating systems do not use this classical approach. In systemd, runlevels are replaced by targets which define the level that we want to set temporarily or by default for system boot.

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
