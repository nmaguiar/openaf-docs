---
layout: default
title: http
parent: Reference
grand_parent: OpenAF docs
---


## http

### HTTP.exec

__HTTP.exec(aUrl, aRequestType, aIn, aRequestMap, isBytes, aTimeout, returnStream) : Object__

````
Builds a HTTP request for the aURL provided with aRequestType (e.g. "GET" or "POST") sending aIn body request (or "") and optionally sending aRequestMap headers and optionally specifying  if the response isBytes and providing an optional custom HTTP aTimeout.  If returnStream = true the response and return value will be in the form of a JavaStream.
````
### HTTP.exec

__HTTP.exec(aUrl, aRequestType, aIn, aRequestMap, isBytes, aTimeout, returnStream) : Object__

````
Builds a HTTP request for the aURL provided with aRequestType (e.g. "GET" or "POST") sending aIn body request (or "") and optionally sending aRequestMap headers and optionally specifying  if the response isBytes and providing an optional custom HTTP aTimeout.  If returnStream = true the response and return value will be in the form of a JavaStream.
````
### HTTP.get

__HTTP.get(aUrl, aIn, aRequestMap, isBytes, aTimeout, returnStream)__

````
Builds a HTTP request for the aURL with a POST sending aIn body request (or "") and optionally sending aRequestMap headers and optionally specifying  if the response isBytes and providing an optional custom HTTP aTimeout. If returnStream = true, the response will be in  the form of a JavaStream (please use the returnStream function).
````
### HTTP.get

__HTTP.get(aUrl, aIn, aRequestMap, isBytes, aTimeout, returnStream)__

````
Builds a HTTP request for the aURL with a POST sending aIn body request (or "") and optionally sending aRequestMap headers and optionally specifying  if the response isBytes and providing an optional custom HTTP aTimeout. If returnStream = true, the response will be in  the form of a JavaStream (please use the returnStream function).
````
### HTTP.getBytes

__HTTP.getBytes(aUrl, aIn, aRequestMap, aTimeout)__

````
Builds a HTTP request returning bytes for the aURL with a GET sending aIn body request (or "") and optionally sending aRequestMap headers and providing an optional custom HTTP aTimeout.
````
### HTTP.getBytes

__HTTP.getBytes(aUrl, aIn, aRequestMap, aTimeout)__

````
Builds a HTTP request returning bytes for the aURL with a GET sending aIn body request (or "") and optionally sending aRequestMap headers and providing an optional custom HTTP aTimeout.
````
### HTTP.getErrorResponse

__HTTP.getErrorResponse() : Object__

````
Returns the HTTP request error result string.
````
### HTTP.getErrorResponse

__HTTP.getErrorResponse() : Object__

````
Returns the HTTP request error result string.
````
### HTTP.getResponse

__HTTP.getResponse() : Object__

````
Returns the HTTP request result string or array of bytes.
````
### HTTP.getResponse

__HTTP.getResponse() : Object__

````
Returns the HTTP request result string or array of bytes.
````
### HTTP.getStream

__HTTP.getStream(aUrl, aIn, aRequestMap, aTimeout)__

````
Builds a HTTP request, returning a JavaStream, for the aURL with a GET sending aIn body request (or "") and optionally sending aRequestMap headers and optionally providing a custom HTTP aTimeout.
````
### HTTP.getStream

__HTTP.getStream(aUrl, aIn, aRequestMap, aTimeout)__

````
Builds a HTTP request, returning a JavaStream, for the aURL with a GET sending aIn body request (or "") and optionally sending aRequestMap headers and optionally providing a custom HTTP aTimeout.
````
### HTTP.http

__HTTP.http(aURL, aRequestType, aIn, aRequestMap, isBytes, aTimeout, returnStream)__

````
Builds a HTTP request for the aURL provided with aRequestType (e.g. "GET" or "POST") sending aIn body request (or "") and optionally sending aRequestMap headers and optionally specifying  if the response isBytes and providing an optional custom HTTP aTimeout.   If needed use java.lang.System.setProperty("sun.net.http.allowRestrictedHeaders", "true") to  allow you to use restricted request headers. If returnStream = true, the response will be in  the form of a JavaStream (please use the returnStream function).
````
### HTTP.http

