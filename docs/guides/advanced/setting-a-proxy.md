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
ow.obj.setHTTPProxy("a.host", 1234)
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
ow.loadObj()
ow.obj.setSOCKSProxy("127.0.0.1", 12345)
````

Now all network connections, from OpenAF, will go through th socks proxy actually feeling like you are executing OpenAF on machine B.

_Note: if a SOCKS proxy user & password is needed you can add it as extra parameters._

Keep in mind that any external processes/scripts executed from OpenAF (e.g. executing sh("someCommand")) won't inherit these proxy settings.

## Setting a FTP proxy

Although less used you can also set a proxy for FTP connections:

````javascript
ow.loadObj()
ow.obj.setFTPProxy("a.host", 1234)
````

## Setting a proxy per execution

If you want to set the proxy to be set permanently you can use _ow.obj.set*Proxy_ functions in your $HOME/.openaf_profile or $OAF_ROOT/.openaf_profile.

Set for a single execution (for example, to use with _oafp_) you can use _OAF\_JARGS_ for this. For example:

```bash
OAF_JARS="-DsocksProxyHost=my.socks.proxy -DsocksProxyPort=12345" oafp url="https://ifconfig.co/json"
```

List of proxy variables to use per execution:

| Type | Settings |
|------|----------|
| SOCKS | ```OAF_JARS="-DsocksProxyHost=my.socks.proxy -DsocksProxyPort=12345 -Djava.net.socks.username=scott -Djava.net.socks.password=tiger"``` |
| HTTP | ```OAF_JARS="-Dhttp.proxyHost=my.http.proxy -Dhttp.proxyPort=3128 -Dhttp.nonProxyHosts=localhost"``` |
| HTTPS | ```OAF_JARS="-Dhttps.proxyHost=my.http.proxy -Dhttps.proxyPort=3128 -Dhttp.nonProxyHosts=localhost"``` |
| FTP | ```OAF_JARS="-Dftp.proxyHost=my.http.proxy -Dftp.proxyPort=3128 -Dftp.nonProxyHosts=localhost"``` |