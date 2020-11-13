---
layout: default
title: "Beginner: Introduction to streams in OpenAF"
parent: Guides
grand_parent: OpenAF docs
---

# Introduction to streams in OpenAF

Some of the functions you find in OpenAF have the "stream version" and the "non stream version". For example: io.readFileBytes and io.readFileStream; io.writeFileBytes and io.writeFileStream; HTTP.getBytes and HTTP.getStream; etc.

So what's the difference? 

Roughly the non stream version will get the relevant contents to memory from another source or write them from memory to another source. It's fast but the bigger the contents, the bigger memory you will need.

The stream version provides an object that let's other functions retrieve small sub-sets of the content (from another source or memory) while handling that content.

For example, reading a file:

````javascript
var contents = io.readFileBytes("myFile.bin");

// vs

var istream = io.readFileStream("myFile.bin");
````

The variable _contents_ will hold all the bytes on the _myFile.bin_ file while the variable _istream_ will be an object allowing other functions to read parts of _myFile.bin_.

## Input and output streams

These OpenAF streams are actually nothing more than the Java's InputStream and OutputStream objects. _Input_ for streams that let you read content from another source and _Output_ for streams that let you write content to some other source.

In the file example you have an input stream: _istream_. So how can you now, for example, write the contents you get from the input stream to another file?

````javascript
var istream = io.readFileStream("myFile.bin");
var ostream = io.writeFileStream("myNewFile.bin");

ioStreamCopy(ostream, istream);
````

Usually these stream objects need to be closed once used by calling the method _.close()_. But this OpenAF's _ioStreamCopy_ does everything for you.

There are more methods like _ioStreamRead_, _ioStreamReadLines_, _ioStreamReadBytes_, _ioStreamWrite_, _ioStreamWriteBytes_, etc...

## Handling input streams

Let's assume that you are reading a huge csv file and you want to process each line:

````javascript
var istream = io.readFileStream("mycsv.csv");
ioStreamReadLines(istream, (line) => {
    // Handle the line

    return result;
});
istream.close();
````

In this example the function _ioStreamReadLines_ will read contents from the _istream_ input stream until it finds the defined separator, new line ('\n') by default in this case. Then it calls the callback function with one argument: the entire line. When it ends the _istream_ is closed since it's no longer needed.

What about the returned _result_? One of the benefits is that you don't have to read to the end of the stream/file. You can stop at any time. If _'result = true'_ the function _ioStreamReadLines_ will stop reading from the input stream and return.

_Note: there is an argument on the ioStreamReadLines function to provide a different separator than '\n'. Check "help ioStreamReadLines" on an openaf-console._