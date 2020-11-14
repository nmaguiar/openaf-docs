---
layout: default
title: Setting a proxy
parent: Advanced
grand_parent: Guides
---

# Setting a proxy

Usually the default java proxy settings cover pretty much all cases. But there are a few cases where it would be helpful to programatically set a proxy.

Let's start with the basic proxy settings.

## Setting a HTTP/HTTPs proxy

To set a HTTP/HTTPs proxy you will need the proxy host and the proxy port:

````javascript
ow.loadObj();
ow.obj.setHTTPProxy("a.host", 1234);
ow.obj.setHTTPSProxy("a.host", 1234)
````

After this all HTTP/HTTPs communications in OpenAF will use the provided proxy.

Keep in mind that any external processes/scripts executed from OpenAF (e.g. executing sh("someCommand")) won't inherit these proxy settings.

## Setting a SOCKS proxy

Nevertheless the most interesting case is connecting to a SOCKS proxy. If you are on machine A but you need to access resources through machine B running OpenAF on machine A like it was running on machine B you can establish a simple dynamic port forwarding with SSH. To establish this simple execute on machine A:

````sh
ssh -D 12345 myuser@machine.b
````

Afterwards, in OpenAF, just execute:

````javascript
ow.loadObj();
ow.obj.setSOCKSProxy("127.0.0.1", 12345);
````

Now all network connections, from OpenAF, will go through th socks proxy actually feeling like you are executing OpenAF on machine B.

_Note: if a SOCKS proxy user & password is needed you can add it as extra parameters._

Keep in mind that any external processes/scripts executed from OpenAF (e.g. executing sh("someCommand")) won't inherit these proxy settings.

## Setting a FTP proxy

Although less used you can also set a proxy for FTP connections:

````javascript
ow.loadObj();
ow.obj.setFTPProxy("a.host", 1234);
````