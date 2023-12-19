

# Apache MOD - Configuring Virtual Hosts

- [Utilizing a Directory Structure for Virtual Hosts](#utilizing-a-directory-structure-for-virtual-hosts)
- [Managing Configuration Files](#managing-configuration-files)
- [Configuration Construction](#configuration-construction)
- [Configuration Shortcut File](#configuration-shortcut-file)
- [The HOSTS File](#the-hosts-file)
- [Verification and Testing](#verification-and-testing)
- [Testing the Web Server](#testing-the-web-server)
- [Additional Virtual Hosts](#rinse-and-repeat)


## Utilizing a Directory Structure for Virtual Hosts:

By establishing a clear structure to manage Virtual Hosts, their management is cleaner and more reliable. Within the directory `L:/var/www`, there exists directory named `_template`. This directory serves as a model for creating new virtual hosts.

When creating new Virtual Hosts, I find naming them as closely to the domain name really helps when I have dozens to work with. If the domain is a bit long, I just use a shorted version and reference that short name throughout the configuration definition. Since this is our first Virtual Host, we'll call it `mine` and create a directory labeled `mine`.

Copy **_template** and rename the copy `mine`.

This contains a directory with `htdocs`, which is the root directory of the new domain you're about to create and a "shortcut" file to the config file we will be creating.

There is a windows shortcut file in that directory as well. Rename it from `vh._template.conf` to `vh.mine.conf`. We'll come back to this shortcut file a bit later.



## Managing Configuration Files

In Windows Explorer, open `L:/etc/Apache24/conf`.
In there you'll see a `conf.vh` directory. This is where the configuration files will reside for each of the virtual hosts you define.

Open it.

There is a `disabled` directory, it contains a single file: `httpd-vhosts.conf`. This is the basic configuration to allow your Apache server to operate virtual hosts.

- Move this file into the `conf.vh` directory.

- While you're in `L:/etc/Apache24/conf/conf.vh`, right-click in the white space of Windows Explorer, and select `Open In Terminal`.

- Within the terminal window run this command:<br>
`L:\> httpd -t`<br>
This should return... <br>
`Syntax OK`

- At the command line type:<br>
`L:\> touch vh.mine.conf`<br>
  This will create an empty file.editor.
> I use the "vh." prefix to designate all my virtual host configuration files.

- Open the newly created `vh.mine.conf` file using a text editor. Here, construct the virtual host configuration by defining specific host details within the "VirtualHost" block.

```apacheconf
### xxx.local

<VirtualHost xxx.local:80>
   define VHNAME xxx
   
   ServerName    ${VHNAME}.local:80
   ServerAdmin   walter@${VHNAME}
   ServerAlias   *.${VHNAME}
   
   DocumentRoot  ${VHROOT}/${VHNAME}/htdocs/
#   ScriptAlias   ${VHROOT}/${VHNAME} ${VHROOT}/${VHNAME}/cgi-bin
   
   ErrorLog      ${ERRLOGDIR}/${VHNAME}.error.log
   TransferLog   ${ERRLOGDIR}/${VHNAME}.access.log
#   ScriptLog     ${ERRLOGDIR}/${VHNAME}.cgi_error.log

   # Additional configurations go here
   	<Directory />
	    Options Indexes FollowSymLinks IncludesNoExec
	    AllowOverride all
	    Require all granted
	</Directory>
</VirtualHost>
```

### Configuration Construction
This is a simple virtual host configuration template. It will serve as a basis for all our future work.

- Replace the `xxx` with `mine` at line 1, 3 and 4.

- The top line is simple the domain I'm working with. In this case it will be <br>
```apacheconf
### mine.local
```

- Line 3 Begins by enclosing the configuration within the "VirtualHost" tags and specifying the domain and port to listen on. This name should be the same as the directory you created for this vhost. In our case, `mine`.<br>
```apacheconf
<VirtualHost mine.local:80>
```
Here, `mine.local` is the domain name, and :80 denotes the port number (typically port 80 for HTTP).

- Define variables within the configuration to simplify settings and make modifications easier:

This makes life SO MUCH easier when we define additional Virtual Hosts on our machine.
```apacheconf
   define VHNAME mine
```
- Set essential details for the virtual host:
```apacheconf
   ServerName    ${VHNAME}.local:80
   ServerAdmin   walter@${VHNAME}
   ServerAlias   *.${VHNAME}

   DocumentRoot  ${VHROOT}/${VHNAME}/htdocs/
#   ScriptAlias   ${VHROOT}/${VHNAME} ${VHROOT}/${VHNAME}/cgi-bin
   
   ErrorLog      ${ERRLOGDIR}/${VHNAME}.error.log
   TransferLog   ${ERRLOGDIR}/${VHNAME}.access.log
#   ScriptLog     ${ERRLOGDIR}/${VHNAME}.cgi_error.log
```
Definitions
: ***ServerName:*** Specifies the primary domain for the virtual host.

: ***ServerAdmin:*** Email address of the server administrator for this host.

: ***ServerAlias:*** Additional domain aliases that point to the same virtual host. Meaning: `mine.test` and `www.mine.test` will both open files in `L:/var/www/mine/htdocs`

: ***DocumentRoot:*** Defines the root directory where the website files for this host are stored.

: ***ScriptAlias:*** Defines the root directory where the CGI files for this host are stored.<br> *I haven't used this is years. That's why they are commented out.*

: ***ErrorLog, TransferLog and ScriptLog:*** Locations and naming conventions for error and access logs related to this virtual host. By keeping all the logs single location and name them per vhost, it makes managing things a bit easier.

> Notice the use of `${VHNAME}` variable.
Oh, when I discovered this I also cried! My life got SO MUSH easier!

The final bit are the directory directives for the virtual host.

```apacheconf
	<Directory />
	    Options Indexes FollowSymLinks IncludesNoExec
	    AllowOverride all
	    Require all granted
	</Directory>
```
 > Complete details are found in [Apache Access Control](https://httpd.apache.org/docs/2.4/howto/access.html) documentation.

### Configuration Shortcut File

Within the new Virtual Hosts directory `L:\var\www\mine` there is Windows "shortcut file" that needs to be updated to open the new configuration file 

- Rename `vh._template.conf` to `vh.mine.conf`
- Open PROPERTIES on this shortcut
- Under SHORTCUT tab, modify the file name as defined in ***TARGET***.

### The HOSTS File:

The Windows HOSTS file needs to be edited to add this new domain.

- Open NOTEPAD "As Administrator". 
- The HOSTS file is located at:<br>
`C:\WINDOWS\system32\drivers\etc\hosts`
- Append this line at the bottom of the file, <br>
`127.0.0.1       mine.local`
- SAVE and close the file.

> You will need to do this each time new add a new Virtual Host.

To test this new virtual host, within the terminal window, execute this command:<br>
`ping mine.local`

This command give this response:<br>
```shell
Pinging mine.local [127.0.0.1] with 32 bytes of data:
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128

Ping statistics for 127.0.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

### Verification and Testing:

To verify the syntax of Apache's configuration file enter this command at the command prompt:
```shell
L:/ httpd -t
```
This return:
```shell
Syntax OK
```
If not, it will give you pretty good messages to try and solve the problem.

If everything is OK, run this command...<br>
```shell
L:/ httpd -S
```

It should give this response:
```shell
VirtualHost configuration:
[::1]:80               localhost (L:/etc/Apache24/conf/conf.vh/httpd-vhosts.conf:41)
127.0.0.1:80           is a NameVirtualHost
         default server localhost (L:/etc/Apache24/conf/conf.vh/httpd-vhosts.conf:41)
         port 80 namevhost localhost (L:/etc/Apache24/conf/conf.vh/httpd-vhosts.conf:41)
                 wild alias *.localhost
         port 80 namevhost mine.local (L:/etc/Apache24/conf/conf.vh/vh.mine.conf:4)
                 wild alias *.mine
ServerRoot: "L:/etc/Apache24"
Main DocumentRoot: "L:/etc/Apache24/htdocs"
Main ErrorLog: "L:/etc/Apache24/logs/error.log"
Mutex default: dir="L:/etc/Apache24/logs/" mechanism=default
PidFile: "L:/etc/Apache24/logs/httpd.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
Define: SRVROOT=/etc/Apache24
Define: CGIDIR=/etc/Apache24/cgi-bin
Define: CONFROOT=/etc/Apache24/conf
Define: ERRLOGDIR=/etc/Apache24/logs
Define: SHARERUNDIR=/etc/Apache24
Define: PRVRUNDIR=/etc/Apache24/logs
Define: MODDIR=/etc/Apache24/modules
Define: DEFAULTDOCROOT=/etc/Apache24/htdocs
Define: VHROOT=/var/www
Define: VHNAME=mine
```

If you do not receive this response, please review this steps to discover the error

### Testing the Web Server:

Initiate the web server by executing `L:/ httpd` in the command line.


## Rinse and Repeat:

For each new virtual host:
1. Clone `/var/www/_template` and give it your new host name
2. Clone `/etc/Appche24/conf/conf.vh/vh.mine.conf` and give it the same name as your new directory
3. Open your new file and change the `VHNAME` definition (line 4) to match your new domain: same as directory and conf file name
4. Update the Shortcut file.
5. Add the new virtual host domain name to your HOSTS file
6. Stop the web server
7. Execute `httpd -t` to validate the new host
8. Restart Web Server
9. Within a browser, enter your new domain


## The horses mouth

For complete and detailed information on Virtual Hosts within Apache, please refer to their website: [Apache Virtual Host documentation](https://httpd.apache.org/docs/2.4/vhosts/)
