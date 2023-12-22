# Apache / PHP Integration

With both [Apache](../apache.md) and [PHP](../../PHP/php.md) installed and verified, it's a short simple step to integrate them both.

I have a set of [pre-defined configuration files](../../assets/apache.php.conf.zip) that define how Apache should access PHP.

Unpack this files into
```shell
L:/etc/Apache/conf/extra/disabled
```

Depending on the version of PHP you're using, move that `conf` file into the `extras` directory.

Restart Apache and open a web browser and navigate to `http://localhost`, this should show the Apache welcome screen you saw when you tested your Apache configuration but with additional information on your PHP install.