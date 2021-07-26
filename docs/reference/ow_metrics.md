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
### ow.metrics.fromObj2OpenMetrics

__ow.metrics.fromObj2OpenMetrics(aObj, aPrefix, aTimestamp, aHelpMap) : String__

````
Given aObj will return a string of open metric (prometheus) metric strings. Optionally you can provide a prefix (defaults to "metric")  and/or aTimestamp (that will be used for all aObj values).
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

__ow.metrics.startCollecting(aChName, aPeriod, some)__

````
Starts collecting metrics on aChName (defaults to '__metrics') every aPeriod ms (defaults to 1000ms) optionally just some (array) metrics.
````
### ow.metrics.stopCollecting

__ow.metrics.stopCollecting(aChName)__

````
Stops collecting metrics on aChName (defaults to '__metrics')
````
