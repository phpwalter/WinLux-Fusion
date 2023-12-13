# Apache 2.2.x

## Pre-requisites
A solid foundation and framework must be built before anything can be installed. Follow all the instructions in the [Start File](../../FIRST.md), before you begin anything here.

## Setup

> This document is valid as of Apache v2.2.4 ==

### But First!

You need to install the latest 14.38.33130 Visual C++ Redistributable [Visual Studio 2015-2022](https://aka.ms/vs/17/release/VC_redist.x64.exe)

### Download the Package

Download the [ZIP package.](https://www.apachelounge.com/download/)

Select the chip of your PC (32 or 64 bit) and the current version of Apache.

## Installation

Open the ZIP package and move the "Apache24" directory into `L:/etc`

Ignore the **README** file.

You can close and delete the ZIP file. We're done with it.

Open `L:/etc/Apache24` and rename the existing '**conf**' to '**conf.org**'

I have reworked some of the conf files that come with Apache. In my view, they are now a bit more logically placed and a bit easier to edit.

Download our customized version of the [Apache CONF files](../assets/conf.zip), it will make your life a **LOT** easier. The complete details on "How and Why" of the customized Apache CONF files can be [read here.](./conf.md)

### Last Step
One last step before we can test our installation.

Copy the directory `L/var/www/_template` to `L/var/www/localhost` 

This will be the default directory web pages can be served from.

## Testing, 1, 2, 3, Testing

To test our installation, it's a simple matter of running a couple command line commands.

Change to the "**L:**" volume and run this command.<br>
`C:/> cd L:`<br>
`L:/> httpd -t`<br>

And, if all went well, you should get this response:<br>
`Syntax OK`<br>
`L:/> |`

> Having placed "**Apache24**" in the environment variables, and the **PATH**, the PC knows where this application resides.


At this point we can test to see if Apache is working with what we have.

At the command prompt...

`L:/> httpd`

This should hesitate for a minute and then the cursor should drop to the next line. At this point it either works or not.

Open your browser enter the localhost URL into the address bar...

`http://localhost`

This will either give you the default "It works!" screen or a 404 error.

If this failed, something went wrong with your file/directory layout. Simply wipe what you have and start again.

Control C (a few times) and ENTER to exit Apache.


###Last Items

The last item of business for Apache is whether to run this as a SERVICE [*a Windows version of a daemon*], which will be "always on" or do you want to turn the web server on when you want to.

- The upside: It's always available
- The downside: It takes some resources just to sit idly wait for requests. Also, if you've not secured your windows properly, others can try to hack in [but they won't get anywhere].

### Windows Service, or Not

If you wish to start Apache manually each time, just enter

`L:/> httpd`

at the command prompt and Apache will begin as a temporary background process.

Actually, it is easier to use the Apache Monitor (described below) to turn on and off Apache.

If you wish Apache to be "always on", then it has to be installed as a Windows Service. To do this, just enter

`L:/> httpd -n Apache -k install`

This will install Apache as a Windows Service with the name ''**Apache**''. Each time you start your PC, Apache will start as well.

### The Apache Monitor

Within the Apache/bin directory, there is a small app called ''**ApacheMonitor.exe**''. Create a shortcut to this file and drop in the STARTUP folder of the START menu.

> Press the Windows logo key + R, type shell:startup, then select OK. This opens the Startup folder. Copy and paste the shortcut here.

Now each time you log in, this monitor will launch and display itself in the task bar next to the clock. I use this tool to stop and start Apache whenever I need to change a conf file, or it hangs for some reason.

<note>This only works on the local PC on which Apache is installed.</note>

## Optional Configuration Procedures

This page was just a basic Apache setup, just to get it running.  These other pages walk you through the various "advanced" features of Apache.

We suggest that you get Virtual Hosts working next. It really does help with overall development. We've found that placing **phpMyadmin** (for example) as its own Virtual Hosted Name makes getting to it a lot easier. Using Virtual Hosts also keeps projects separate and easier to work with.

[Configuration Procedures](./optional.md)
