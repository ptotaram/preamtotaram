---
layout: post
title: I've stopped using config files
date: 2016-4-3
categories: development backend
---

In the last HTTP API I've built, I decided to drop the environment config files.
Although it was how things were generally done, I thought about it and wondered why I would expose sensitive information like my database password and AWS keys in my codebase.
After a little consideration, I thought about using environment variables, instead.
After consideration I realized it was the best way to go.
I wouldn't have to worry about setting up an environment fallback structure.
In this situation I would just have to set the variables in the environment, and refer to the variables.
I can also keep sinsitive information out of my codebase for security concerns.

##Setting Environment Variables

Because I've made a conscious decision to keep my development unix-based, so I do not not know about Windows servers to comfortably include them in my blog posts.
However, creating an environment variable in Unix is easy just use the `export` command.
Remember that when you close the terminal instance you will loose the environment variable.
Save it to your .zshrc, .bashrc, .bash_profile, or which ever file you may be using.

```

Example:

export VAR_NAME="value"

```

##Accessing Environment Varibales
Here is how the environment variables are accessed in some languages I use/experiment with.
Some languages (like PHP) have a lot of frameworks that have wrappers for doing this.
I would suggest to use the wrappers, they are usually cleaner.

###NodeJs

```
process.env.VAR_NAME
```

###PHP

```
$_SERVER['VAR_NAME']
```

###Go

```
import "os"

func main() {
  os.Getenv("VAR_NAME")
}
```

###C++

```
#include <cstdlib>

int main()
{
  std::getenv("VAR_NAME");
}

```

###Java

```
java.lang.System.getenv("VAR_NAME");
```

###Ruby

```
ENV['VAR_NAME']
```

###Python

```
import os
os.environ['VAR_NAME']
```

