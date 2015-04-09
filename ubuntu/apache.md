# Apache #

### Resources ###
 - https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps



### Setup ###

 - Installing

```bash
sudo apt-get update
sudo apt-get install apache2
```

- Setup Available Virtual Hosts

Edit available sites in /etc/apache2/sites-available

```bash
sudo vi /etc/apache2/sites-available/000-default.conf

```

- Enabling Sites

```bash
sudo a2ensite 000-default.conf
sudo service apache2 reload
```

- Disable Sites
```bash
sudo a2dissite 000-default.conf
sudo service apache2 reload
```
- Enable modules

If you fail to load the rewrite module you will get an error like ".htaccess: Invalid command 'RewriteEngine'...".

```bash
sudo a2enmod rewrite && sudo service apache2 restart
```

### Virtual Host ###

```xml
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin you@company.com
        DocumentRoot /var/app/public
        <Directory /var/app/public>
                DirectoryIndex index.php
                AllowOverride All
                Require all granted
        </Directory>

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>
```
