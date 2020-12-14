---
layout: default
title: oJob
parent: Concepts
grand_parent: OpenAF docs
---

# OpenAF

OpenAF (pronounced _open-A-F_) is a basic command-line Java-based application that started as an open "application framework" in order to solve different automation challenges with minimal requirements and footprint.

On it's core is basically a Javascript interpreter (based on [Mozilla's Rhino](https://github.com/mozilla/rhino)) with lots of included functions, javascript libraries (called OpenWrap or "ow" for short) and java libraries. 

Since it's possible to mix Java and Javascript languages it can use all the extensive Java libraries available and also the majority of Javascript browser-based libraries making it possible to mix a lot of different functionality without big modules and dependencies or specific platform recompiling needs that other languages and tools require. Nevertheless it also allows to mix Python, shell script, PowerShell, PHP, etc... functionality easily and when needed.

OpenAF's evolution is basically driven by the problems it's applied to try to solve while trying to keep, as much as possible, legacy support. When legacy support has to be broken versions will keep for one or two years old functionality deprecation. This goes from function signature upon to functionality alternatives.

OpenAF is also built to be "contained" on the folder where it's installed so it can adapt to different types of deployments with different types of requirements.

## Versions

The version numbering has been based on the build day, month and year (e.g. 20191231) for now.

## Distributions 

There are "stable" and "nightly" distribution builds where a "stable" is a build that has been tested under "nightly" for quite some time. "Stable" versions are usually launched with one to some months apart. "Nightly" versions are built every day and intended to test new functionality.

There are other distributions used also in continuous development (CD) but not recommended for every-day usage.

## Extending

To extend functionality there is an include "package manager" called _oPack_ (OpenPack) meant to be independent and solely based on OpenAF.

When an oPack is installed it will be placed under a sub-folder of the OpenAF installation being used. It can include both Javascript and Java functionality.

There are public and private oPack repositories and the "packages" themselves are basically _zip_ files meant to be easy to be deployed on environments where you might to be able to access any public or private repository.

In order to keep a small footprint on the main installation it's not unusual that functionality not often used gets moved into oPacks over-time while keeping the same scripting interface.

## oJob

Out of the experience of writing thousands of OpenAF scripts an "orchestrator" was born to coordinate and easily reuse pieces of scripting code. 

It basically allows for one or multiple YAML or JSON data files to define how different pieces of code (either javascript, python, shell script, powershell (in Windows), php, etc...) can interact to reach an end goal using one or multiple executing instances.

It also aims to make it easy to reuse code in a standard format and to move it easily to where you need it.

Right after installing OpenAF you can use oJob.io (using the public or a private repository) to quickly execute and reuse "oJob"s to achieve different goals making it an ideal "DevOps" tool (e.g. building a quick pipeline, building quick micro-services, etc...).