# Optional Apache Configurations

This is an ever-growing list of optional configurations for Apache. 

If you have a setup to add to this list, please, be my guest!

### Additional Configuration Procedures
- [Virtual Hosts](./mods/vhost.md)
- [MOD Rewrite](./mods/mod.rewrite.md)
- [SSL](./mods/ssl.md)
- Userdir - <i>planned</i>

### Verify Installation
  - Open Command Window

#### Test Apache VHOST and CONF Files
  - Enter: `httpd -t`
  - It should respond with:
```shell
Syntax OK
```

#### Show Parsed Vhost Settings 
  - Enter: `httpd -S`
  - It should respond with:
```shell
VirtualHost configuration:
[::1]:80               localhost (L:/etc/Apache2.4/conf/conf.vh/httpd-vhosts.conf:30)
127.0.0.1:80           is a NameVirtualHost
         default server localhost (L:/etc/Apache2.4/conf/conf.vh/httpd-vhosts.conf:30)
[list of vhost servers]
ServerRoot: "L:/etc/Apache2.4"
Main DocumentRoot: "L:/etc/Apache2.4/htdocs"
Main ErrorLog: "L:/etc/Apache2.4/logs/ssl_engine.log"
Mutex ssl-cache: using_defaults
Mutex default: dir="L:/etc/Apache2.4/logs/" mechanism=default
Mutex ssl-stapling-refresh: using_defaults
Mutex rewrite-map: using_defaults
Mutex ssl-stapling: using_defaults
PidFile: "L:/etc/Apache2.4/logs/httpd.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
Define: SRVROOT=L:/etc/Apache2.4
Define: ERRLOGDIR=L:/etc/Apache2.4/logs
Define: DEFAULTDOCROOT=L:/etc/Apache2.4/htdocs
Define: VHROOT=/var/www
Define: CGIDIR=L:/etc/Apache2.4/cgi-bin
Define: MODDIR=L:/etc/Apache2.4/modules
Define: CONFROOT=L:/etc/Apache2.4/conf
Define: SHARERUNDIR=L:/etc/Apache2.4
Define: PRVRUNDIR=L:/etc/Apache2.4/logs
```

#### Test Apache loaded MOD Files
  - Enter: `httpd -M`
  - It should respond with:
```shell
[list of MODs]
```

## My Pipe Dream

I would like to document each and every MOD that Apache has, its configuration and how it works.

If you've made a particular MOD run, and it's not here, please make a branch (name it the MOD your adding) and submit your addition.

### Apache MODs

- Userdir - <i>planned</i>
- Proxy - <i>planned</i>
- DAV - <i>planned</i>
