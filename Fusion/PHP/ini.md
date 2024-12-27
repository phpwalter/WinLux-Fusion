# PHP INI Customization

The standard PHP `ini` file contains a large collection of settings that allow PHP to be customized and optimized for almost any situation.

I found that it being such a large file hampered my ability to fully understand the options PHP offered.

This collection of `ini` files is the various pats of the original file split into its logical, defined, sections. 

The EXTENSIONS definitions have also been pulled out into their separate ini files. This method allows you to simply move the `ini` file for a particular extension your interested into the main `conf` directory and update the options of the extension as needed.

If this is of interest:
1. rename your local copy of `php.ini` to `php.ini.org`
2. pull this [ZIP file](../assets/php_ini_conf.zip) containing the separated segments
3. unpack the ZIP file and place the new `php.ini` and the `conf` directory into your `php` main directory.
5. create a new ENVIRONMENTAL VARIABLE and label it `PHP_INI_SCAN_DIR` and define its value as the path to your PHP directory; `%php%`.

To test if this works as planned:
- open a command window
- enter:
```shell
php --ini
```
you should get back...
```shell
Configuration File (php.ini) Path:
Loaded Configuration File:         L:\etc\php\php.ini
Scan for additional .ini files in: L:\etc\php\conf
Additional .ini files parsed:      L:\etc\php\conf\data_handling.ini,
L:\etc\php\conf\errors_logging.ini,
L:\etc\php\conf\extensions.ini,
L:\etc\php\conf\file_uploads.ini,
L:\etc\php\conf\fopen_wrappers.ini,
L:\etc\php\conf\paths.ini,
L:\etc\php\conf\res_limits.ini
```

That's it.

Review [PHP Optional Configurations](./optional.md) for details on how to manage these files.
