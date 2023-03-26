---
layout: default
title: Reading, listing and writing TAR files
parent: Medium
grand_parent: Guides
---

# Reading, listing and writing TAR files

_version: >= 20220508_

It's possible to directly read, list or write TAR (or tar gzipped files) directly from OpenAF. This allows OpenAF scripts not only to [work with ZIP files](../beginner/creating-a-zip-file.md) but also tar/tar.gz files.

## Writing

Let's start by writing a simple tar file based on a Java source-code folder (e.g. "src") with multiple levels of folders:

````javascript
ow.loadFormat()
print("Creating mytar.tgz:")

io.writeFileTARStream("mytar.tgz", true, writer => {
	// Listing all files that end in .java from the sub-folder src
	$from( listFilesRecursive("src") )
	.ends("filename", ".java")
	.select(r => {
		// Remove src/ prefix from the path
		var targetFilePath = r.filepath.replace(/^src\//, "")

		// Add bytes abbreviation
		r.bytesAbb = ow.format.toBytesAbbreviation(r.size)
{% raw %}
		tprint("  writing {{filepath}} ({{bytesAbb}})", r)
{% endraw %}
        // Writing a file to the tgz file
		writer(targetFilePath, io.readFileStream(r.filepath))
	})
})
````

The function __io.writeFileTARStream__ receives three arguments: a target filename (or Java stream), a boolean to indicate if it's gzipped or not and a function that provides a _writer_ function. This _writer_ function should be called as many times as files you want to add to your tgz file. It's arguments are: _filePathOnTheTarFile_, _inputJavaStreamForAFile_.

The result of running the previous code will be similar to this:

````bash
$ tar tzf mytar.tgz
openaf/JAnsiRender.java
openaf/OAFdCL.java
openaf/CompileJS2Java.java
openaf/OAFEngineFactory.java
openaf/plugins/SSH.java
openaf/plugins/HTTP.java
openaf/plugins/ZIP.java
[...]
````
> Notice that despite the files being located in src/openaf/* and src/openaf/plugins/* what matters is the targetFilePath you provide to the _writer_ function.

## Listing

To list you just need to use the function __io.listFilesTAR__:

````bash
> $from( io.listFilesTAR("mytar.tgz") )
  .less("size", 1024)
  .select({ filepath: "", size: -1 })

╭ [0] ╭ filepath: openaf/jline/OpenAFArgumentDelimiter.java 
│     ╰ size    : 552 
├ [1] ╭ filepath: openaf/core/AF.java 
│     ╰ size    : 212 
├ [2] ╭ filepath: org/json/JSONException.java 
│     ╰ size    : 709 
├ [3] ╭ filepath: org/json/JSONString.java 
│     ╰ size    : 740 
╰ [4] ╭ filepath: com/jamesmurty/utils/XMLBuilderRuntimeException.java 
      ╰ size    : 526 
````

## Reading

To read you can use the function __io.readFileTARStream__:

````javascript
ow.loadFormat()

var targetFolder = "/tmp/myTar"
var source       = "mytar.tgz"
print("Expanding " + source + "...")
$from( io.listFilesTAR(source) )
.less("size", 1024)
.select(r => {
	io.readFileTARStream(source, r.filepath, true, iStream => {
		// Determines the complete path
		var parentDir = targetFolder + "/" + r.filepath.substr(0, r.filepath.lastIndexOf("/"))
		io.mkdir(parentDir)   // Ensure folder is created or exists

		// Add bytes abbreviation
		r.bytesAbb = ow.format.toBytesAbbreviation(r.size)
{% raw %}
		tprint("  writing {{filepath}} ({{bytesAbb}})", r)
{% endraw %}
		ioStreamCopy(io.writeFileStream(parentDir + "/" + r.filename), iStream)
	})
})
````

If you need just the contents of file you can quickly do it using __io.readFileTARBytes__:

````javascript
var fileContents = af.fromBytes2String( io.readFileTARBytes("mytar.tgz", "openaf/core/AF.java", true) )
print("The file has #" + fileContents.split("\n").length + " lines.")
````