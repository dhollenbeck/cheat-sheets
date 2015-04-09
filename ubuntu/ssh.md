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

### Recommends Configuration Changes ###

It is recommend that password authenication is turned off to stop brute force attacks. Of course, this means you will need to setup key based authenication. It also recommended that you disable root login.

Set PasswordAuthentication to 'no'
Set PermitRootLogin to 'no'


### Authenicate via SSH Key Pair Authentication

```bash
ssh -i ~/.ssh/key ubuntu@xxx.xxx.xxx.xxx
```

### Setup SSH Key Pair Authentication ###

Start by generating a key pair with no passphrase on the desktop:

```bash
ssh-keygen
```
Upload the public key (*.pub or *.pem) to the server.  It will be placed in user ubuntu's home director.

```bash
scp ~/.ssh/key.pub ubuntu@xxx.xxx.xxx.xxx:
```

On the server make an .ssh folder.
```bash
mkdir .ssh
```

Add the key.pub in the ssh folder to the .ssh/authorized_keys file.
```bash
cat key.pub >> .ssh/authorized_keys
```

Fix permissions
```bash
chown -R ubuntu:ubuntu .ssh
chmod 700 .ssh
chmod 600 .ssh/authorized_keys
```

### Trouble-shooting ###

- monitor ssh server log file during connection problems

```bash
tail -f /var/log/auth.log
```

On the client use the -v option when connecting.
