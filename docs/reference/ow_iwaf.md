---
layout: default
title: ow.iwaf
parent: Reference
grand_parent: OpenAF docs
---


## ow.iwaf

### i$.exec

__i$.exec(aOperation, aMapIn, aThread) : Map__

````
Executes the AF aOperation on the current instance (with the current permissions) using aMapIn. Returns the aOperation map result.
````
### i$.exec2Raw

__i$.exec2Raw(aOperation, aMapIn) : JavaParameterMap__

````
Executes the AF aOperation on the current instance (with the current permissions) using aMapIn. Returns the aOperation map result as a Java ParameterMap object.
````
### i$.getExecutionMap

__i$.getExecutionMap(aThis) : Map__

````
Returns the current flow execution map given aThis (this).
````
### i$.getService

__i$.getService(aThis, aServiceName) : JavaObject__

````
Given aThis (this) returns a java objet for the RAID aServiceName.
````
### i$.internalAF 

__i$.internalAF : AF__

````
Provides a "fake" af object to be used with ow.waf to mimic the same functionality but using the internal AF connection to RAID.
````
### i$.log

__i$.log(aMessage)__

````
Logs aMessage, as a warning, in the instance log .
````
### i$.logWarn

__i$.logWarn(aMessage)__

````
Logs aMessage, as a warning, in the instance log .
````
### i$.setAlternativeHTTP

__i$.setAlternativeHTTP(useNew)__

````
For older versions of RAID that can't use newer OpenAF HTTP libraries execute this function with useNew = false to revert ow.obj.rest.* functionality to Java's HTTP API. Using useNew = true will revert to using ow.obj.http.
````
### i$.setExecutionMap

__i$.setExecutionMap(aThis, aMap)__

````
Sets aMap as the flow execution map given aThis (this).
````
### i$.slog

__i$.slog(aObject)__

````
Logs a stringify representation of aObject in the instance log.
````
### i$.slogErr

__i$.slogErr(aObject)__

````
Logs a stringify representation of aObject, as an error, in the instance log.
````
### i$.slogWarn

__i$.slogWarn(aObject)__

````
Logs a stringify representation of aObject, as a warning, in the instance log.
````
