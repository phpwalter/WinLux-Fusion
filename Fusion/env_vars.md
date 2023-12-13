## Application Setup
Open the "Advanced System Settings" and hit the "Environment Variables..." toward the bottom of the window.

Be sure to add these variables in the lower panel, "System variables".

Notice that some definitions have a trailing slash '\' and others do not. This is important.

### Apache
- Name: Apache
- Value: %etc%\Apache24\bin\

### Composer
- Name: COMPOSER_HOME
- Value: %etc%\composer

### GIT
- Name: GIT
- Value: %etc%\git\bin

### MySQL
- Name: MySQL
- Value: %etc%\mysql\bin\

### PHP
- Name: PHP
- Value: %etc%\php

### PHP_INI_SCAN_DIR
- Name: PHP_INI_SCAN_DIR
- Value: %php%\config

### PHPRC
- Name: PHPRC
- Value: %php%

### NPM
- Name: npm
- Value: %etc%\node.js


### SSH2
- Name: SSH2
- Value: %etc%\ssh2


## Unix Stuff
### Cmd Line Tool paths

#### etc
- Name: etc
- Value: L:\etc

#### Term
- Name: Term:
- Value: vt100

#### Timezone
- Name: TZ
- Value: {[Select your TimezoneList of TimeZone](https://gist.github.com/alejzeis/ad5827eb14b5c22109ba652a1a267af5)}

#### Main Tool directory
- Name: UnixDOS
- Value: L:\bin

#### user/bin
- Name: usr-bin
- Value: L:\usr\bin

#### user/sbin
- Name: usr-sbin
- Value: L:\usr\sbin

#### TMP
- Name: TMP
- Value: L:\tmp

#### TEMP
- Name: TEMP
- Value: %tmp%


## Windows Tie-In
Add each of these variables into the PATH variable.
Don't forget to add the percent sign before and after each name. ie: %php%
