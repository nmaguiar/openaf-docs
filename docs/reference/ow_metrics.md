---
layout: default
title: ow.metrics
parent: Reference
grand_parent: OpenAF docs
---


## ow.metrics

### ow.metrics.add

__ow.metrics.add(aName, aFunction)__

````
Adds aName metric whose values are a map returned by aFunction.
````
### ow.metrics.collectMetrics

__ow.metrics.collectMetrics(aName, aFunction) : Object__

````
Executes aFunction while collecting functions metrics under the name aName. Returns whatever the function returns or throws any exception.
````
### ow.metrics.collectMetrics4Fn

__ow.metrics.collectMetrics4Fn(aName, aFn)__

````
Adds extra code to an existing aFn to collect functions metrics under the name aName. If the same aName and aFn has been already executed before it will throw an exception "Already collecting for the provided function."
````
### ow.metrics.exists

__ow.metrics.exists(aName) : Boolean__

````
Determines if metric aName is currenly assigned.
````
### ow.metrics.fromObj2OpenMetrics

__ow.metrics.fromObj2OpenMetrics(aObj, aPrefix, aTimestamp, aHelpMap, aConvMap) : String__

````
Given aObj will return a string of open metric (prometheus) metric strings. Optionally you can provide a prefix (defaults to "metric")  and/or aTimestamp (a number in seconds or a label field, that will be used for all aObj values) and aConvMap composed of a key with a map of possible values and corresponding translation to numbers. Note: prefixes should not start with a digit.
````
### ow.metrics.fromOpenMetrics2Array

__ow.metrics.fromOpenMetrics2Array(aLines) : Array__

````
Given an array or string newline delimited string following the OpenMetrics format  will try to return an array with each metric, value, labels, timestamp and perceived prefix.
````
### ow.metrics.getAll

__ow.metrics.getAll() : Map__

````
Returns a map with all registered metrics.
````
### ow.metrics.getSome

__ow.metrics.getSome(anArrayOfNames) : Map__

````
Returns just the metrics in the provided anArrayOfNames.
````
### ow.metrics.startCollecting

__ow.metrics.startCollecting(aChName, aPeriod, some, noDate)__

````
Starts collecting metrics on aChName (defaults to '__metrics') every aPeriod ms (defaults to 1000ms) optionally just some (array) metrics.
````
### ow.metrics.stopCollecting

__ow.metrics.stopCollecting(aChName)__

````
Stops collecting metrics on aChName (defaults to '__metrics')
````
