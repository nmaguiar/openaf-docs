---
layout: default
title: Making it easy to read with $from
parent: Beginner
grand_parent: Guides
---

# Making it easy to read with $from

When you start to write several OpenAF scripts you will usually start to write a log while/for/do cycles to go through an array and perform so task. Take the following example (which might be hard to read for a beginner):

What this piece of code does is:

````javascript
var list = io.listFiles("."); 
var found = false, i = 0;
while(!found) {
   var file = list.files[i];
   if (file.isFile && file.filename == "myScript.js") 
      found = true;
   else
      i++;
}
var myRecord = list.files[i];
````

  * Get an array with all the files and folders on the folder "." (through io.listFiles). This will result in an array of maps. Similar to: 
  ````javascript
  {
  "isDirectory": true,
  "isFile": false,
  "filename": "somefile.txt",
  "filepath": "./somefile.txt",
  "canonicalPath": "/some/folder/somefile",
  "lastModified": 1560515651403,
  "createTime": 1560515651374,
  "lastAccess": 1564194441636,
  "size": 640,
  "permissions": "xrw"
},
````
  * Iterate through each element of the array trying to find a filename equal to "myScript.js" and ensuring it's a file and not a folder.
  * Once found, break the cycle and store the corresponding map in the variable myRecord

Now let's rewrite it using $from (a shortcut to the [JLinq library](http://hugoware.net/projects/jlinq)):
````javascript
var myRecord = $from(io.listFiles(".").files)
        .equals("isFile", true)
        .equals("filename", "myScript.js")
        .select();
````

Doesn't it look a little bit easier to read? It's structured like a SQL query where "from" points to the array origin, the "where" comes next is the functions equals to test if it's a file and for the filename "myScript.js" and finally "select"s all fields keeping the result in myRecord.

Some more examples:

````javascript
// From a listOfThings array of maps, where type equals "item" and barcode starts with "501"
// return true if there is any matching map.
$from(listOfThings).equals("type", "item").starts("barcode", "501").any();

// From a list of files of the current folder, where it's a directory, count the corresponding
// matching maps.
$from(io.listFiles(".").files).equals("isDirectory", true).count();

// From a files of files of the current folder, where filename matches the regular expression 
// "work.+", select only the field filename from the map (if it doesn't exist replace the 
// missing value with "")
$from(io.listFiles(".").files).match("filename", "work.+").select({ filename: "" });

// From a listOfThings array of maps, where type equals "item", sort the results by name and 
// select the result by running a function passing to it each matching map. The returned result
// of executing the function with each matching map will be returned in an array.
$from(listOfThings)
.equals("type", "item")
.sort("name")
.select((record) => {
   return r.barcode + " - " + r.name;
});
````

You can check more examples on the [jLinq demo](http://www.hugoware.net/projects/jlinq/demo) or typing, in the openaf-console, "desc $from([])".