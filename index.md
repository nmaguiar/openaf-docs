---
layout: default
title: OpenAF docs
has_children: true
---

# OpenAF documentation

OpenAF (_pronounced open-a-f_) is a Java & Javascript based "swiss-army knife" scripting DevOps tool for different automation challenges with minimal requirements and footprint, extensible through packages ([oPacks](docs/concepts/oPack.md)) and with easy code orchestration ([oJob](docs/concepts/oJob.md) and [oJob.io](docs/concepts/oJobIO.md)).
## Topics

* __[Concepts](docs/concepts/index.md)__ - understand some of the basic concepts
* __[How to](docs/howto/index.md)__ - core functionality exemplified.
* __[Guides](docs/guides/index.md)__ - guides with example code from beginner to advanced topics.

## Installing

### Unix (x86 based)

````bash
$ mkdir oaf && cd oaf
$ wget -O - https://openaf.io/unix64/install.sh | sh
$ ./oafc
````

### Windows (64-bit)

````
C:\> mkdir oaf
C:\> cd oaf
C:\oaf> curl https://openaf.io/win64/install.bat -O
C:\oaf> install.bat
C:\oaf> oafc
````

### Mac OS (Intel based)

````bash
$ mkdir oaf && cd oaf
$ curl -o install.sh https://openaf.io/mac64/install.sh
$ sh install.sh
$ ./oafc
````

### Mac OS (Apple silicon based)

````bash
$ mkdir oaf && cd oaf
$ curl -o install.sh https://openaf.io/macarm/install.sh | sh
$ ./oafc
````

### Docker

````bash
$ docker run --rm -ti openaf/openaf
/openaf # oafc
````

### Unix (ARM 64)

````bash
$ mkdir oaf && cd oaf
$ wget -O - https://openaf.io/arm64/install.sh | sh
$ oafc
````

### Unix (ARM 32)

````bash
$ mkdir oaf && cd oaf
$ wget -O - https://openaf.io/arm32/install.sh | sh
$ oafc
````

## Upgrade

After installing an update.sh (or update.bat in Windows) will be created. Simply execute it.

## Move to a different folder

After moving to the new folder execute the reinstall.sh (or reinstall.bat in Windows) created after the first installation.

## Uninstall

Simply delete the created folder.

There might be also ".openaf*" files created on your home folder.

## Unix generic install/uninstall

### Install (with Java)

````bash
$ wget -O - https://openaf.io/install.sh | sh
````

### Install (without Java)

````bash
$ wget -O - https://openaf.io/download.sh | sh
````

### Uninstall

````bash
$ sudo ojob ojob.io/oaf/symlinks UNINSTALL=true && sudo rm -rf /opt/oaf
````

### Nightly build

If you want to install the nightly build follow these [instructions](installing-nightly).

### Older versions

To install older versions please follow these [instructions](docs/howto/Download-older-versions).
You can also check the [GitHub releases list](https://github.com/OpenAF/openaf/releases)