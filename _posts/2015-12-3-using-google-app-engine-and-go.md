---
layout: post
title: Using Google App Engine and Go
date: 2015-12-3
categories: development fullstack google-app-engine go
---

In a current project, I'm building a makeshift MVC system on Google App Engine where the view layer is an AgularJS app and the Model-Controller is done in Go.

First thing I did was set up my local dev environment. [There is a good set up tutorial here](https://cloud.google.com/appengine/docs/go/tools/devserver?hl=en).
Generally, when you dev a Go app you need to set the environment variable `$GOPATH` to a directory.
When using the Google App Engine environment, there is a `gopath` directory you can work with in the `go_appengine` directory.
Your application goes in `go_appengine/gopath/src`.
In order for the app server to know what to do, you need to have an app.yaml file in the app root.
Here you can set up routing, where you and make `/` point to the angular app.
You may also need to set up static pointers to static files like css, images, and fonts.
Then, in the last line, set up a catch-all for the REST routes.

```yaml
  application: testapp
  version: 1
  runtime: go
  api_version: go1

  handlers:
  - url: /
    static_files: angular/app/index.html
    upload: angular/app/(.*\.html)
  - url: /.*
    script: _go_app
```
