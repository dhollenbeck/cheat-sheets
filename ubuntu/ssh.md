# SSH #

ssh - Open SSH server

### Resources ###

- https://help.ubuntu.com/lts/serverguide/serverguide.pdf
- man sshd_config

### Commands ###

 - client install

```bash
ubuntu@server:~# sudo apt-get install openssh-client
```

 - server install

```bash
ubuntu@server:~# sudo apt-get install openssh-server
```

- server config

```bash
ubuntu@server:~# sudo vi /etc/ssh/sshd_config
```

- server restart, start, stop

```bash
ubuntu@server:~# sudo service ssh restart
```
