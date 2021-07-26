---
layout: default
title: bsdiff
parent: Reference
grand_parent: OpenAF docs
---


## bsdiff

### BSDiff.BSDiff

__BSDiff.BSDiff()__

````
Creates a new BSDiff instance to diff and patch binary files.
````
### BSDiff.diff

__BSDiff.diff(anOldFile, aNewFile, aPatchFile)__

````
Given anOldFile and aNewFile binary file, the two will be compared and a new compressed aPatchFile will be generated. Check compression to be used with BSDiff.getCompression().
````
### BSDiff.diffBytes

__BSDiff.diffBytes(oldArrayOfBytes, newArrayOfBytes) : ArrayOfBytes__

````
Given oldArrayOfBytes and newArrayOfBytes, the two will be compared and a new compressed ArrayOfBytes will be generated and returned. Check compression to be used with BSDiff.getCompression().
````
### BSDiff.getCompression

__BSDiff.getCompression() : String__

````
Returns the current compression method in use.
````
### BSDiff.patchBytes

__BSDiff.patchBytes(oldFile, patchFile, newFile) : ArrayOfBytes__

````
Given an oldFile will apply a patchFile (produced by diff/diffBytes) and write the result to newFile.
````
### BSDiff.setCompression

__BSDiff.setCompression(aCompression)__

````
Sets a different compression method to be used (based on Apache Commons Compression available methods).
````
