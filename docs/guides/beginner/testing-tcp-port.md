---
layout: default
title: Testing a TCP port
parent: Beginner
grand_parent: Guides
---

# Testing a TCP port

When performing TCP connections you always have to deal with the eventual connection failure. For example, if you write a script that will connect to a specific server, you should deal with the issue that when executing the script might not have connectivity to the desire target.

So how to handle these events? The typical answer is waiting for the connection error exception and deal with it. For example:

````javascript
try {
    // make the TCP call
} catch(e) {
    // handle the exception
}
````

You should always handle the exception but you can avoid even going into the try/catch block with a quick TCP connectivy check:

````javascript
ow.loadNet()

var host = "my.service.host"
var port = 1234

if (ow.net.testPort(host, port)) {
    var result
    try {
        result = callService(host, port, params)
        // process result
    } catch(e) {
        logErr("Problem calling service on " + host + ":" + port)
    }
} else {
    logErr("No connectivity to " + host + ":" + port)
}
````

The _ow.test.testPort_ function allows for quick socket connection tests. By default it timeouts after 1.5 seconds but you can change that using a third parameter:

````javascript
// Wait 5 seconds before declaring farAway service not reachable (false)
ow.test.testPort(farAwayHost, farAwayPort, 5000);
````