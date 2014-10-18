---
layout: post
title: Serve Static Pages with Nginx
date:   2014-10-18 12:59:26
categories: dev-ops nginx server
---

# Ubuntu Setup
- Install Nginx  
  `sudo apt-get install nginx`
- Navigate to
  `/etc/nginx/sites-available`
- Open a new file for editing
- Example configuration  

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

  **Note** Notice the semi-colons at the end of every line  
- Navigate to  
  `/sites/example.com/html`  
- Create an `index.html` and add content  
- (Re)start Nginx  
  `sudo service nginx restart`  
- When you visit `example.com`, you should see the text you entered in html

