---
layout: default
title: Timing executions on OpenAF console
parent: Medium
grand_parent: Guides
---

# Timing executions on OpenAF console

When profilling your script or functions you created it's usually helpfull to quickly understand how many ms or seconds it took to execute. Using the OpenAF console you can use the "time" command to provide you the execution time of every console line executed:

````javascript
> time
-- Timing of commands is enabled.
> sleep(500)
-- Elapsed time: 0.51s
````

## Analysing results

Consider the following example:

````javascript
> var o = io.listFiles("/usr/bin")
-- Elapsed time: 0.045s
> var o = io.listFiles("/usr/bin")
-- Elapsed time: 0.028s
> var o = io.listFiles("/usr/bin")
-- Elapsed time: 0.024s
````

"Why the first test was slower than the other two tests?" Whenever analysing execution time you need to consider several factors among them:

  * OpenAF uses the [Rhino javascript engine](https://github.com/mozilla/rhino) that, by default in OpenAF, will interpret the javascript code and then compile it "on-the-fly" to java bytecode. Subsequent calls will then use the compiled code.
  * The are always several levels of caching. In this case the operating system might cache the results of listing details about a folder so subsequent calls will be faster.
  * It's Java underneath so the Java Gargabe Collector might influence results.
  * The current machine load can also influence the execution time.

## Adivces

The generic advices, given the factors that might influence execution, are:

  * Always time execution more than one time. Exit and reopen the openaf-console, if needed, to understand the time it takes to "heat up".
  * Keep an eye on the current machine load. Make sure you only make comparitions with similar general loads.
  * Make sure there is enough memory for the openaf-console Java process and the execution you are profiling.

If you want to keep an eye on the memory you can also execute the "one-line":

````javascript
> ow.loadFormat();
> watch var rm = java.lang.Runtime.getRuntime(); templify("{{free}}/{{total}} ({{max}})", { free: ow.format.toBytesAbbreviation(rm.freeMemory()), total: ow.format.toBytesAbbreviation(rm.totalMemory()), max: ow.format.toBytesAbbreviation(rm.maxMemory()) })
````

Executing now the same calls you can now see the memory evolution ("free/total (max)"):

````javascript
> var o = io.listFiles("/usr/bin")
-- Elapsed time: 0.033s
[ "48.2 MB/59.5 MB (879 MB)" ]
> var o = io.listFiles("/usr/bin")
-- Elapsed time: 0.024s
[ "45.2 MB/59.5 MB (879 MB)" ]
> var o = io.listFiles("/usr/bin")
-- Elapsed time: 0.022s
[ "42.1 MB/59.5 MB (879 MB)" ]
````

## How to turn it off

To turn off the timming of command executions and the memory evolution watch command just execute:

````javascript
> time
-- Timing of commands is disabled.
> watch off
>
````

You can also add time specific points in an existing script using functions like now(). For even more functionality the ow.test library provides more tools for reporting 