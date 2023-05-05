---
layout: default
title: How to access args in multiple languages
parent: oJob
grand_parent: Guides
---

# How to access args in multiple languages

In an oJob it's possible to use a mix of programming languages. In each you will probably want to access the args dictionary/map to perform different actions.

The following example uses the same _args.file_ to count the corresponding files' lines in Python, Perl, Shell script and OpenAF javascript and return the result in _args.lines_:

````yaml
todo:
- Init python to be fair
- Count lines in python
- Count lines in shell
- Count lines in js
- Count lines in perl
- ojob final report

ojob:
  includeOJob: true

jobs:
# -----------------------------
- name : Init python to be fair
  lang : python
  exec : |
    print("args = " + _d(args)) # dumps the current args

# ----------------------------
- name : Count lines in python
  to   : ojob output
  args : &OUTARGS
    __key : args
    __path: lines
  check: &CHECKFILE
    in:
      file: isString
  lang : python
  exec : |
    with open(args['file'], 'r') as f:
      lines = 0
      for line in f:
        lines += 1
      args['lines'] = lines

# ---------------------------
- name : Count lines in shell
  to   : ojob output
  args : *OUTARGS
  check: *CHECKFILE
  lang : shell
  exec : |
    echo "{ lines: `wc -l < {% raw %}{{file}}{% endraw %}` }"

# --------------------------
- name : Count lines in perl
  to   : ojob output
  args : *OUTARGS
  check: *CHECKFILE
  lang : perl
  exec : |
    open(my $fh, '<', '{% raw %}{{file}}{% endraw %}');
    my $count = 0;
    while (<$fh>) {
      $count++;
    }
    print "{ lines: $count }";

# ------------------------
- name : Count lines in js
  to   : ojob output
  args : *OUTARGS
  check: *CHECKFILE
  exec : |
    args.lines = io.readFileAsArray(args.file).length
````

Then to execute:

````
ojob myexample.yaml file=myexample.yaml
````

## OpenAF javascript

As expected the _args_ map is available as a Javascript map to used.

## Python

In oJob Python is a "first-class" language so after initializing it has the _args_ dictionary available for use in Python.

> the *_d()* function allows for converting any Python json or dictionary into the corresponding stringified version.

## Shell and Perl script

For non OpenAF/Python languages the _exec_ code is treated like an [OpenAF template](../cheat-sheet/templating.md) receiving the _args_ map. 

The output is parsed from a JSON output through _stdout_.