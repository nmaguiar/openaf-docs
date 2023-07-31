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
. <(curl https://ojob.io/autoComplete.sh)
````

When the _unix/ojobComplete_ runs a bash-compatible "complete" command string is generated with the current contents of ojob.io. 

## Mac OS

The more recent versions of Mac OS use the _zsh_ on which you can quickly add the auto-complete to the current session by just executing:

````sh
. <(curl -s https://ojob.io/unix/ojobComplete.sh)
````

> If you are using an older Mac OS version based on _bash_ simply follow the instructions for Linux/Unix.

## Testing

On your bash/zsh session try to write and hit the _tab_ key:

````
ojob ojob.io/hel<TAB><TAB>
ojob ojob.io/hello/w<TAB>
ojob ojob.io/hellow/world<ENTER>
````

## Making the auto-complete functionality permanent

### Linux/Unix

On a Linux/Unix with a bash shell, you can edit your user's ~/.bashrc and append the following commands:

````bash
if [ ! -e ~/.openaf-ojobio-complete ] || [ $(find ~/.openaf-ojobio-complete -mtime +1) ]; then curl https://ojob.io/autoComplete.sh > ~/.openaf-ojobio-complete; fi
source ~/.openaf-ojobio-complete
````

> This will create a ~/.openaf-ojobio-complete file if it doesn't exist or it's older than 1 day (to refresh the list from ojob.io). Afterwards it loads the file into bash auto-complete functionality.

### Mac OS

In Mac OS, using zsh, you can edit your user's ~/.zshrc and append the following commands:

````bash
if [ ! -e ~/.openaf-ojobio-complete ] || [ $(find ~/.openaf-ojobio-complete -mtime +1) ]; then https://ojob.io/autoComplete.sh > ~/.openaf-ojobio-complete; fi
autoload -U +X compinit && compinit
autoload -U +X bashcompinit && bashcompinit
source ~/.openaf-ojobio-complete
````

> This will create a ~/.openaf-ojobio-complete file if it doesn't exist or it's older than 1 day (to refresh the list from ojob.io). Afterwards it loads the file into zsh auto-complete functionality.