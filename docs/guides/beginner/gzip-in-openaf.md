---
layout: default
title: gzip/gunzip functionality in OpenAF
parent: Beginner
grand_parent: Guides
---

# gzip/gunzip functionality in OpenAF

There are built-in functionality, in OpenAF, to apply gzip or gunzip to files or arrays of bytes. The functionality is available on the object io with the functions: _io.gzip_, _io.gunzip_, _io.readFileGzipStream_ and _io.writeFileGzipStream_. They divide into two ways of using it:

## To/From an array of bytes

The simplest way is to gzip/gunzip to/from an array of bytes:

````javascript
var theLog = io.gunzip(io.readFileBytes("abc.log.gz"));
var gzLog  = io.writeFileBytes("new.log.gz", io.gzip(theLog));
````

The only issue is that the array of bytes (e.g. theLog, gzLog) will be kept in memory. 

## To/From streams

To address larger sets of bytes without occuring into memory spending, specially for large files, the are the stream based functions:

````javascript
var rstream = io.readFileGzipStream("abc.log.gz");
// use the rstream and change it's content
// when ready to write just create a write stream
var wstream = io.writeFileGzipStream("new.log.gz");
// and use it to write to the new gzip file
````

## Compress/Uncompress

To help store big javascript objects (even in memory) OpenAF provides two functions: _compress_ and _uncompress_.

Of course the gains will be greater the bigger, and more compressable, the object is. Let's see some examples:

````javascript
> var out = compress(io.listFiles("."));
> out.length
1959
> stringify(io.listFiles("."), void 0, 22).length
11674
> stringify(uncompress(out), void 0, "").length
11674
````

Of course objects are not stored in memory as their stringify version but, you get the idea. It's specific for cases when you need to keep an object in memory that you won't be acesssing on the medium/long term of the execution of your OpenAF script. Of course, it's also easy to save/load from a binary file:

````javascript
> io.writeFileBytes("myObj.gz", compress(io.listFiles(".")));
> var theLog = uncompress(io.readFileBytes("myObj.gz"));
````