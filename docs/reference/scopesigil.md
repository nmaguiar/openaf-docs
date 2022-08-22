---
layout: default
title: scopesigil
parent: Reference
grand_parent: OpenAF docs
---


## scopesigil

### $$.get

__$$.get(aPath) : Object__

````
Given aObject it will try to parse the aPath and retrive the corresponding object under that path. Example:

var a = { a : 1, b : { c: 2, d: [0, 1] } };

print($$(a).get("b.c")); // 2
sprint($$(a).get("b.d")); // [0, 1]
print($$(a).get("b.d[0]")); // 0


````
### $$.getI

__$$.getI(aPath) : Object__

````
Given aObject it will try to parse the aPath (in a case-insensitive way) and retrive the corresponding object under that path. Example:

var a = { a : 1, b : { c: 2, d: [0, 1] } };

print($$(a).getI("b.C")); // 2
sprint($$(a).getI("B.d")); // [0, 1]
print($$(a).getI("B.D[0]")); // 0


````
### $$.set

__$$.set(aPath, aNewValue) : Object__

````
Given aObject it will try to parse the aPath a set the corresponding object under that path to aNewValue. Example:

var a = { a : 1, b : { c: 2, d: [0, 1] } };

sprint($$(a).set("b.c", 123); // { a : 1, b : { c: 123, d: [0, 1] } }


````
### _$

___$(aObject, anErrorMessagePrefix)__

````
Shortcut to facilitate argument pre-validation and promote defensive programming.

.default(aNewObject) : aObject
Checks if aObject is defined and returns aObject. If it's not defined it will return aNewObject (the default value).

$_(aMessage) : aObject
Throws an exception with aMessage if aObject is not defined otherwise returns aObject.
````
