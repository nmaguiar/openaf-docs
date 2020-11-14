---
layout: default
title: Micro remote HTTP server file browser
parent: Beginner
grand_parent: Guides
---

# Micro remote HTTP server file browser

There is an emergency! Time is ticking and you need to quickly solve things. You need to copy files from A to B and there isn't any sftp, scp, ftp, shared volumes/drives, etc&#46;&#46;&#46; Security? you just need a minute with a quick http server up and running. Should you install Apache, ngnix, &#46;&#46;&#46;? Well having the OpenAF "swiss army knife" with me it just a couple of YAML lines and running an OpenAF's oJob. Just copy+paste to a httpd.yaml file:

````yaml
init:
  port  : &PORT   8888
  folder: &FOLDER .

ojob:
  daemon: true
  opacks:
    - oJob-common

include:
  - oJobHTTPd.yaml


todo:
  # -----------------------
  - name: HTTP Start Server
    args:
      port   : *PORT
      mapLibs: true
  # ------------------
  - name: Browse files

jobs:
  # -----------------
  - name: Browse files
    to  : HTTP File Browse
    args:
      uri : /
      port: *PORT
      path: *FOLDER
````

Change the PORT and the FOLDER if needed. Execute:

````bash
/my/openaf/ojob httpd.yaml
````

and you have yourself a micro/temporary/easy http file browsing server to copy files from A (running the yaml ojob) to B (pointing the browser to http://ip.address.of.A:8888):

![micro-remote-http-server-file-browser-1](micro-remote-http-server-file-browser-1.png)