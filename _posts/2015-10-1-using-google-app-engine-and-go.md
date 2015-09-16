---
layout: post
title: Using Google App Engine and Go
date: 2015-10-1
categories: development fullstack google-app-engine go
---

In my current project, I'm building a makeshift MVC system on Googla App Engine where the view layer is an AgularJS app and the Model-Controller is done in Go.

First thing I did was set up my local dev environment, there is a good set up tutoprial here: LINK GOES HERE. 
Generally when you dev a GO app you need to set the environment variable GOPATH to a directory. When using the Google App Engine environment there is a gopath directory you can work with in the go_appengine directory.  Your application goes in the ```src``` directory.  In order for the app server to know what to do, you need to have an app.yaml file in the app root.  Here you can set up routing, where you and make ```/``` point to the angular app.

Then, do a catchall for the API'
