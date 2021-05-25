---
layout: default
title: Javascript to OpenAF
parent: Concepts
grand_parent: OpenAF docs
---

# Javascript to OpenAF

This article provides a description of the additions (e.g. functions, variables, libraries, etc...) to the standard JavaScript included with OpenAF.

## Basics

Starting with basics, OpenAF runs on Java interpreting/compiling javascript using [Mozilla Rhino](https://github.com/mozilla/rhino). Not the version that was included on the JVM a long time ago but current stable version on GitHub. That means it supports [ES5](https://www.w3schools.com/js/js_es5.asp) with some features of [ES6](https://www.w3schools.com/js/js_es6.asp) (see a [compatibility map from Mozilla Rhino](http://mozilla.github.io/rhino/compat/engines.html)).

You can always check documentation here or, using the openaf-console (oafc), executing the "help" command for more details:

````
> help [partial of full word match]
````

_tbc_

## Basic

| Function | Description |
|----------|-------------|
| compare | Compares two javascript objects (with deep map search). |
| clone | Clones the provided javascript object to a new instance. | 
| merge | Merges two javascript maps and/or arrays into a new object. |
| inherit | Given an parent and a child object it will copy the parent javascript prototype to the child prototype. |
| load | Given an OpenAF javascript file it will interpret and compile the corresponding code. Will search the current installed oPack paths if not found on the current path. |
| loadLib | Sames as _load_ but keeping track of previously loaded OpenAF javascript files to avoid re-execution. |
| plugin | Loads a Java-based OpenAF plugin that must be on the classpath. If found on current installed oPack paths it will try to dynamically added to the classpath (when using the custom class loader). | 
| require | Loads an OpenAF javascript with declared exports returning a map with the same. |
| exit | Immediatelly exits the current execution with the provided exit code. |
| arrayContains | Tries to determine if an array contains an object. |
| uniqArray | Returns an array with no duplicated entries (with deep map search). |
| splitArray | Returns the best effort of diving the provided array into a specific number of equal parts. |

## Checking types

_tbc_
## Printing

_tbc_
## Logging 

_tbc_

## Navigating arrays and maps

There are a set of libraries includes to help to "navigate" through javascript arrays and maps:

| Function | Description | 
|----------|-------------|
| $from | See more in [$from](OpenAF-nLinq.md) |
| $path | Uses the [JMESPath library](http://jmespath.org) |
| $stream | Uses the old [streamjs library](https://github.com/winterbe/streamjs/blob/master/APIDOC.md) |

## Utility

_tbc_

## Parallel execution

_tbc_

## OPack specific

_tbc_

## OpenAF help functionality

_tbc_
## OpenAF runtime specific

### Global variables

| Variable | Type | Description |
|----------|------|-------------|
| global   | | Represents all the global variables (e.g. _this_ on the main context). |
| noHomeComms | Boolean | When set to _true_ the OpenAF runtime will avoid any call to "openaf.io" (to get help indexes, latest version, etc...) |
| __separator | String | The operating-system dependent line separator (e.g. '\n' or '\r\n') |

_tbc_

### Functions

| Function | Description |
|----------|-------------|
| getOpenAFJar | Returns the complete filepath and name for the OpenAF jar file. |
| processExpr | Processes command-line argument data provided with the option _-e_ |
| getVersion | Returns the current OpenAF runtime version. |
| getDistribution | Returns the current OpenAF runtime distribution name. |
| getOpenAFPath | Returns the filepath to where OpenAF seems to be installed. |
| loadExternalJars | If using OpenAF's custom class loader it will dynamicall load external classes from JARs on the filpath provided. |
| loadCompiled | Loads a pre-compiled OpenAF javascript library (if not pre-compiled it will attempt to compile it). |
| loadLibCompiled | Same as _loadCompiled_ but ensuring that the pre-compiled OpenAF javascript library code is only executed once. |
| requireCompiled | Returns an object with all the javascript exports on a javascript pre-compiled library. |
| restartOpenAF | Terminates the current OpenAF execution and tries to restart the java process again. |
| forkOpenAF | Starts another OpenAF process with the same command-line. |
| stopOpenAFAndRun | Terminates the current OpenAF execution in parallel with starting the execution of a new command-line provided. |
| addOnOpenAFShutdown | Adds a function to be executed upon OpenAF execution end. |
| getNumberOfCores | Returns the current reported number of cores. |
| getCPULoad | Returns the current reports CPU load from the Java instrumentation API. |
| getPid | Returns the current process OS identifier. |
| pidCheck | Verifies if the provided pid is currently running or not. |
| pidCheckIn | Provides check-in pid functionality over a .pid file to ensure that only one OpenAF execution is invoked. |
| pidKill | Tries to terminate a OS process by pid. |
| pidCheckOut | Provided check-out pid functionality over a .pid file to ensure that only one OpenAF execution is invoked. |
_tbc_

## Python integration

_tbc_

## oWrap and other included libraries

The following is a list of the OpenAF and external libraries included. Most of the libraries are automatically loaded by OpenAF when required but _ow.load*_ and _load*_ functions can be used to ensure they are loaded. These load functions can be used repeatedly as OpenAF ensures that they are only loaded on the first call. 

Most of the none basic OpenAF functionality is kept in included "ow" (OpenWrap) _wrapper_ libraries:

| Library | Description | To load |
|---------|-------------|---------|
| Format | One of the main libraries with all formatting functionality (might include some old format unrelated functions) | ````ow.loadFormat();```` |
| Obj | One of the main libraries with object manipulation functionality | ````ow.loadObj();```` |
| Server | One of the main libraries with server related functionality when OpenAF code is run as a daemon | ````ow.loadServer();```` |
| Ch | One of the main libraries with [OpenAF channel](OpenAF-Channels.md) functionality | ````ow.loadCh();```` |
| Template | One of the main libraries providing templating functionality (HandleBards based) | ````ow.loadTemplate();```` | 
| Sec | Includes all the [OpenAF 'secure buckets'](sBuckets.md) functionality | ````ow.loadSec();```` |
| Net | Includes network related functionality | ````ow.loadNet();```` |
| Metrics | Includes self monitoring and telemetry functionality | ````ow.loadMetrics();```` |
| Test | Includes unitary test helper functionality | ````ow.loadTest();```` | 
| Java | Java integration functionality | ````ow.loadJava();```` |
| Python | Python integration functionality | ````ow.loadPython();```` |
| AI | Includes some basic AI functionality | ````ow.loadAI();```` |
| Dev | Includes functionality that it's still being tested. | ````ow.loadDev();```` |

External javascript based libraries are also included:

| Library | To load | 
|---------|---------|
| Underscore (Lodash) | ````loadUnderscore()```` |
| FuseJS | ````loadFuse()```` |
| JsDiff | ````loadDiff()```` |
| Ajv | ````loadAjv()```` |
| Lodash (Underscore) | ````loadLodash()```` |
| OpenAF oDoc (help functionality) | ````loadHelp()```` |
## Java support

To check on how to interact between Javascript and Java in OpenAF (including some OpenAF helper functions built-in) see [Java support](/docs/concepts/java.md)