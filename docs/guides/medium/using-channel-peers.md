---
layout: default
title: Using channel peers
parent: Medium
grand_parent: Guides
---

# Using channel peers

If you use OpenAF channels there are some cases where you would like to connect them across OpenAF scripts.

To achieve this you can use the *\$ch.expose* and the *\$ch.createRemote* functions that allow you to expose an internal OpenAF to be accessible by other OpenAF scripts remotely.

But if the original OpenAF script which exposed the channel "dies" all the others will no longer be able to access the corresponding data. This might not be the desired scenarion in some cases.

## Peering

But making a mix of *expose* and *createRemote* functions between several OpenAF scripts you can achieve what is provided by the *\$ch.peer* function.

The *\$ch.peer* will expose an OpenAF channel and exchange sync data with a set of "peer" OpenAF scripts that just have to execute the same similar command:

````javascript
$ch("myChannel").peer(12340, 
                      "/myURI", 
                      [ "http://script01:12340/myURI", 
                        "http://script02:12341/myURI", 
                        "http://script03:12343/myURI"]);
````

The signature is:

````javascript
$ch.peer(aLocalPortOrServer, aPath, aRemoteURL, aAuthFunc, aUnAuthFunc)
````

The parameters are similar to the *\$ch.expose* function:

| Parameter | Type | Description |
|-----------|------|-------------|
| aLocalPortOrServer | Object/Number | The local port or a HTTPServer object to hold the HTTP/HTTPs server. |
| aPath | String | The URI where the channel interaction will be performed. |
| aRemoteURL | Array | An array of peer URLs |
| aAuthFunc | Function | This function will be called with user and password. If returns true the authentication is successful. |
| aUnAuthFunc | Function | This function will be called with the http server and the http request. |

If you call it, after the first time, with a different array of aRemoteURL it will replace the existing. If the array references itself it will be ignored.

## Unpeering

To remove a peering you can call:

````javascript
$ch.unpeer(aRemoteURL)
````

## Testing

### Setting up data channels in each peer

First script (on host h1):

````javascript
$ch("data").peer(9080, "/data", [ "http://h1:9080/data", "http://h1:9090/data", "http://h2:9080/data" ]);
````

Second script (on host h1):

````javascript
$ch("data").peer(9090, "/data", [ "http://h1:9080/data", "http://h1:9090/data", "http://h2:9080/data" ]);
````

Third script (on host h2):

````javascript
$ch("data").peer(9080, "/data", [ "http://h1:9080/data", "http://h1:9090/data", "http://h2:9080/data" ]);
````

### Changing and retrieving data

1. On host h2:

````javascript
> $ch("data").size()
0
````

2. On host h1:

````javascript
> $ch("data").size()
0
> $ch("data").setAll(["canonicalPath"], io.listFiles(".").files);
> $ch("data").size()
25
````

3. On host h2:

````javascript
> $ch("data").size()
25
````