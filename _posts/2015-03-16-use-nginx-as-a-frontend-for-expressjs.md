---
layout: post
title: Use Nginx as a frontend for ExpressJs
date: 2015-03-16
categories: dev-ops nginx javascript nodejs expressjs
---

When learning Node and Express, I was searching the web for a way to use Nginx as the front-end.  I couldn't find a blog post that simply explained how to do this, so I decided to write one.

After running the Express server (on port 3000, for example), you want Nginx to see that and render what ever is on port 3000.  Here is my configuration file.

```
upstream project {
  server localhost:3000;
}

server {
  listen 80;
  location / {
    proxy_pass http://project;
  }
}
```

Project is just a keyword to be used in the `server` block, you can choose you own, what ever makes the most sense semantically.  Also, you can have the Express instance on a different server and just include the IP rather than `localhost`.  By adding multiple instances in the upstream block, you can have Nginx function as a load balancer.

**Side Note**  
The web server instances in the upstream block can be web server: Nginx, Apache, MeteorJs, PHP Webserver (I would advise not use the PHP Web Server in production), or Node Web Server, as examples.