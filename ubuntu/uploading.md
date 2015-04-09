# Uploading Files #

### Resources ###
 -
 -
 -
 -


### Commands ###

 - Granting Permissions to the user to upload files

```bash
sudo adduser ubuntu www-data
sudo chown root.www-data /var/app
sudo chmod g+ws /var/app
```

- Sublime Text

In the sftp-config.json file

```json
"host": "xxx.xxx.xxx.xx",
"user": "ubuntu",
"ssh_key_file": "~/.ssh/key",
```