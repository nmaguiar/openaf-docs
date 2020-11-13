# Quick OpenAF streams conversion

When using input or output streams in OpenAF you might want to quickly "convert them" to string or array of bytes and vice-versa. Usually for testing proposes but you can find the following functions handy any time.

## Converting from String/Bytes to an Input Stream

If you need to get a string or an array of bytes into an input stream you can use _af.fromBytes2InputStream_ or _af.fromString2InputStream_. Here is an example:

````javascript
ioStreamReadLines(af.fromString2InputStream("Hello World!!\n"), (line) => {
    print(line);
});
````

## Creating and converting an OutputStream to String/Bytes

If you wanna check what it's being output to a given output stream you can create an "in-memory" OutputStream (actually a java.io.ByteArrayOutputStream):

````javascript
var ostream = af.newOutputStream();
ioStreamCopy(ostream, af.fromString2InputStream("Hello World!\n"));

// Converting to string
print(ostream.toString());  

// Converting to an array of bytes
//var b = ostream.toByteArray(); 
````

If you don't wanna copy from another input stream and just want to set the contents of the output stream:

````javascript
var ostream = af.fromString2OutputStream("Hello world!\n");
````

Which is prettry much equivalent to the previous example. Of course there is also a _af.fromBytes2OutputStream_ function.

## Converting and InputStream to String/Bytes

Ok, now we have an input stream that we just wanna check it's contents on the form of an array of bytes:

````javascript
var istream = io.readFileStream("myfile.txt");
var contents = af.fromInputStream2Bytes(istream);
````

Again, a _af.fromInputStream2String_ is also available.