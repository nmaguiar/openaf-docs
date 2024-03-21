---
layout: default
title: Quickly validate a YAML file
parent: OneLiner
grand_parent: Guides
---

# Quickly validate a YAML file

One of the cons of using YAML (e.g. and any other identation based languages) is forgetting about a tab or a wrong spacing that leads to errors. For example:

````yaml
jobs:
  #-------------------
  - name: Hello World!
  exec: print('Hello World!')

todo:
  - Hello World!
````

The problem with this YAML file is on the 4th line since the 3rd line started a map as part of the jobs array but the 4th line is a map entry. One way to quickly check this is using another "one-liner":

````bash
$ oaf -c "io.readFileYAML('aYAMLFile.yaml')"
````

In this case the result would be:

````bash
Error while executing operation: YAMLException: bad indentation of a mapping entry at line 4, column 3:
      exec: print('Hello World!')
      ^ (js-yaml_js#1)
````

Solving the issue:

````yaml
jobs:
  #-------------------
  - name: Hello World!
    exec: print('Hello World!')

todo:
  - Hello World!
````

Executing the same one-liner now the result is no errors:

````bash
$ oaf -c "io.readFileYAML('aYAMLFile.yaml')"
$
````
