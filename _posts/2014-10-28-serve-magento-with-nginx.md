---
layout: post
title:  Serve Magento sites with Nginx
date: 2014-10-28
categories: dev-ops nginx php server
---

#How do I host a Magento Site using Nginx (Ubuntu Setup)

In my [previous post](http://preamtotaram.com/dev-ops/nginx/php/server/2014/10/23/serve-php-files-with-nginx.html), I explained to to serve PHP files with nginx.  Refer to that to configure PHP-FPM.  To serve a magento site is really not diffucult.  I was able to do this with the help of the [Magento Wiki](http://www.magentocommerce.com/wiki/1_-_installation_and_configuration/configuring_nginx_for_magento).  Because Magento uses `.htaccess` files, it would generally require less configuration to accomplish this with `Apache`. This is what my magento server block looks like.

```
server {
  listen 80;
  server_name example.com;
  root /sites/example.com;
  location / {
    index index.html index.php;
    expires 30d;
  }

  location ^~ /app/                { deny all; }
  location ^~ /includes/           { deny all; }
  location ^~ /lib/                { deny all; }
  location ^~ /media/downloadable/ { deny all; }
  location ^~ /pkginfo/            { deny all; }
  location ^~ /report/config.xml   { deny all; }
  location ^~ /var/                { deny all; }

  location /. {
    return 404;
  }

  location @handler {
    rewrite / /index.php;
  }

  location ~ .php/ {
    rewrite ^(.*.php)/ $1 last;
  }

  location ~ .php$ {
    if (!-e $request_filename) { rewrite / /index.php last; }

    expires             off;
    fastcgi_pass        unix:/var/run/php5-fpm.sock;
    fastcgi_param       SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_param       MAGE_RUN_CODE default;
    fastcgi_param       MAGE_RUN_TYPE store;
    #used for development and staging encironments
    fastcgi_param       MAGE_IS_DEVELOPER_MODE true;
    include             fastcgi_params;
  }
}
```
