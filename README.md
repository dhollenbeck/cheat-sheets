cheat-sheets
============

Web development cheat-sheets.


## Mac Lion Setup

Install iTerm by downloading it from [http://www.iterm2.com/](http://www.iterm2.com/)

Install .bash_profile and .gitconfig from your personal dotfile repos. Copy these files into your home dir.

Install mac github client. Setup app references including installing command line tools.

Create dir to store your repos ('~/repos').

Install Sublime Text.
Setup command line launcher [https://gist.github.com/olivierlacan/1195304](https://gist.github.com/olivierlacan/1195304).

Install Node.js by downloading it from [http://www.node.js/download/](http://www.node.js/download/)
Node will be installed into /usr/loca/bin/node. NPM will be installed into /usr/local/bin/npm. Make /usr/local/bin is in your $PATH.

Install MAMP from [http:/www.mamp.info](http:/www.mamp.info)

Map the Home and End keys to mimic something useful:
https://gist.github.com/1730936
http://mwholt.blogspot.nl/2012/09/fix-home-and-end-keys-on-mac-os-x.html

# MYSQL

```sql
SHOW GLOBAL VARIABLES LIKE 'max_connections';
SHOW GLOBAL STATUS LIKE 'max_used_connections';
```
