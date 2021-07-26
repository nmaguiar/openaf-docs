---
layout: default
title: jmx
parent: Reference
grand_parent: OpenAF docs
---


## jmx

### JMX.attach2Local

__JMX.attach2Local(aId) : Object__

````
Establishes a connection with a local Java process given the aId provided by JMX.getLocals() returning an URL to establish a JMX connection, a list of System environment variables and a Agent describing the Java Management Agent activated on the local Java process.
````
### JMX.getLocals

__JMX.getLocals() : Object__

````
Returns a Locals map with an id and name of each Java process detected locally. To be used with JMX.attach2Local().
````
### JMX.getObject

__JMX.getObject(aObjName) : Object__

````
Obtains a bean aObject (e.g. aObjName = "com.openaf:type=Values").
Example:

jmx.getObject("com.openaf:type=Values");


````
### JMX.JMX

__JMX.JMX(aURL, aLogin, aPassword, aProvider) : JMX__

````
Creates an instance to connect to aURL (e.g. service:jmx:rmi:///jndi/rmi://127.0.0.1:12345/jmxrmi). If needed aLogin and aPassword can be provided. aProvider can also be specified to access custom MX bean classes (e.g. WebLogic application servers).
Example:

var jmx = new JMX("service:jmx:rmi:///jndi/rmi://127.0.0.1:12345/jmxrmi");


````
