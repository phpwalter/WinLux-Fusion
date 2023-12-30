# SSL in Apache Web Servers

Protecting sensitive information exchanged between web servers and users is crucial in maintaining security online. A fundamental aspect of this safeguarding is SSL (Secure Sockets Layer), a protocol extensively employed to encrypt data and create a secure link between a web server and a browser. In Apache web servers, SSL is pivotal in enhancing the integrity and confidentiality of data transmitted over the internet. SSL certificates, provided by trusted third-party entities called Certificate Authorities (CAs), validate the server's identity, ensuring users connect to legitimate websites.

## Preqs

[OpenSSL for Windows](../../OpenSSL/openssl.md) should be installed first.

## Installing and Verifying SSL

- Open `/etc/Apache24/httpd_modules.conf` in your favorite editor
- Search for "#LoadModule ssl_module modules/mod_ssl.so"
- Remove the asterisk from the beginning of the line
- Save and close the file.
- Restart your Apache Server

## Verify Installation

- open command window enter these commands
```shell
C:/> cd %apache%
C:/> L:
L:/> httpd -t -D DUMP_MODULES
```
- This should display a list installed modules, in alphabetical order. You should see `ssl_module (shared)` toward the bottom.

> See the official [Apache documentation](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html) on how to use this module.


## SSL Certificates

Read these [detailed instructions](./certs.md) on how to create and install a "self-signed" SSL certificate


509 info
https://www.openssl.org/docs/man1.1.1/man5/x509v3_config.html