---
layout: default
title: "Medium: Using the OpenAF&#x27;s SVN plugin"
parent: Guides
grand_parent: OpenAF docs
---

# Using the OpenAF's SVN plugin

There is a built-in SVN client (plugin) in OpenAF that doesn't require any other installed SVN binary to run. Below some examples of commands you can use.

Before using it you have to load the plugin:

````javascript
plugin("SVN");
````

## Checking out from SVN

You can check out *without authenticating* yourself (if allowed by the SVN server via HTTP):

````javascript
var svn = new SVN("http://my.svn.server/svn/nAttrMon/trunk");
svn.checkout("nAttrMon") // "102"
````

And that's it. The folder “nAttrMon” should have been created on the current folder with a checkout from nAttrMon's current trunk. The checkout operation ends indicating the revision retrieved (in this case 102).

You can check out *authenticating* yourself:

````javascript
var svn = new SVN("svn+ssh://my.svn.server/v1/svn/repos/project", "myuser", "mypass");
svn.checkout("."); // "1002"
````

_Note: When providing the password to authenticate you can use also use an encrypted text._

## Updating your working copy

To update your working copy (using the nAttrMon's example):

````javascript
svn.update(["config/inputs", "config/outputs"], "HEAD")
````

This will update only the config/inputs and config/outputs folders. You may optionally also provide which revision you want (in this case the HEAD for the latest).

## Commit changes and new files

Let's say you created a new input and output and you wish to add it to the input.disabled and output.disabled examples folders in nAttrMon:

````javascript
var svn = new SVN("http://my.svn.server/svn/nAttrMon/trunk", "myuser", "mypass");
svn.add([
  "config/input.disabled/myAwesomeInput.js",
  "config/output.disabled/myAwesomeOutput.js"]);
svn.commit(
  ["config/input.disabled", "config/output.disabled"], 
  "My new awesome nAttrMon input and output plugs! and some bug corrections..."
);
````

First, before any commit you need to authenticate yourself. Then if you are adding new files you need to use _svn.add_ and provide an array of the new files you are adding. Then finally you can commit providing a list of folders that contain new or changed files.

## Additional tricks

### You can retrieve just the files you need

You don't need to checkout an entire folder if you just need to files. For example:

````javascript
var svn = new SVN("http://my.svn.server/svn/nAttrMon/trunk/config/inputs.disabled");
svn.update(["00.doc.js", "00.init.js"]);
````

Will retrieve just the 00.doc.js and 00.init.js files from the trunk/config/inputs.disabled SVN repository folder.

### Revert a changed file

You aren't sure you changed a file on your working copy directory, no problem:

````javascript
svn.revert(["00.init.js"]);
````

_Note: Most SVN functions accept file path arrays meaning it could be just the file path to a file or it can be for an entire folder (for example: svn.update[“.”])._