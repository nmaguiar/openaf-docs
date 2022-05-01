---
layout: default
title: Using a filter map
parent: Advanced
grand_parent: Guides
---

# Using a filter map

_version: >= 20220422_

It's a common OpenAF practice to use the _$from_ construct to build queries around arrays:

````javascript
// Querying files (excluding folders) and get a list of filenames sorted by size
var sortedList = $from( io.listFiles(".").files )
                 .equals("isFile", true)
                 .sort("-size")
                 .select({ filename: "n/a", size: - 1 })
````

It's a powerfull tool to declare queries to arrays but in advance cases (like nAttrMon and others) you might want to configure these queries from a YAML/JSON map. To make it easier you can use *ow.obj.filter*:

````yaml
init:
  myFilter:
    where:
    - cond: equals
      args:
      - isFile
      - true
    transform:
    - func: sort
      args:
      - "-size"
    select:
      canonicalPath: n/a
      size         : -1

todo:
- Run my filter

jobs:
- name : Run my filter
  check:
    in:
      path: isString.default(".")
  exec : |
    ow.loadObj()
    args.result = ow.obj.filter( io.listFiles(args.path).files, args.init.myFilter )

    ow.oJob.output(args.result, args)
````

In the above _ojob_ all the $from construct has been "outsourced" to the _myFilter_ map. Sure it seems a lot more than the simple OpenAF javascript code but it now allows it to be customized without any changes on the code and placed as part of any JSON/YAML map construct needed without having to expose the code itself directly.

> If needed the code can still control the _select_ map entry to ensure it gets the data needed

Running the above _ojob_ would return something similar to:

````bash
$ ojob test.yaml __format=table
>> [Run my filter] | 300511 | STARTED ──────────────────
        canonicalPath        │  size  
─────────────────────────────┼────────
/root/kubectl                │46931968
/root/.viminfo               │14695   
/root/.bash_history          │12950   
/root/.openaf-console_history│7695    
/root/test.md                │4864    
/root/.bashrc                │3106  

<< [Run my filter] | 300511 | SUCCESS ══════════════════
````

## Understanding ow.obj.filter map

The filter map is composed of the following sections:

| section   | $from correspondent |
|-----------|---------------------|
| where     | all the filtering functions like _equals_, _less_, _match_, _contains_, etc... It expects a _cond_ and then an array of _args_ |
| transform | all the transforming functions like _attach_, _sort_, etc... It expects a _func_ and then an array of _args_ |
| select    | a map or the code for a select function |
| selector  | all the selector functions like _at_, _min_, _max_, etc... It expects a _func_ and then an array of _args_ |

## In-map coding

If you really need to code functions in the map (should be discouraged) where are some examples:

Adding an _attach_ code:

````yaml
myFilter:
  // ...
  transform:
  - func: attach
    args:
    - lastAccess
    - !!js/eval elem => new Date(elem.lastAccess)
  - func: sort
    args:
    - lastAccess
  // ...
````

> In order to use "!!js/eval" in __YAMLFormat.unsafe flag must be true

Adding a _select_ code:

````yaml
myFilter:
  // ...
  select: |
    elem.id = sha256( stringify(elem, __, "") )

    return id
````
