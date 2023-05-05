---
layout: default
title: Accessing $get/$set in Python code blocks
parent: Medium
grand_parent: Guides
---

# Accessing $get/$set in Python code blocks

In oJob one of the methods to share data across multiple jobs is to use the functions _$get_ and _$set_. But when running a Python code block, before OpenAF version 20230325, the only way was to use a previous job to map data into the current _args_.

Starting on OpenAF version 20230325 it's possible to use two new functions made available in Python code blocks.

## Example using Python function _g

If a previous job sets the key "test" with a map you can use __g_ to retrieve the value:

````yaml
# --------------------
- name : Set test data
  to   : ojob set
  args :
    data  :
      x: 1
      y: -1
    __key : test
    __path: data

# ------------------------
- name : Test _g in python
  from : Set test data
  lang : python
  exec : |
    data = _g('test')
    print("X = " + str(data['x']))
    print("Y = " + str(data['y']))
````

This will result that the Python code will print:

````
X = 1
Y = -1


````

## Example using Python function _s

If a python job sets the key "test" with a dictionary another OpenAF block can retrieve the value using _$get_:

````yaml
# ------------------------
- name : Test _s in python
  to   : Show test data
  lang : python
  exec : |
    test = {}
    test['x'] = 1
    test['y'] = -1
    _s('test', test)

# ---------------------
- name : Show test data
  exec : |
    var data = $get("test")
    print("x = " + data.x)
    print("y = " + data.y)
````

This will result that the OpenAF code will print:

````
x = 1
y = -1

````