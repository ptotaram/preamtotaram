---
layout: post
title: Serve PHP files with Nginx
date: 2014-10-23
categories: dev-ops nginx php server
---

#How do I serve PHP files (Ubuntu Setup)
Continued from previous post, [Serve Static Pages with Nginx](http://preamtotaram.com/dev-ops/nginx/server/2014/10/18/serve-static-pages-with-nginx.html).

You can start from a server block that looks like this

```
server {
  listen 80;

  server_name example.com;

  root /sites/example.com/html;

  index index.html index.htm;

  location / {
    try_files $uri $uri/ =404;
  }
}
```
At this point you need PHP-FPM
`sudo apt-get install php5-fpm`

Given that you are using linux, you will want PHP-FPM to run on a UNIX socket.
-  Open `/etc/php5/fpm/pool.d/www.conf` for editing.
-  Find the line that says `listen = 127.0.0.1:9000` and change the value to `/var/run/php5-fpm.sock`  
-  Restart PHP-FPM `sudo service php5-fpm restart`

After this, you would need to add a new location block that would look like this

```
location ~ [^/]\.php(/|$){
  fastcgi_pass unix:/var/run/php5-fpm.sock;
  fastcgi_index index.php;
  include fastcgi_params;
}
```

If you restart nginx and reload the page at this point, nginx throws returns a `403 Forbidden` error  
This is because you need to add `index.php` to
```
index index.php index.html index.htm;
```
