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

### Docker

````bash
docker run --pull always --rm -ti openaf/oaf
# ./oafc
````

### Linux

````bash
# With sudo
curl https://openaf.io/install.sh | sh
# oafc

# Without sudo
curl https://openaf.io/setup.sh | sh && cd oaf
# ./oafc
````

> If you don't have _sudo_, _curl_ or _wget_ but you do have bash [follow these instructions](docs/howto/Download-without-curl-or-wget.md).

### Mac OS

````bash
curl -o setup.sh https://openaf.io/setup.sh && sh setup.sh && rm setup.sh && mv oaf /Applications/OpenAF && sudo sh -c "echo "/Applications/OpenAF" > /etc/paths.d/OpenAF"
# oafc
````

### Windows

````
C:\> mkdir oaf
C:\> cd oaf
C:\oaf> curl https://openaf.io/install.bat -o install.bat
C:\oaf> install.bat
C:\oaf> oafc
````

For specific platforms:

* [Unix (x86)](#unix-x86-based)
* [Unix (ARM 64)](#unix-arm-64)
* [Unix (ARM 32)](#unix-arm-32)
* [Windows (64-bit)](#windows-64-bit)
* [Mac OS (Intel)](#mac-os-intel-based)
* [Mac OS (Apple silicon)](#mac-os-apple-silicon-based)
* [Docker](#docker)

## Move to a different folder

If you used "install.sh": After moving to the new folder execute the reinstall.sh (or reinstall.bat in Windows) created after the first installation.

If you used "setup.sh": Simple move the folder.

## Upgrade

After installing an update.sh (or update.bat in Windows) will be created. Simply execute it.

## Uninstall

### Linux

````bash
sudo ojob ojob.io/oaf/symlinks UNINSTALL=true && sudo rm -rf /opt/oaf
````

### Mac OS

````
rm -rf /Applications/OpenAF && sudo rm /etc/paths/OpenAF && rm ~/.openaf*
````

### Windows

Simply delete the created folder ([current folder]/oaf or c:\\oaf)

There might be also ".openaf*" files created on your home folder (c:\\users\\[your user]\\.openaf*)

## Specific installs

Follow the link for [specific architectures installations](installing.md).

### Nightly build

If you want to install the nightly build follow these [instructions](installing-nightly).

### Older versions

To install older versions please follow these [instructions](docs/howto/Download-older-versions).
You can also check the [GitHub releases list](https://github.com/OpenAF/openaf/releases)