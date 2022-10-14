---
layout: default
title: Quickly download portable JDKs/JREs
parent: oJobIO
grand_parent: Guides
---

# Quickly download portable JVMs/JREs

For different reasons you might need to quickly download the latest specific Java JDK and/or JRE in a way that is portable with little dependencies. For that you can use the following ojob:

````bash
$ ojob ojob.io/java/download
````

Without any parameters it will try to download a linux, x64, version 8, Java JRE:

````
INFO | Download parameters: arch=x64 os=linux version=8 type=jre jvm=hotspot heap=normal
INFO | Downloading to jre.tgz (39.4 MB)...
INFO | Repacking jre.tgz...
INFO | Package jre.tgz (39.7 MB) ready.
````

The generated "jre.tgz" is ready to be expand in any modern linux and provides a ready-to-use JRE:

````bash
$ tar xzf jre.tgz
$ jre/bin/java -version
openjdk version "1.8.0_345"
OpenJDK Runtime Environment (Temurin)(build 1.8.0_345-b01)
OpenJDK 64-Bit Server VM (Temurin)(build 25.345-b01, mixed mode)
````

## Download a JDK instead of a JRE

To download the full JDK just add the _type=jdk_ to the parameters:

````bash
$ ojob ojob.io/java/download type=jdk
INFO | Download parameters: arch=x64 os=linux version=8 type=jdk jvm=hotspot heap=normal
INFO | Downloading to jdk.tgz (98.2 MB)...
INFO | Repacking jdk.tgz...
INFO | Package jdk.tgz (98.4 MB) ready.
````

## Download a different version, a different architecture and/or a different operating system

Let's say you are on a Mac with Apple Silicon and you need a JDK with version 19:

````bash
$ ojob ojob.io/java/download type=jdk arch=aarch64 os=mac version=19
````

## Listing available options

But which architecture, operating system, etc... can you choose from? For that you just need to run _list=true_ for the intended major version:

````bash
$ ojob ojob.io/java/download version=19 list=true
 arch  │     os     │ heap │   type   │  jvm  │version│ release 
───────┼────────────┼──────┼──────────┼───────┼───────┼─────────
aarch64│linux       │normal│debugimage│hotspot│19     │jdk-19+36
aarch64│linux       │normal│jdk       │hotspot│19     │jdk-19+36
aarch64│linux       │normal│jre       │hotspot│19     │jdk-19+36
aarch64│linux       │normal│sbom      │hotspot│19     │jdk-19+36
aarch64│linux       │normal│staticlibs│hotspot│19     │jdk-19+36
aarch64│mac         │normal│debugimage│hotspot│19     │jdk-19+36
aarch64│mac         │normal│jdk       │hotspot│19     │jdk-19+36
aarch64│mac         │normal│jre       │hotspot│19     │jdk-19+36
aarch64│mac         │normal│sbom      │hotspot│19     │jdk-19+36
aarch64│mac         │normal│staticlibs│hotspot│19     │jdk-19+36
arm    │linux       │normal│debugimage│hotspot│19     │jdk-19+36
arm    │linux       │normal│jdk       │hotspot│19     │jdk-19+36
arm    │linux       │normal│jre       │hotspot│19     │jdk-19+36
arm    │linux       │normal│sbom      │hotspot│19     │jdk-19+36
arm    │linux       │normal│staticlibs│hotspot│19     │jdk-19+36
ppc64le│linux       │normal│debugimage│hotspot│19     │jdk-19+36
ppc64le│linux       │normal│jdk       │hotspot│19     │jdk-19+36
ppc64le│linux       │normal│jre       │hotspot│19     │jdk-19+36
ppc64le│linux       │normal│sbom      │hotspot│19     │jdk-19+36
ppc64le│linux       │normal│staticlibs│hotspot│19     │jdk-19+36
s390x  │linux       │normal│debugimage│hotspot│19     │jdk-19+36
s390x  │linux       │normal│jdk       │hotspot│19     │jdk-19+36
s390x  │linux       │normal│jre       │hotspot│19     │jdk-19+36
s390x  │linux       │normal│sbom      │hotspot│19     │jdk-19+36
s390x  │linux       │normal│staticlibs│hotspot│19     │jdk-19+36
x32    │windows     │normal│debugimage│hotspot│19     │jdk-19+36
x32    │windows     │normal│jdk       │hotspot│19     │jdk-19+36
x32    │windows     │normal│jre       │hotspot│19     │jdk-19+36
x32    │windows     │normal│sbom      │hotspot│19     │jdk-19+36
x32    │windows     │normal│staticlibs│hotspot│19     │jdk-19+36
x64    │alpine-linux│normal│debugimage│hotspot│19     │jdk-19+36
x64    │alpine-linux│normal│jdk       │hotspot│19     │jdk-19+36
x64    │alpine-linux│normal│jre       │hotspot│19     │jdk-19+36
x64    │alpine-linux│normal│sbom      │hotspot│19     │jdk-19+36
x64    │alpine-linux│normal│staticlibs│hotspot│19     │jdk-19+36
x64    │linux       │normal│debugimage│hotspot│19     │jdk-19+36
x64    │linux       │normal│jdk       │hotspot│19     │jdk-19+36
x64    │linux       │normal│jre       │hotspot│19     │jdk-19+36
x64    │linux       │normal│sbom      │hotspot│19     │jdk-19+36
x64    │linux       │normal│sources   │hotspot│19     │jdk-19+36
x64    │linux       │normal│staticlibs│hotspot│19     │jdk-19+36
x64    │mac         │normal│debugimage│hotspot│19     │jdk-19+36
x64    │mac         │normal│jdk       │hotspot│19     │jdk-19+36
x64    │mac         │normal│jre       │hotspot│19     │jdk-19+36
x64    │mac         │normal│sbom      │hotspot│19     │jdk-19+36
x64    │mac         │normal│staticlibs│hotspot│19     │jdk-19+36
x64    │windows     │normal│debugimage│hotspot│19     │jdk-19+36
x64    │windows     │normal│jdk       │hotspot│19     │jdk-19+36
x64    │windows     │normal│jre       │hotspot│19     │jdk-19+36
x64    │windows     │normal│sbom      │hotspot│19     │jdk-19+36
x64    │windows     │normal│staticlibs│hotspot│19     │jdk-19+36
````