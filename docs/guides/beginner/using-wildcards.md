---
layout: default
title: Using wildcards
parent: Beginner
grand_parent: Guides
---

# Using wildcards

When thinking of filtering files you might want to use wildcards. For example:

* ````*.yaml```` - to filter by all files that end with the _yaml_ extension
* ````my-file-??.*```` - to filter by files whose filename starts with "my-file-" followed by two characters and any extension

In Javascript the closest that you have is [regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions). Nevertheless wildcards are simpler to understand and use than regular expressions especially for filename filtering. 

## Simple use in OpenAF

So, starting with OpenAF version 20221216, you can use a built-in function (ow.format.string.wildcardTest) that will return true or false if a wildcard expression matches the provided string.

````javascript
ow.loadFormat()
ow.format.string.wildcardTest("myfile.yaml", "*.yaml")
// true
ow.format.string.wildcardTest("myfile.json", "*.yaml")
// false
````

## Filtering a list of files

You can use it in conjunction with io.listFiles to filter an array of files:

````javascript
io.listFiles(".").files.filter(f => ow.format.string.wildcardTest(f.filepath, "*.yaml"))
// results in array with only the entries whose filenames end in ".yaml"
````

## Case sensitive

The default behaviour is to be case insensitive:

````javascript
ow.format.string.wildcardTest("myfile.yaml", "*.yaml")
// true
ow.format.string.wildcardTest("myfile.YAML", "*.yaml")
// true
````

But in some cases you might want for the expressions to be case sensitive. For that you can use a third argument of _ow.format.string.wildcardTest_:

````javascript
> ow.format.string.wildcardTest("myfile.yaml", "*.yaml", true)
true
> ow.format.string.wildcardTest("myfile.YAML", "*.yaml", true)
false
````