__HTTP.http(aURL, aRequestType, aIn, aRequestMap, isBytes, aTimeout, returnStream)__

````
Builds a HTTP request for the aURL provided with aRequestType (e.g. "GET" or "POST") sending aIn body request (or "") and optionally sending aRequestMap headers and optionally specifying  if the response isBytes and providing an optional custom HTTP aTimeout.   If needed use java.lang.System.setProperty("sun.net.http.allowRestrictedHeaders", "true") to  allow you to use restricted request headers. If returnStream = true, the response will be in  the form of a JavaStream (please use the returnStream function).
````
### HTTP.login

__HTTP.login(aUser, aPassword, forceBasic, urlPartial)__

````
Tries to build a simple password authentication with the provided aUser and aPassword (encrypted or not). By default it tries to use the Java Password Authentication but it forceBasic = true it will force basic authentication to be use. It's advisable to use urlPartial to associate a login/password to a specific URL location.
````
### HTTP.login

__HTTP.login(aUser, aPassword, forceBasic, urlPartial)__

````
Tries to build a simple password authentication with the provided aUser and aPassword (encrypted or not). By default it tries to use the Java Password Authentication but it forceBasic = true it will force basic authentication to be use. It's advisable to use urlPartial to associate a login/password to a specific URL location.
````
### HTTP.response

__HTTP.response() : String__

````
Returns the HTTP request result as a string (if isBytes = false or default)
````
### HTTP.response

__HTTP.response() : String__

````
Returns the HTTP request result as a string (if isBytes = false or default)
````
### HTTP.responseBytes

__HTTP.responseBytes() : ArrayOfBytes__

````
Returns the HTTP request result as an array of bytes (if isBytes = true)
````
### HTTP.responseBytes

__HTTP.responseBytes() : ArrayOfBytes__

````
Returns the HTTP request result as an array of bytes (if isBytes = true)
````
### HTTP.responseCode

__HTTP.responseCode() : Number__

````
Returns the HTTP request response code (e.g. 404, 500, ...)
````
### HTTP.responseCode

__HTTP.responseCode() : Number__

````
Returns the HTTP request response code (e.g. 404, 500, ...)
````
### HTTP.responseHeaders

__HTTP.responseHeaders() : Map__

````
Returns a Map with the response headers of the HTTP request.
````
### HTTP.responseHeaders

__HTTP.responseHeaders() : Map__

````
Returns a Map with the response headers of the HTTP request.
````
### HTTP.responseStream

__HTTP.responseStream() : JavaStream__

````
Returns a JavaStream if the option of returnStream = true in the previous instance function called.
````
### HTTP.responseStream

__HTTP.responseStream() : JavaStream__

````
Returns a JavaStream if the option of returnStream = true in the previous instance function called.
````
### HTTP.responseType

__HTTP.responseType() : String__

````
Returns the HTTP request response content mime type.
````
### HTTP.responseType

__HTTP.responseType() : String__

````
Returns the HTTP request response content mime type.
````
### HTTP.wsClient

__HTTP.wsClient(anURL, onConnect, onMsg, onError, onClose, aTimeout, supportSelfSigned) : WebSocketsReply__

````
Tries to establish a websocket connection (ws or wss) and returns a jetty WebSocketClient java object. As callbacks you should defined onConnect, onMsg, onError and onClose. The onConnect callback will  provide, as argument, the created session that you should use to send data; the onMsg callback will provide, as arguments, aType (either "text" or "bytes"), aPayload (string or array of bytes) and an offset and length (in case type is "bytes"); the onError callback will provide the cause; the onClose callback will provide aStatusCode and aReason. You can optionally provide aTimeout (number) and indicate if self signed SSL certificates should be accepted (supportSelfSigned = true). Example:

plugin("HTTP");
var session; var output = "";
var res = (new HTTP()).wsClient("ws://echo.websocket.org",
  function(aSession) { log("Connected"); session = aSession; },
  function(aType, aPayload, aOffset, aLength) { if (aType == "text") output += aPayload; },
  function(aCause) { logErr(aCause); },
  function(aStatusCode, aReason) { log("Closed (" + aReason + ")"); }
);
session.getRemote().sendString("Hello World!");
while(output.length < 1) { sleep(100); };
res.client.stop();
print(output);

