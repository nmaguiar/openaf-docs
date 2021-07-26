---
layout: default
title: Shebang
parent: Concepts
grand_parent: OpenAF docs
---

# Shebang

[Shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) is a character sequence (__#!__), used in Unix-based operating systems, that enables on a text file to indicate a program interpreter to execute the rest of the remaining of the file.

OpenAF also supports this unix functionality and makes it easy to transform any existing OpenAF script into a shebang unix script.

## Simple Unix example

If you already know how Unix's Shebang functionality works you can skip to the next section. If not let's start with a simple Unix shell script editing a sample file _example.sh_:

````sh
NAME=Scott
echo Hello $NAME
````

If you execute it will print the expected result:

````sh
$ /bin/sh example.sh
Hello Scott
````

To avoid having to mention the script interpreter (e.g. _/bin/sh_) in Unix you can add a "shebang" editing the header of the _example.sh_ file:

````sh
#!/usr/bin/sh
NAME=$1
echo Hello $NAME
````

Then you just need to set execution permissions and _execute it_:

````sh
$ chmod +x example.sh
$ ./example.sh Tom
Hello Tom 
````

## Setting _shebang_ for OpenAF

Let's start by a very simple OpenAF script _example.js_:

````javascript
var name = "Scott";
print("Hello " + name);
````

Executing with OpenAF as you would normally do:

````sh
$ [openaf path]/oaf -f example.js
Hello Scott
````

### Adding _shebang_

To add the shebang and set the execution permissions in Unix just execute with OpenAF:

````sh
$ [openaf path]/oaf --sb example.js
````

__That's it!__ It's ready, just execute _directly_:

````sh
$ ./example.js
Hello Scott
````

### Using parameters

After using OpenAF to set _shebang_ on a existing script it actually pre-appends the necessary code to use command-line parameters. Let's go through the changes necessary to provide a custom name:

````sh
$ ./example.js name=Tom
````

Let's start by looking at the generated code in _example.js_:

````javascript
#!/usr/bin/env /openaf/oaf-sb

var params = processExpr(" ");
// sprint(params);

var name = "Scott";
print("Hello " + name);
````

Apart from the first _shebang_ line there are two extra lines added by OpenAF:

````javascript
var params = processExpr(" ");
// sprint(params);
````

The first one creates a _params_ variable to capture the result of calling the OpenAF function _processExpr_. This OpenAF function takes one argument (e.g. " ") as the command-line separator between command-line parameters and will return a javascript map with the corresponding result. Let's try out some examples to better understand how it works. To test it just temporially uncomment the _sprint_ line added previously by OpenAF:

````javascript
#!/usr/bin/env /openaf/oaf-sb

var params = processExpr(" ");
sprint(params);

var name = "Scott";
print("Hello " + name);
````

Now try executing with different parameters combinations (note: openaf expects parameters to be a pair of key and corresponding value separated with _'='_):

````sh
$ ./example.js name=Tom
{
    "name": "Tom"
}
Hello Scott
$
$ ./example.js name=Tom something other=stuff
{
    "name": "Tom",
    "something": "",
    "other": "stuff"
}
````

Returning to the initial propose we would like to use the _name_ parameter to customize the name to display. So let's assign it to the existing _name_ variable:

````javascript
#!/usr/bin/env /openaf/oaf-sb

var params = processExpr(" ");
// sprint(params);

var name = params.name;  // <-- assigning the name parameter 
print("Hello " + name);
````

Executing it after the last changes:

````sh
$ ./example.js name=Tom
Hello Tom
````