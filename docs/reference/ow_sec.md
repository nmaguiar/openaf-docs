---
layout: default
title: ow.sec
parent: Reference
grand_parent: OpenAF docs
---


## ow.sec

### $sec.$sec

__$sec.$sec(aRepo, dBucket, dLockSecret, aMainSecret, aFile) : $sec__

````
Shortcut for acessing ow.sec.SBuckets given aMainSecret and, optionally, aRepo. A default dBucket and the corresponding dLockSecret can be provided.
````
### $sec.close

__$sec.close() : Object__

````
Close the current repository.
````
### $sec.encSKey

__$sec.encSKey(aKey) : String__

````
Given aKey will return the encrypted version of it with the current main sectet for the repo.

Example:

  $sec("test", "b1", $sec("test", __, __, "Password123").encSKey("Password1"), "Password123", "test.yml").set("mysecret", { l:"l", p:"p" })
  // ...
  $sec("test", "b1", $sec("test", __, __, "Password123").encSKey("Password1"), "Password123", "test.yml").get("mysecret")


````
### $sec.get

__$sec.get(aKey, aBucket, aLockSecret) : Object__

````
Retrieves the secret object/string for aKey. Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.getBucket

__$sec.getBucket(aBucket, aLockSecret) : String__

````
Retrieves a encrypted SBucket string to be transported to another SBucket repo.  Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.getFn

__$sec.getFn(aKey, aExtraArgs, aBucket, aLockSecret) : Object__

````
Invokes a function using the secret arguments for aKey with non-secret aExtraArgs map (arguments should have the same name as the function help parameters). Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.getObj

__$sec.getObj(aKey, aExtraArgs, aBucket, aLockSecret) : Object__

````
Creates a new instance of an object using the secret arguments for aKey with non-secret aExtraArgs map (arguments should have the same name as the constructor help parameters). Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.list

__$sec.list(aBucket, aLockSecret) : Array__

````
Returns a map with a list of all the sBuckets on the current repo. If a specifc sBucket and aLockSecret isn't provide the current sBucket will have an associated array with the list of corresponding keys.
````
### $sec.set

__$sec.set(aKey, aObj, aBucket, aLockSecret) : Object__

````
Sets the secret aObj map/string associating it with aKey. Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.setBucket

__$sec.setBucket(aBucketString, aBucket, aLockSecret) : String__

````
Sets an encrypted SBucket string transported from another SBucket repo (the aLockSecret should be equal) Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.setFn

__$sec.setFn(aKey, aFn, aArgs, aBucket, aLockSecret) : Object__

````
Sets secret aArgs (map with the arguments names on the aFn help)) for calling aFn (string). Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.setObj

__$sec.setObj(aKey, aObj, aArgs, aBucket, aLockSecret) : Object__

````
Sets secret aArgs (map with the arguments names on the aObj constructor help)) for constructing aObj (string). Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.unset

__$sec.unset(aKey, aBucket, aLockSecret) : Object__

````
Unsets aKey for a SBucket. Optionally you can provide a specific aBucket and the corresponding aLockSecret.
````
### $sec.unsetBucket

__$sec.unsetBucket(aBucket)__

````
Unsets aBucket from the current repo.
````
### $sec.unsetRepo

__$sec.unsetRepo()__

````
Unsets the current repo.
````
### ow.sec.closeMainSBuckets

__ow.sec.closeMainSBuckets()__

````
Close the default SBucket.
````
### ow.sec.closeSBuckets

__ow.sec.closeSBuckets(aRepo, aFile)__

````
Close a previously open aRepo SBucket.
````
### ow.sec.openMainSBuckets

__ow.sec.openMainSBuckets(aMainSecret)__

````
Open the default SBucket using aMainSecret.
````
### ow.sec.openSBuckets

__ow.sec.openSBuckets(aRepo, aMainSecret, aFile)__

````
Opens aRepo SBucket using aMainSecret.
````
### ow.sec.purgeMainSBuckets

__ow.sec.purgeMainSBuckets()__

````
Purge the default SBucket.
````
### ow.sec.purgeSBuckets

__ow.sec.purgeSBuckets(aRepo, aFile)__

````
Purge aRepo SBucket.
````
### ow.sec.SBucket.createBucket

__ow.sec.SBucket.createBucket(sBucket, aLockSecret)__

````
Creates a sbucket with a specific aLockSecret.
````
### ow.sec.SBucket.destroyBucket

__ow.sec.SBucket.destroyBucket(sBucket)__

````
Destroys a sBucket.
````
### ow.sec.SBucket.getBucket

__ow.sec.SBucket.getBucket(sBucket, aLockSecret) : String__

