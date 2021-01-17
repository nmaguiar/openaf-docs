---
layout: default
title: git
parent: Reference
grand_parent: OpenAF docs
---


## git

### GIT.add

__GIT.add(aFilePattern) : JavaDirCache__

````
Adds a given aFilePattern (e.g. "some.file.txt" or "someFiles*") to the current open repository. Throws a "Repository not open"  exception if the repository is not open.
````
### GIT.add

__GIT.add(aFilePattern) : JavaDirCache__

````
Adds a given aFilePattern (e.g. "some.file.txt" or "someFiles*") to the current open repository. Throws a "Repository not open"  exception if the repository is not open.
````
### GIT.branch

__GIT.branch() : String__

````
Returns the current branch for the repository.
````
### GIT.branch

__GIT.branch() : String__

````
Returns the current branch for the repository.
````
### GIT.branchCreate

__GIT.branchCreate(aBranchName)__

````
Creates a branch with the provided aBranchName on the current open GIT repository.
````
### GIT.branchCreate

__GIT.branchCreate(aBranchName)__

````
Creates a branch with the provided aBranchName on the current open GIT repository.
````
### GIT.branchDelete

__GIT.branchDelete(aBranchName)__

````
Deletes a branch named aBranchName from the current open GIT repository.
````
### GIT.branchDelete

__GIT.branchDelete(aBranchName)__

````
Deletes a branch named aBranchName from the current open GIT repository.
````
### GIT.branchList

__GIT.branchList()__

````
Lists the name and objectId for each branch available on the current open GIT repository.
````
### GIT.branchList

__GIT.branchList()__

````
Lists the name and objectId for each branch available on the current open GIT repository.
````
### GIT.branchRename

__GIT.branchRename(aOldName, aNewName)__

````
Renames aOldName branch with aNewName on the current open GIT repository.
````
### GIT.branchRename

__GIT.branchRename(aOldName, aNewName)__

````
Renames aOldName branch with aNewName on the current open GIT repository.
````
### GIT.checkout

__GIT.checkout(aPath, aBranchName) : JavaRef__

````
Checkouts the current GIT repository to aPath. Optionally you can provide aBranchName to checkout a specific branch.
````
### GIT.checkout

__GIT.checkout(aPath, aBranchName) : JavaRef__

````
Checkouts the current GIT repository to aPath. Optionally you can provide aBranchName to checkout a specific branch.
````
### GIT.clone

__GIT.clone(aURL, aDirectory, cloneAll, aBranchName, aUser, aPassword)__

````
Clones aURL GIT repository to the aDirectory provided. Optionally, if you want all branches cloned you can indicate that with cloneAll = true. If don't want all branches cloned but a specific one you can indicate it with aBranchName.
````
### GIT.clone

__GIT.clone(aURL, aDirectory, cloneAll, aBranchName, aUser, aPassword)__

````
Clones aURL GIT repository to the aDirectory provided. Optionally, if you want all branches cloned you can indicate that with cloneAll = true. If don't want all branches cloned but a specific one you can indicate it with aBranchName.
````
### GIT.close

__GIT.close()__

````
Closes the current open GIT repository.
````
### GIT.close

__GIT.close()__

````
Closes the current open GIT repository.
````
### GIT.commit

__GIT.commit(aMessage, aName, anEmail) : JavaRevCommit__

````
Commits the current open GIT repository with aMessage provided. Throws an exception if not possible. Optionally you can also provide aName and anEmail.
````
### GIT.commit

__GIT.commit(aMessage, aName, anEmail) : JavaRevCommit__

````
Commits the current open GIT repository with aMessage provided. Throws an exception if not possible. Optionally you can also provide aName and anEmail.
````
### GIT.fetch

__GIT.fetch(aRemote)__

````
Performs a fetch command on the current open GIT repository. Optionally you can provide aRemote.
````
### GIT.fetch

__GIT.fetch(aRemote)__

````
Performs a fetch command on the current open GIT repository. Optionally you can provide aRemote.
````
### GIT.getJavaGit

__GIT.getJavaGit() : JavaGit__

````
Returns the internal Java GIT object.
````
### GIT.getJavaGit

__GIT.getJavaGit() : JavaGit__

````
Returns the internal Java GIT object.
````
### GIT.GIT

__GIT.GIT(aDirectory, aUser, aPassword)__

````
Creates a GIT object instance to access a GIT repository on the aDirectory provided. Optionally you can provide also a login and password for remote repositories.
````
### GIT.GIT

__GIT.GIT(aDirectory, aUser, aPassword)__

````
Creates a GIT object instance to access a GIT repository on the aDirectory provided. Optionally you can provide also a login and password for remote repositories.
````
### GIT.init

__GIT.init(aDirectory)__

````
Initializes a GIT repository on the aDirectory provided.
````
### GIT.init

__GIT.init(aDirectory)__

````
Initializes a GIT repository on the aDirectory provided.
````
### GIT.open

__GIT.open(aDirectory)__

````
Opens a GIT repository on the aDirectory provided.
````
### GIT.open

__GIT.open(aDirectory)__

````
Opens a GIT repository on the aDirectory provided.
````
### GIT.pull

__GIT.pull()__

````
Performs a pull command on the current opened GIT repository.
````
### GIT.pull

__GIT.pull()__

````
Performs a pull command on the current opened GIT repository.
````
### GIT.push

__GIT.push()__

````
Performs a push command on the current opened GIT repository.
````
### GIT.push

__GIT.push()__

````
Performs a push command on the current opened GIT repository.
````
### GIT.remove

__GIT.remove(aFilePattern)__

````
Removes a given aFilePattern (e.g. "some.file.txt" or "someFiles*") from the current open repository. Throws an exception if not possible.
````
### GIT.remove

__GIT.remove(aFilePattern)__

````
Removes a given aFilePattern (e.g. "some.file.txt" or "someFiles*") from the current open repository. Throws an exception if not possible.
````
