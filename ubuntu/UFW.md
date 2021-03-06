# UFW #

 ufw - program for managing a netfilter firewall and aims to provide an easy to use interface for the user.

### Resources ###
 - # man ufw
 - http://www.youtube.com/watch?v=PEa1xopeufQ  (skip to 33 min)
 - https://wiki.ubuntu.com/UncomplicatedFirewall
 - http://ubuntuforums.org/showthread.php?t=823741


### Commands ###

 - show firewall status with each rule numbered

```bash
sudo ufw status numbered
```

 - show firewall status verbose

```bash
sudo ufw status verbose
```

 - set default policy,
```bash
sudo ufw default deny
```

 - enable or disable firewall,
```bash
sudo ufw enable
sudo ufw disable
```

 - deleting rules
```bash
sudo ufw delete xx (where xx = rule number)
```

 - insert rule to allow|deny port,
```bash
ufw allow 80
```

 - insert rule to allow everything from ip address,
```bash
ufw allow from xxx.xxx.xxx.xxx
```

 - insert rule to allow port from ip address,
```bash
ufw allow from xxx.xxx.xxx.xxx to any port 22
ufw allow from xxx.xxx.xxx.xxx to any port 3306
```

 - insert rule to allow a specific interface traffice from a specific port to port 80
```bash
sudo ufw allow in on eth0 from 192.168.1.0/24 to any port 80
```
### Example ###

Internal LAMP server:

```bash
sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22 on eth0                 ALLOW IN    192.168.1.0/24
3306 on eth0               ALLOW IN    192.168.1.0/24
80 on eth0                 ALLOW IN    Anywhere
80 on eth0                 ALLOW IN    Anywhere (v6)
```
