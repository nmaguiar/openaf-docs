---
layout: default
title: "Medium: How to run OpenAF code from shell script"
parent: Guides
grand_parent: OpenAF docs
---

# How to run OpenAF code from shell script

To run an OpenAF script you just need to execute: _'openaf -f myScript.js'_. But what if you wanted to include some OpenAF code without having to create a separate file. There are several ways to achived this with OpenAF.

## Inline code

The simplest way it's using the _'-c'_ option:

````bash
$ openaf -c 'var res = $rest().get("https://uinames.com/api"); print(printMap(res, void 0, "plain", true))'
+----------+---------------+
|    name: | John          |
| surname: | Lawrence      |
|  gender: | male          |
|  region: | United States |
+----------+---------------+
````

Incorporating into a shell script:

````bash
#!/bin/sh

name=$(openaf -c 'print($rest().get("https://uinames.com/api").name)')
echo Hi $name
````

Running:

````bash
$ sh sayHi.sh
Hi Andrea
````

## Multiline code

For simple code inline code works well but for multi line code it may become hard to read. Another option is using the _'-p'_ option that will receive input from _stdin_.

````bash
#!/bin/bash

output=$(openaf -i script -p << __endScript

  // OpenAF javascript code
  var res = \$rest().get("https://uinames.com/api/?ext");
  print(res.name + " " + res.surname + ";" + res.phone);

__endScript
)

# interpreting result in bash
IFS='\;'
read -a strarr <<< "$output"

echo Name : ${strarr[0]}
echo Phone: ${strarr[1]}
````

And the result of mixing shell script and OpenAF:

````bash
Name : Angela Johnston
Phone: (134) 382 2457
````