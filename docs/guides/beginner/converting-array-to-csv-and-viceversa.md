---
layout: default
title: Converting an array to a CSV file and vice-versa
parent: Beginner
grand_parent: Guides
---

# Converting an array to a CSV file and vice-versa

The OpenAF's included CSV object provides some basic functionality for handling CSV files. Althought not intended for handling "huge" CSV files some of these functions are usually handy to quickly convert javascript arrays (composed of javascript map entries) to and from a CSV file. 

The main CSV functions to use are: _CSV.fromArray2File_ and _CSV.fromFile2Array_.

## Converting from an Array to a CSV file

Here is an example:

````javascript
// Let's prepare a sample array with all the file info from the current folder
var myArray = io.listFiles(".").files;

// Let's create a CSV object instance
var csv = new CSV();

// Now simply write a file based on the existing array
csv.fromArray2File(myArray, "mycsv.csv");
````

Now if you check the newly created (or overwritten) CSV file it will look similar to:

````csv
"isDirectory","isFile","filename","filepath","canonicalPath","lastModified","createTime","lastAccess","size","permissions"
"false","true","opack","./opack","/openaf/opack",1569823332000,1569823332000,1569823332000,353,"xrw"
"false","true","openaf","./openaf","/openaf/openaf",1569823332000,1569823332000,1569823332000,342,"xrw"
````

which maps the original array content:

````javascript
> myArray
[{
    isDirectory: false,
    isFile: true,
    filename: "opack",
    filepath: "./opack",
    canonicalPath: "/openaf/opack",
    lastModified: 1569823332000,
    createTime: 1569823332000,
    lastAccess: 1569823332000,
    size: 353,
    permissions: "xrw"
}, {
    isDirectory: false,
    isFile: true, 
    filename: "openaf",
    filepath: "./openaf",
    canonicalPath: "/openaf/openaf",
    lastModified: 1569823332000,
    createTime: 1569823332000,
    lastAccess: 1569823332000,
    size: 342,
    permissions: "xrw"
}
...
````

If you examine it carefully the boolean values, from the javascript map, were converted to _strings_. This is expected since the CSV format will only map javascript _Number_ and _String_ trying to convert any other unknown type to _String_.

_Note: Javascript maps can contain sub-maps and sub-arrays. These won't be correctly converted to CSV._

### Specific array fields

As an optional third argument of the _CSV.fromArray2File_ function you can also limit the fields used or provide a specific order to use:

````javascript
csv.fromArray2File(myArray, "mycsv.csv", ["canonicalPath", "size"]);
````

## Converting a CSV file into an array

Using the previous example where we converted a javascript array into a CSV file, it's easy to convert back to an array:

````javascript
var myNewArray = csv.fromFile2Array("mycsv.csv");
````

But, as previously warned, some types will be represented as strings:

````javascript
> myNewArray
[{
  isDirectory: "false",
  isFile: "true",
  filename: "opack",
  filepath: "./opack",
  canonicalPath: "/openaf/opack",
  lastModified: "1569823332000",
  createTime: "1569823332000",
  lastAccess: "1569823332000",
  size: "353",
  permissions: "xrw"
}, {
...
````

Nevertheless these functions provide a quick and easy way to convert javascript arrays to and from CSV files which can be useful when you are trying to use the javascript data with other tools.