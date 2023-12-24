# PHP Extensions - Apache Integration

## Installation of Xdebug on Windows:
- **Step 1: Verify PHP Installation:** Open Command Prompt and type php -v to ensure PHP is installed. If not installed, visit php.net, download the PHP installer, and follow the installation instructions.

- **Step 2: Download Xdebug:** Visit xdebug.org/download.php.
Select the appropriate Xdebug version based on your PHP version (Non-TS or TS). Download the Xdebug DLL file, for example: `php_xdebug-3.1.1-8.0-vc16-x86_64.dll`.

- **Step 3: Place Xdebug DLL in PHP Extension Directory** Assuming your PHP installation is in `L:\etc\php`, follow these steps:
  - Navigate to `L:\etc\php`
  - Move the downloaded `php_xdebug-3.1.1-8.0-vc16-x86_64.dll` into the `ext` directory.
- **Step 4: Configure PHP**
  - Navigate to `L:\etc\php\conf`
  - Move `php_xdebug.ini` from `disabled` into `conf`
  - Open `php_xdebug.ini` in your favorite editor
  - Replace the name of the DDL defined in line 7 with the file name just downloaded
  - Refer to [official documentation](https://xdebug.org/docs/) on configuring this extension,

- **Step 5: Restart Apache Server:** Open Command Prompt as an administrator. Type `httpd -k` restart to restart the Apache server.

- **Step 6: Verify Xdebug Installation:**
  - Open a browse and navigate to `http:\\localhost`.
  - `CTL-F` (find) enter `xdebug` to confirm Xdebug installation.
 
 
## Testing Xdebug:

(*On the assumption you completed the [Apache Virtual Host](../../Apache/mods/vhost.md) section*)

- **Step 1 Test File:** 
  - Navigate to `/var/www/localhost/htdocs`
  - Create a PHP file named `test.php` with the code below.
```php
<?php
$number = 5;
for ($i = 0; $i < $number; $i++) {
    echo "The number is: $i <br>";
}
?>
```
 - ** Step 2: Running debugger**
   - Open `http:\\localhost\test.php` in your browser.
   - Use an IDE like PhpStorm or Visual Studio Code with an Xdebug extension.
   - Set breakpoints in the PHP code.
   - Start a debugging session in your IDE and execute `test.php` in the browser.
   - The debugger should pause at the breakpoints, allowing you to inspect variables and step through the code.

By following these steps and conducting the testing process, you've successfully installed and tested Xdebug on your Windows system. If you encounter issues, consult official documentation or seek help from online communities for further assistance.