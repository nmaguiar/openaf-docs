---
layout: default
title: Validate an YAML file
parent: oJobIO
grand_parent: Guides
---

# Validate an YAML file

With YAML files being used for more and more cases everyday it becomes usefull to validate them after any change. Sure modern editors do that but you might edit in a remote server through vi or another UNIX tool and you just want to quickly validate it.

## Simple validation

To do it just execute:

```bash
ojob ojob.io/langs/yaml file=/my/yamlFile.yaml
```

As you result you will get an "ok":

```
╭ result : ok 
╰ message:  
```

or an error:

```
╭ result : not ok 
╰ message: YAMLException: bad indentation of a sequence entry (3:2)
           
            1 | jobs:
            2 | - name: ok
            3 |  - name: not ok
           ------^
            4 | - name: list
            5 |   exec: | 
```

## Parsing contents

Besides checking for syntax you can also try to parse the data and verify the contents on the parsed output:

```
╭ result : ok 
├ message:  
╰ parsed  ─ jobs ╭ [0] ─ name: ok 
                 ├ [1] ─ name: not ok 
                 ╰ [2] ╭ name: list 
                       ╰ exec: some text here
```

This way you can check if the YAML data output is also what you intended it to be.