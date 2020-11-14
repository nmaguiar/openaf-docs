---
layout: default
title: How to access remote JMX data
parent: Medium
grand_parent: Guides
---

# How to access remote JMX data

JMX, the Java Management Extensions, allows you to monitor/manage any Java based process. Since OpenAF is also a Java process it can be used as a "client" to check other java processes (including other OpenAF processes).

To set it up you will need to enable remote JMX access on the target Java process. Typically:

````bash
java -D"com.sun.management.jmxremote.port=9999" -D"com.sun.management.jmxremote.authenticate=false" -D"com.sun.management.jmxremote.ssl=false" -jar myApp.jar
````

_Note: is not recommended to disable authentication and SSL if you weren't on a controlled environment._

Now, in OpenAF, you can check remotely some JMX beans like the java.lang.Runtime and java.lang.Memory.

Let's start by creating a JMX object instance:

````javascript
> plugin("JMX");
> var jmx = new JMX("service:jmx:rmi:///jndi/rmi://127.0.0.1:9999/jmxrmi");
````

_Note: It's also possible to attach directly to running JVMs on the same host without having to change their startup arguments using JMX.attach2Local._

## Checking existing attributes

Let's check the available attributes for java.lang.Memory:

````javascript
> var obj = jmx.getObject("java.lang:type=Runtime");
> af.fromJavaMap(obj.getAttributes());
+-------------+------+----------------+------------------+------------------+
| attributes: |  [0] |      openType: |       className: | java.lang.String |
|             |      |                |     description: | java.lang.String |
|             |      |                |        typeName: | java.lang.String |
+-------------+------+----------------+------------------+------------------+
|             |      | attributeType: | java.lang.String |                  |
|             |      |       isWrite: | false            |                  |
|             |      |        isRead: | true             |                  |
|             |      |            is: | false            |                  |
|             |      |          name: | Name             |                  |
|             |      |   description: | Name             |                  |
+-------------+------+----------------+------------------+------------------+
|             |  [1] |      openType: |       className: | java.lang.String |
|             |      |                |     description: | java.lang.String |
|             |      |                |        typeName: | java.lang.String |
+-------------+------+----------------+------------------+------------------+
|             |      | attributeType: | java.lang.String |                  |
|             |      |       isWrite: | false            |                  |
|             |      |        isRead: | true             |                  |
|             |      |            is: | false            |                  |
|             |      |          name: | ClassPath        |                  |
|             |      |   description: | ClassPath        |                  |
+-------------+------+----------------+------------------+------------------+
...
````

## Retrieving string values

So we now know there are several attributes and their corresponding type: "Name", "ClassPath", etc&#46;&#46;&#46; To retrieve the current value of each just execute:

````javascript
> String(obj.get("Name"))
"12345@openaf"
> String(obj.get("ClassPath"))
"/openaf/openaf.jar"
````

## Retrieving composite values

But not all attributes have simple type values like String. If you check java.lang.Memory you will find that the specific values are wrapped on a Java class:

````javascript
> var obj = jmx.getObject("java.lang:type=Memory");
> af.fromJavaMap(obj.getAttributes()).attributes[1].name
"HeapMemoryUsage"
> af.fromJavaMap(obj.getAttributes()).attributes[1].attributeType
"javax.management.openmbean.CompositeData"
> af.fromJavaMap(obj.getAttributes()).attributes[1].openType.typeName
"java.lang.management.MemoryUsage"
````

To retrieve composite values just get the first composite value and use the corresponding class methods to retrieve "sub-values":

````javascript
> Number(o.get("HeapMemoryUsage").get("max"))
1821376512
> Number(o.get("HeapMemoryUsage").get("init"))
130023424
> Number(o.get("HeapMemoryUsage").get("used"))
13376936
> Number(o.get("HeapMemoryUsage").get("committed"))
124780544
````

_Note: The class and type should be available on the OpenAF's classpath if not standard._