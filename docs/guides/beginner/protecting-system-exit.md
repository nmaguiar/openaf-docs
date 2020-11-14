---
layout: default
title: Protecting from system exit
parent: Beginner
grand_parent: Guides
---

# Protecting from system exit

Whenever running a script you may want to abort/stop the current execution completely exiting the OpenAF process. You can do that using the function _exit_:

````javascript
exit(0);
// Exits the current execution immediatelly with exit code 0

exit(-1);
// Exits the current execution immediatelly with exit code -1
````

But what if you are calling that script from the openaf-console (using the _load_ function) or similar and you don't want the entire Java process to "die"? You can use the _af.protectSystemExit_ function for that:

````javascript
> af.protectSystemExit(true, "No can do!: ");
> exit(0);
-- No can do!: 0
> exit(-10);
-- No can do!: -10
````

Everytime the script tries to end processing by means of a system exit a javascript execption will be raised with the provided text appended with the corresponding exit code.

If you want to "disarm" this protection:

````javascript
> af.protectSystemExit(false);
> exit(0);
$
````

_Note: this protection uses the Java security manager. So even java system exit code will be affected by this "protection"._