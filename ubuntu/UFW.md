# Ubuntu Setup #

http://joshrendek.com/2013/01/securing-ubuntu/
http://news.ycombinator.com/item?id=5087183

## UFW ##

Use ufw to manage the firewall iptables.

### Resources ###
 - # man ufw
 - http://www.youtube.com/watch?v=PEa1xopeufQ  (skip to 33 min)
 - https://wiki.ubuntu.com/UncomplicatedFirewall
 - http://ubuntuforums.org/showthread.php?t=823741


### Commands ###

 - show firewall status with each rule numbered

```bash
#sudo ufw status numbered
```

 - set default policy,
```bash
	#sudo ufw default deny
```

 - enable or disable firewall,
```bash
	#sudo ufw enable
	#sudo ufw disable
```

 - deleting rules
```bash
	#sudo ufw delete xx (where xx = rule number)
```

 - insert rule to allow|deny port,
```bash
	#ufw allow 80
```

 - insert rule to allow everything from ip address,
```bash
	#ufw allow from 97.79.131.82
```

 - insert rule to allow port from ip address,
```bash
	#ufw allow from 97.79.131.82 to any port 22
	#ufw allow from 97.79.131.82 to any port 3306
```

 - insert rule to allow a specific interface traffice from a specific port to port 80
```bash
	#sudo ufw allow in on eth0 from 192.168.1.0/24 to any port 80
```
### Example ###

Internal LAMP server:

```bash
sudo ufw status
	To                         Action      From
	--                         ------      ----
	80                         ALLOW       Anywhere
	443                        ALLOW       Anywhere
	3306                       ALLOW       192.168.1.0/24
	22                         ALLOW       192.168.1.0/24
```
