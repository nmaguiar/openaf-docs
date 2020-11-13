---
layout: default
title: "Beginner: Accessing environment variables"
parent: Guides
grand_parent: OpenAF docs
---

# Accessing environment variables

If you previously wrote any type of script you probably, sooner or later, want to access environment variables. OpenAF is no different and access to the operating system environment variables it's very easy with getEnv and getEnvs functions:

````javascript
> getEnvs()
{
   "PATH": "/some/dir:/usr/bin",
   "SHELL": "/bin/bash",
   "CUSTOM": "something",
//...
````

_getEnvs_ will retrieve a map of the current environment variables. To retrieve a specific environment variable you can directly access the map:

````javascript
> getEnvs()["CUSTOM"]
"something"
````

or use _getEnv_ directly:

````javascript
> getEnv("CUSTOM")
"something"
````