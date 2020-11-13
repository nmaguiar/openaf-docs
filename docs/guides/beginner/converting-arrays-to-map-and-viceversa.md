---
layout: default
title: "Beginner: How to convert arrays to maps and vice-versa"
parent: Guides
grand_parent: OpenAF docs
---

# How to convert arrays to maps and vice-versa

When working with javascript maps of maps or arrays of maps you might sometimes think: "if only it was an array instead of an object" or "if only it was an object instead of an array". 

Usually this happens when you know the perfect method/library but it would only work with arrays or objects.

In OpenAF there are two functions to try to make it easier to convert arrays to maps and vice-versa: _ow.obj.fromArray2Obj_ and _ow.obj.fromObj2Array_.

## Converting a map into an array

Let's take, for example, the map that it's returned by the _getRemoteOPackDB()_:

````javascript
{
    "OpenAF-Templates": {
        "version": "20190906",
        "files": [
            // ...
        ],
        "description": "..."
    },
    "OpenAFLambdaLayers": {
        "version": "20190809",
        "files": [
            //...
        ],
        "description": "..."
    },
    ...
}
````

You can quickly convert into an array:

````javascript
> ow.loadObj();
> var ar = ow.obj.fromObj2Array(getRemoteOPackDB(), "name")
[
    {
        "name": "OpenAF-Templates",
        "version": "20190906",
        "files": [
            // ...
        ],
        "description": "..."
    },
    {
        "name": "OpenAFLambdaLayers",
        "version": "20190809",
        "files": [
            // ...
        ],
        "description": "..."
    }
]
> printTable(mapArray(ar, ["name", "version"]));
       name        |version
-------------------+--------
OpenAF-Templates   |20190906
OpenAFLambdaLayers |20190809
// ...
````

The second parameter for _ow.obj.fromObj2Array_ is the attribute that the array of maps will include if you want to map each key into an entry (e.g. in this case _name_).

## Converting an array into a map

Let's take the example of an array with the list of files:

````javascript
> var files = io.listFiles("/my/folder").files;
> var obj = ow.obj.fromArray2Obj(files, "canonicalPath");
{
    "/my/folder/a.js": {
        "isDirectory": false,
        "isFile": true,
        "filename": "a.js",
        "filepath": "/my/folder/a.js",
        "lastModified": 1534542464558,
        "createTime": 1534541960321,
        "lastAccess": 1562153514605,
        "size": 16384,
        "permissions": "xrw"
    },
    "/my/folder/b.js": {
        // ...
    }
}
````

The second argument provided to the function _ow.obj.fromArray2Obj_ will be each map's entry that will be used as key on the resulting map. 

Optionally you can also add a third boolean argument to indicate if you want, or not, the entry remote from each map detail.