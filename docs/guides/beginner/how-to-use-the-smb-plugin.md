---
layout: default
title: "Beginner: How to upload/download files from a Window/SMB share folder"
parent: Guides
grand_parent: OpenAF docs
---

# How to upload/download files from a Window/SMB share folder

The OpenAF's SMB plugin (or the SaMBa plugin, or the [Server Message Block](https://en.wikipedia.org/wiki/Server_Message_Block) plugin) can be added by installing the "plugin-smb" oPack. It allows scripts to upload, download, remove and list files on a remote Windows/Samba share (depending on the user's permission, of course).

_(note: it supports SMBv3)_

## How to install it

Just execute:

````bash
opack install plugin-smb
````

## How to use it

After installing you need to include the SMB plugin on your code:

````javascript
plugin("SMB");
````

Now you can create any javascript object instance to access a SMB URL on a given domain with the corresponding user and password:

````javascript
var smb = new SMB("smb://my.server/myShare", "mydomain", "myuser", "mypassword");
````

### Listing files on a share folder

To list the files on a specific folder you can use the _.listFiles_ function:

````javascript
> smb.listFiles("smb://my.server/myShare/aFolder");
+--------+-----+---------------+--------------------------------------------------------+
| files: | [0] |     filename: | a/                                                     |
|        |     |     filepath: | smb://my.server/myShare/aFolder/a/                     |
|        |     |         size: | 0                                                      |
|        |     |  permissions: | <all permissions>                                      |
|        |     | lastModified: | 1552671846146                                          |
|        |     |   createTime: | 1302948583597                                          |
|        |     |  isDirectory: | true                                                   |
|        |     |       isFile: | false                                                  |
+--------+-----+---------------+--------------------------------------------------------+
|        | [1] |     filename: | Thumbs.db                                              |
|        |     |     filepath: | smb://my.server/myShare/aFolder/Thumbs.db              |
|        |     |         size: | 99328                                                  |
|        |     |  permissions: | <all permissions>                                      |
|        |     | lastModified: | 1555318143997                                          |
|        |     |   createTime: | 1379322293251                                          |
|        |     |  isDirectory: | false                                                  |
|        |     |       isFile: | true                                                   |
+--------+-----+---------------+--------------------------------------------------------+
````

Notice that the _filepath_ entry is the prebuilt URL you can use to list another sub-folder, for example.

### Downloading a file from a share folder

To download a file you just need to provide the SMB URL:

````javascript
> smb.getFile("smb://my.server/myShare/aFolder/Thumbs.db", "theOtherThumbs.db");
99328
````

It will return you the number of bytes transfered.

You can also use _.getFileBytes_ to handle the download content as an internal array of bytes instead of saving to a file and _.getInputStream_ to receive a stream to handle the download. Check the corresponding help information on the openaf-console.

### Uploading a file to a share folder

To upload a file it's similar to the download, reversing the arguments for the _.putFile_ function:

````javascript
> smb.putFile("readme.txt", "smb://my.server/myShare/aFolder/readme.txt");
1235
````

It will also return you the number of bytes transfered.

As with the _.getFile_ function you also have the functions _.writeFileBytes_ to upload content directly from an internal array of bytes instead of a local file and _.writeFileStream_ to upload directly from a stream. Check the corresponding help information on the openaf-console. There is also an extra argument to _append_ content to an existing file on the remote share folder.

### Removing a file from a remote share folder

To delete a file from a remote share folder just use the _.rm_ function:

````javascript
smb.rm("smb://my.server/myShare/aFolder/readme.txt")
````