# Apache MOD - Rewrite

This module is a versatile tool that allows web admins and developers to manipulate URLs and control how the server handles requests. Comprehending mod_rewrite is a pivotal step in mastering the art of configuring web server behavior.

At its core, mod_rewrite is an Apache module that provides a way to modify (rewrite) incoming URLs. It enables the server to manipulate URLs on the fly, allowing for modifying URL paths, query strings, and other request attributes before sending the request to the intended destination.

## Common Uses of mod_rewrite:

1. ***URL Rewriting:*** One of the primary uses of mod_rewrite is to rewrite URLs in a more user-friendly or SEO-friendly format. For instance, transforming a complex URL like `example.com/page.php?id=123` into a cleaner and more readable URL like `example.com/products/123`.

2. ***Redirects:*** Redirecting URLs is another frequent task. For instance, permanently redirecting visitors from an old URL to a new one, for instance `example.com/products/123` into `example.com/items/123`

3. ***Blocking/Filtering Requests:*** Mod_rewrite can also be used to block or filter requests based on specific conditions. For example, blocking access to certain directories or files:


## Installing MOD_rewrite

- Open `/etc/Apache24/httpd_modules.conf` in your favorite editor
- Search for "#LoadModule rewrite_module modules/mod_rewrite.so"
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
- This should display a list installed modules, in alphabetical order. You should see `rewrite_module (shared)` toward the bottom.

> See the official [Apache documentation](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) on how to use this module.