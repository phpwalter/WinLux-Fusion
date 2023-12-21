# PHP

> This document is valid for all versions for PHP from 5.6.9 through 8.3.1


## Pre-requisites
A solid foundation and framework must be built before anything can be installed. Follow all the instructions in the [Start File](../../FIRST.md), before you begin anything here.

## Setup

Add these Windows Environmental Variables to your System:

### PHP
- Name: PHP
- Value: %etc%\php

> Add %php% to the ***PATH*** variable as well

### PHP_INI_SCAN_DIR
- Name: PHP_INI_SCAN_DIR
- Value: %php%\config

### PHPRC
- Name: PHPRC
- Value: %php%


### Download the Package

Download the curretn version PHP [ZIP package.]https://windows.php.net/downloads/qa/)

Select the chip of your PC (x32 or x64 ) and the current version of PHP.

As of the writing of this document, the current version is:<br>
`php-8.3.1RC3-Win32-vs16-x??.zip`

## Installation

Open the ZIP package and move the contents into `L:/etc/php-8.3`

Ignore the **README** file.

You can close and delete the ZIP file. We're done with it.

Open `L:/etc/php-8.3` and create a new directory labeled '**conf**'.

I have reworked some of the .ini file that come with PHP. In my view, it is  now a bit more logically organized and a bit easier to manage.

Download our customized version of the [PHP INI files](../assets/php_ini_conf.zip), it will make your life a **LOT** easier. The complete details on "How and Why" of the customized PHP INI files can be [read here.](./ini.md)

### Testing, 1, 2, 3, Testing

To test this installation, it's a simple matter of running a couple command line commands.

Change to the "**L:**" volume and run this command.<br>
```shell
C:/> cd L:
L:/> php -v
```

And, if all went well, you should get this response:<br>
```shell
PHP 8.3.1RC3 (cli) (built: Dec  6 2023 23:00:56) (ZTS Visual C++ 2019 x64)
Copyright (c) The PHP Group
Zend Engine v4.3.1RC3, Copyright (c) Zend Technologies
```

> Having placed "**PHP**" in the environment variables, and the **PATH**, the PC knows where this application resides.


## Optional Configuration Procedures

This page was just a basic PHP setup, just to get it running.  These other pages walk you through the various "advanced" features of PHP.

We suggest that you get PHP working with Apache next. It really does help with overall development.

[Configuration Procedures](./optional.md)