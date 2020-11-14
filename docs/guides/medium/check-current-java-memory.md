---
layout: default
title: Check current OpenAF Java memory
parent: Medium
grand_parent: Guides
---

# Check current OpenAF Java memory

Keeping in mind that OpenAF runs on a JVM so you might want to keep an eye on the current heap size.

## Checking current memory size

You can do this easily with the included _ow.java_ library. Just load it:

````javascript
ow.loadJava();
````

And call _ow.java.getMemory_:

````javascript
> ow.java.getMemory()
+--------+------------+
|   max: | 2048917504 |
| total: | 46137344   |
|  used: | 12635344   |
|  free: | 33502000   |
+--------+------------+
````

If you want to convert it to the corresponding byte abbrevation just use the first boolean argument:

````javascript
> ow.java.getMemory(true)
+--------+---------+
|   max: | 1.91 GB |
| total: | 44.0 MB |
|  used: | 12.4 MB |
|  free: | 31.6 MB |
+--------+---------+
````

## Forcing the Java garbage collector

If you fill the heap size temporarially and, afterwards, no longer need the assigned memory Java will eventualy free up once it's corresponding Java garbabe collector runs:

````javascript
> var list = io.listFiles("c:/windows/system32");
> ow.java.getMemory(true)
+--------+---------+
|   max: | 1.91 GB |
| total: | 44.0 MB |
|  used: | 16.7 MB |
|  free: | 27.3 MB |
+--------+---------+
> ow.java.gc();
> ow.java.getMemory(true)
+--------+---------+
|   max: | 1.91 GB |
| total: | 44.0 MB |
|  used: | 12.1 MB |
|  free: | 31.9 MB |
+--------+---------+
````