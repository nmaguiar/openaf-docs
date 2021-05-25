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

_tbc_

## Java support

To check on how to interact between Javascript and Java in OpenAF (including some OpenAF helper functions built-in) see [Java support](/docs/concepts/java.md)