````
Given a sbucket and aLockSecret retrieves a string representation of the sbucket.
````
### ow.sec.SBucket.getKeys

__ow.sec.SBucket.getKeys(sBucket, aLockSecret, aKey) : Map__

````
Returns a map with a list of all the sBuckets on the current repo. If a specifc sBucket and aLockSecret isn't provide the current sBucket will have an associated array with the list of corresponding keys.
````
### ow.sec.SBucket.getNewFn

__ow.sec.SBucket.getNewFn(sBucket, aLockSecret, aKey, defaultArgs)__

````
For the sBucket with aLockSecret will invoke a function and set arguments using aKey.
````
### ow.sec.SBucket.getNewObj

__ow.sec.SBucket.getNewObj(sBucket, aLockSecret, aKey, defaultArgs)__

````
For the sBucket with aLockSecret create an object with the arguments in aKey.
````
### ow.sec.SBucket.getSBucket

__ow.sec.SBucket.getSBucket() : String__

````
Returns a string representation of the sbucket.
````
### ow.sec.SBucket.getSecret

__ow.sec.SBucket.getSecret(sBucket, aLockSecret, aKey) : Map__

````
Given a sbucket and a specific aLockSecret will return the associated aKey.
````
### ow.sec.SBucket.getSecretAs

__ow.sec.SBucket.getSecretAs(sBucket, aLockSecret, aEncryptKey, aKey) : Map__

````
Given a sbucket and a specific aLockSecret will return the associated aKey encrypted with aEncryptKey.
````
### ow.sec.SBucket.getSNewFn

__ow.sec.SBucket.getSNewFn(Key)__

````
Will invoke a function and set arguments using aKey.
````
### ow.sec.SBucket.getSNewObj

__ow.sec.SBucket.getSNewObj(aKey)__

````
Create an object with the arguments in aKey.
````
### ow.sec.SBucket.getSSecret

__ow.sec.SBucket.getSSecret(aKey) : Map__

````
Returns the associated aKey value.
````
### ow.sec.SBucket.getSSecretAs

__ow.sec.SBucket.getSSecretAs(aEncryptKey, aKey) : Map__

````
Returns the associated aKey encrypted with aEncryptKey.
````
### ow.sec.SBucket.SBucket

__ow.sec.SBucket.SBucket(aCh, aMainSecret, sBucket, aLockSecret) : sbucket__

````
Creates a set of sbuckets on aCh using aMainSecret.  Defaults, if provided, to sBucket and aLockSecret.
````
### ow.sec.SBucket.setBucket

__ow.sec.SBucket.setBucket(sBucket, aLockSecret, aBucketString)__

````
Given a sbucket, aLockSecret will set the sbucket to the provided aBucketString.
````
### ow.sec.SBucket.setNewFn

__ow.sec.SBucket.setNewFn(sBucket, aLockSecret, aKey, aFn, args)__

````
For the sBucket with aLockSecret will set aKey to use aFn with the arguments map ($fnDev4Help).
````
### ow.sec.SBucket.setNewObj

__ow.sec.SBucket.setNewObj(sBucket, aLockSecret, aKey, aObject, args)__

````
For the sBucket with aLockSecret will set aKey to create aObject with the arguments map ($fnDev4Help).
````
### ow.sec.SBucket.setSBucket

__ow.sec.SBucket.setSBucket(aBucketString)__

````
Set the current sbucket to the provided aBucketString.
````
### ow.sec.SBucket.setSecret

__ow.sec.SBucket.setSecret(sBucket, aLockSecret, aKey, aObj)__

````
Given a sbucket and aLockSecret will set aKey to aObj (string or map)
````
### ow.sec.SBucket.setSNewFn

__ow.sec.SBucket.setSNewFn(aKey, aFn, args)__

````
For the sBucket with aLockSecret will set aKey to use aFn with the arguments map ($fnDev4Help).
````
### ow.sec.SBucket.setSNewObj

__ow.sec.SBucket.setSNewObj(aKey, aObject, args)__

````
Will set aKey to create aObject with the arguments map ($fnDev4Help).
````
### ow.sec.SBucket.setSSecret

__ow.sec.SBucket.setSSecret(aKey, aObj)__

````
Sets aKey to aObj (string or map)
````
### ow.sec.SBucket.unsetSecret

__ow.sec.SBucket.unsetSecret(sBucket, aLockSecret, aKey)__

````
Given a sbucket and aLockSecret will unset aKey.
````
### ow.sec.SBucket.unsetSSecret

__ow.sec.SBucket.unsetSSecret(aKey)__

````
Unsets aKey.
````
