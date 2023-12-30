# Creating Self-Signed SSL Certificates

Securing your website with SSL (Secure Sockets Layer) certificates is crucial for protecting sensitive information exchanged between users and your server. Commercial SSL certificates are an industry standard, but they can be expensive and are not required for local development environments. Creating self-signed SSL certificates can be an initial step for testing or internal purposes.

Before anything SSL must be installed on the Apache Server. Details are in [this document](./ssl.md).

## Configuration for self-signed Certificates

Understanding and configuring the OpenSSL.cnf file allows for tailored SSL certificate generation and management. Users can create certificates customized for their specific requirements by adjusting settings within this file. Remember to back up the original file before making changes and test your configurations to ensure they work correctly within your Apache environment.

- open `/etc/Apache24/conf/openssl.cnf`


## Generate a Self-Signed SSL Certificate

- Open Command Prompt as an administrator.
- navigate to the Apache `bin` directory
```shell
cd %apache%/bin
```
- run the following command to generate the SSL certificate and key:
```shell
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout server.key -out server.crt
```