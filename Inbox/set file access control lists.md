
SetFacl and GetFacl are linux commands to retrieve and set file acces control list permissions. 
We can use it to grand permissions to specific users, groups and also remove these permissions. 

```bash
sudo setfacl -m u:john:r-- /etc/hostname
```
grants read-only permission to john

[setfacl](https://linux.die.net/man/1/setfacl)