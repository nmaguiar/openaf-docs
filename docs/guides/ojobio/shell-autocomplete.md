---
layout: default
title: Unix shell auto-complete
parent: oJobIO
grand_parent: Guides
---

# Unix shell auto-complete

With hundreds of available oJob's in [ojob.io](https://ojob.io) it becomes usefull to be able to hit _<TAB>_ and use the auto-complete features available in Unix and Mac OS shells. Here is how to enable it.

## Linux/Unix

On Linux/Unix the auto-complete functionality is based on the _bash_ shell. To quickly add the auto-complete to the current session just execute:

````bash
. <(ojob ojob.io/unix/ojobComplete)
````

When the _unix/ojobComplete_ runs a bash-compatible "complete" command string is generated with the current contents of ojob.io. 

## Mac OS

The more recent versions of Mac OS use the _zsh_ on which you can quickly add the auto-complete to the current session by just executing:

````sh
. <(curl https://ojob.io/unix/ojobComplete.sh)
````

> If you are using an older Mac OS version based on _bash_ simply follow the instructions for Linux/Unix.