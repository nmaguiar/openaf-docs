---
layout: default
title: ow.python
parent: Reference
grand_parent: OpenAF docs
---


## ow.python

### ow.python.exec

__ow.python.exec(aPythonCode, aInput, aOutputArray, shouldFork) : Map__

````
Tries to execute aPythonCode with the current interpreter providing the aInput map keys as python variables. It tries to return the values of the aOutputArray name variables. Example:

   var res = ow.python.exec("c = a + b", { a: 2, b: 1 }, [ "c" ]);
   print(res.c); // 3


````
### ow.python.execPM

__ow.python.execPM(aPythonCode, aInput) : Map__

````
Tries to execute aPythonCode with the current interpreter providing the aInput map as a python variable __pm. Any changes to this python variable will be returned.
````
### ow.python.getVersion

__ow.python.getVersion() : String__

````
The majoy python version detected.
````
### ow.python.setPython

__ow.python.setPython(aPythonPath)__

````
Sets the aPythonPath to the python interpreter process to use.
````
