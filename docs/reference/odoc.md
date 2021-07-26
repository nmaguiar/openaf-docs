---
layout: default
title: odoc
parent: Reference
grand_parent: OpenAF docs
---


## odoc

### ODoc

__ODoc(aoDoc)__

````
Object to hold an ODoc, the basic structure for OpenAF documentation. You can provide a ODoc structure to initialize this ODoc object.
````
### ODoc.add

__ODoc.add(aKey, aFullKey, aValue)__

````
Adds a ODoc entry given a key (a unique name), a full key (a function or object signature) and a corresponding text value.
````
### ODoc.addAll

__ODoc.addAll()__

````
Adds an ODoc Map structure imported from another ODoc object.
````
### ODoc.get

__ODoc.get(aKey) : Map__

````
Returns the ODoc entry corresponding to the unique key provided.
````
### ODoc.getAll

__ODoc.getAll() : Map__

````
Returns the ODoc entire Map structure to be exported somewhere else.
````
### ODoc.getKeys

__ODoc.getKeys() : Array__

````
Returns an array with all keys from this ODoc.
````
### ODocs

__ODocs(aPath, aODocs, anArrayURLs, offline)__

````
Object to hold ODocs objects, search them, load or save them (either offline or online). The parameter aPath should be use as a path to save for offline use or as a path to save for online use. The parameter aODocs is optional but it can be used to link with ODocsGen contents (e.g (new ODocsGen(aMapOfFiles)).getODoc())). It's also possible to additionally specify anArrayURLs to load ODocs via web. Optional you can force it to only work offline (offline = true)
````
### ODocs.addAll

__ODocs.addAll(aODoc)__

````
Add an external ODocs structure into these object.
````
### ODocs.save

__ODocs.save()__

````
Saves the current ODocs into the filename provided on the constructor in a way suitable for offline use.
````
### ODocs.saveWeb

__ODocs.saveWeb()__

````
Saves the current ODocs into the path provided on the constructor with files suitable from loading from web.
````
### ODocsGen

__ODocsGen(aMapOfFiles) : ODocsGen__

````
Object to generate ODocs structures. Given a map where the key is a ODoc subject and the value is the filesystem path to a javascript or Java source file (e.g. new ODocsGen({"sample": "/some/place/source.java"})). It finds text within odoc xml tags and adds it as odoc text. Inside the odoc xml tags you should have a key xml tag to specify a unique key within a ODoc subject (the key will be interpreted until the first '(', '{' or '[' occurs). Per standard practice you should specify the entire signature of a function when describing one.
````
### ODocsGen.genODoc

__ODocsGen.genODoc(aFileName) : Map__

````
Generates a ODoc map where each key will be the identified odoc key and the value a map where k will represent the original key and t the associated text.
````
### ODocsGen.genODocs

__ODocsGen.genODocs()__

````
The main execution function. Will generate odoc structures for all the files provided to this object
````
### ODocsGen.getODoc

__ODocsGen.getODoc() : Map__

````
Gets the current odoc maps per id.
````
### ODocsGen.getODocKeys

__ODocsGen.getODocKeys() : Array__

````
Gets the current odocs keys per id.
````
