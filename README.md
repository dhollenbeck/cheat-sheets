cheat-sheets
============

Web development cheat-sheets.


## Mac Lion Setup

All repos are stored in the user home folder ('/Users/dan/repos').  

Setup the apache2 vhosts file /etc/apache2/extra/http-vhosts.conf
,,,
<Directory "/Users/dan/repos/">
  Options +Indexes
  Allow From All
  AllowOverride All
</Directory>

<VirtualHost *:80>
    ServerAdmin wemaster@example.com
    DocumentRoot "/Users/dan/repos/txn/app/public/"
    ServerName txn.dev
    ServerAlias www.txn.dev
</VirtualHost>
,,,

You will also need to edit the hosts file pointing the development domain (txn.dev) to 127.0.0.1.  The hosts file is located /private/etc/hosts.

You can map the Home and End keys to mimic windows: 
https://gist.github.com/1730936
http://mwholt.blogspot.nl/2012/09/fix-home-and-end-keys-on-mac-os-x.html


## Ubuntu Setup ##

http://joshrendek.com/2013/01/securing-ubuntu/
http://news.ycombinator.com/item?id=5087183