NOTE: this functionality is only available if used with JVM >= 1.8


````
### HTTP.wsClient

__HTTP.wsClient(anURL, onConnect, onMsg, onError, onClose, aTimeout, supportSelfSigned) : WebSocketsReply__

````
Tries to establish a websocket connection (ws or wss) and returns a jetty WebSocketClient java object. As callbacks you should defined onConnect, onMsg, onError and onClose. The onConnect callback will  provide, as argument, the created session that you should use to send data; the onMsg callback will provide, as arguments, aType (either "text" or "bytes"), aPayload (string or array of bytes) and an offset and length (in case type is "bytes"); the onError callback will provide the cause; the onClose callback will provide aStatusCode and aReason. You can optionally provide aTimeout (number) and indicate if self signed SSL certificates should be accepted (supportSelfSigned = true). Example:

plugin("HTTP");
var session; var output = "";
var res = (new HTTP()).wsClient("ws://echo.websocket.org",
  function(aSession) { log("Connected"); session = aSession; },
  function(aType, aPayload, aOffset, aLength) { if (aType == "text") output += aPayload; },
  function(aCause) { logErr(aCause); },
  function(aStatusCode, aReason) { log("Closed (" + aReason + ")"); }
);
session.getRemote().sendString("Hello World!");
while(output.length < 1) { sleep(100); };
res.client.stop();
print(output);

NOTE: this functionality is only available if used with JVM >= 1.8


````
### HTTP.wsConnect

__HTTP.wsConnect(anURL, onConnect, onMsg, onError, onClose, aTimeout, supportSelfSigned) : WebSocketClient__

````
Tries to establish a websocket connection (ws or wss) and returns a jetty WebSocketClient java object. As callbacks you should defined onConnect, onMsg, onError and onClose. The onConnect callback will  provide, as argument, the created session that you should use to send data; the onMsg callback will provide, as arguments, aType (either "text" or "bytes"), aPayload (string or array of bytes) and an offset and length (in case type is "bytes"); the onError callback will provide the cause; the onClose callback will provide aStatusCode and aReason. You can optionally provide aTimeout (number) and indicate if self signed SSL certificates should be accepted (supportSelfSigned = true). Example:

plugin("HTTP");
var session; var output = "";
var client = (new HTTP()).wsConnect("ws://echo.websocket.org",
  function(aSession) { log("Connected"); session = aSession; },
  function(aType, aPayload, aOffset, aLength) { if (aType == "text") output += aPayload; },
  function(aCause) { logErr(aCause); },
  function(aStatusCode, aReason) { log("Closed (" + aReason + ")"); }
);
session.getRemote().sendString("Hello World!");
while(output.length < 1) { sleep(100); };
client.stop();
print(output);

NOTE: this functionality is only available if used with JVM >= 1.8


````
### HTTP.wsConnect

__HTTP.wsConnect(anURL, onConnect, onMsg, onError, onClose, aTimeout, supportSelfSigned) : WebSocketClient__

````
Tries to establish a websocket connection (ws or wss) and returns a jetty WebSocketClient java object. As callbacks you should defined onConnect, onMsg, onError and onClose. The onConnect callback will  provide, as argument, the created session that you should use to send data; the onMsg callback will provide, as arguments, aType (either "text" or "bytes"), aPayload (string or array of bytes) and an offset and length (in case type is "bytes"); the onError callback will provide the cause; the onClose callback will provide aStatusCode and aReason. You can optionally provide aTimeout (number) and indicate if self signed SSL certificates should be accepted (supportSelfSigned = true). Example:

plugin("HTTP");
var session; var output = "";
var client = (new HTTP()).wsConnect("ws://echo.websocket.org",
  function(aSession) { log("Connected"); session = aSession; },
  function(aType, aPayload, aOffset, aLength) { if (aType == "text") output += aPayload; },
  function(aCause) { logErr(aCause); },
  function(aStatusCode, aReason) { log("Closed (" + aReason + ")"); }
);
session.getRemote().sendString("Hello World!");
while(output.length < 1) { sleep(100); };
client.stop();
print(output);

NOTE: this functionality is only available if used with JVM >= 1.8


````
