---
layout: default
title: "Beginner: Creating a ZIP file"
parent: Guides
grand_parent: OpenAF docs
---

# Creating a ZIP file

OpenAF includes a specific plugin to group all the ZIP related functionality trying to make it easy to use it.

In this case we will show how easy is to create a ZIP file. We have two local files that we want to add to a new zip file: myclass.java and myclass.class.

````javascript
plugin("ZIP");

zip.putFile("src/myclass.java", "myclass.java");
zip.putFile("bin/myclass.class", "myclass.class");

zip.generate2File("myclass.zip", { compressionLevel: 9 });
zip.close();
````

If you look carefully we are taking two local files, from the same folder, but storing them in different folders inside the ZIP file (e.g. _zip.putFile(target, source)_).

The ZIP file will get written when you call the _zip.generate2File(aFilePath, mapOptions)_ function. Besides creating the _"myclass.zip"_ we are also specifying that we want the maximum compression possible (e.g. level 9).

You can explore the contents of this newly created zip file using _zip.list(aZipFile)_ function:

````javascript
> plugin("ZIP");
> var zip = new ZIP();
> zip.list("myclass.zip");
+--------------------+-----------------+-------------------+
|  src/myclass.java: | compressedSize: | 17                |
|                    |           size: | 15                |
|                    |            crc: | 3010494688        |
|                    |           name: | src/myclass.java  |
|                    |        comment: | null              |
|                    |           time: | 1569369872000     |
+--------------------+-----------------+-------------------+
| bin/myclass.class: | compressedSize: | 18                |
|                    |           size: | 16                |
|                    |            crc: | 626008697         |
|                    |           name: | bin/myclass.class |
|                    |        comment: | null              |
|                    |           time: | 1569369872000     |
+--------------------+-----------------+-------------------+
````

_Note: for bigger ZIP files you can use zip.streamPutFile*_