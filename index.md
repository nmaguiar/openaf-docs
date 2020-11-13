# OpenAF documentation<a href="/"><img align="right" src="/images/openaf_small.png"></a>

## Topics

* __[Concepts](_concepts/index.md)__ - understand some of the basic concepts
* __[How to](_howto/index.md)__ - core functionality exemplified.
* __[Guides](_guides/index.md)__ - guides with example code from beginner to advanced topics.

## Installing

### Unix (x86 based)

````bash
$ mkdir oaf
$ wget -O - https://openaf.io/unix64/install.sh | sh
$ ./oafc
````

### Mac OS

````bash
$ mkdir oaf
$ curl -o install.sh https://openaf.io/mac64/install.sh
$ sh install.sh
$ oafc
````

### Windows (64-bit)

````
C:\> mkdir oaf
C:\> cd oaf
C:\oaf> curl https://openaf.io/win64/install.bat -O
C:\oaf> install.bat
C:\oaf> oafc
````

### Docker

````bash
$ docker run --rm -ti openaf/openaf
/openaf # oafc
````

### Unix (ARM 64)

````bash
$ mkdir oaf
$ wget -O https://openaf.io/arm64/install.sh | sh
$ oafc
````

### Unix (ARM 32)

````bash
$ mkdir oaf
$ wget -O https://openaf.io/arm32/install.sh | sh
$ oafc
````

## Upgrade

After installing an update.sh (or update.bat in Windows) will be created. Simply execute it.

## Move to a different folder

After moving to the new folder execute the reinstall.sh (or reinstall.bat in Windows) created after the first installation.

## Uninstall

Simply delete the created folder.

There might be also ".openaf*" files created on your home folder.