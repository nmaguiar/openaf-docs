---
layout: default
title: Example of using the LLM oJob shortcut
parent: oJob
grand_parent: Guides
---

# Example of using the LLM oJob shortcut

(OpenAF version >= 20240501)

Using the oJob's LLM shortcut it's possible to build oJobs that use external LLM models to provide results over gathered input data.

In this example we will prepare a of list the files, in a specific path. That list will then be sent, as context, to a LLM model to classify which files look like photos by their corresponding file extensions:

```yaml
todo:
- List files
- Analyze files for photos

jobs:
# ----------------
- name: List files
  to  :
  # Arguments for io.listFiles
  - (pass   ):
      aFilePath: .

  # Executing io.listFiles
  - (fn     ): io.listFiles

  # from the io.listFiles results query and transform to a filename list
  - (query  ): "sort_by(files[?isFile==`true`], &filename) | [].{ filename: filename } | { files: [] }"
    ((type )): path
    ((key  )): res
    ((toKey)): fileList

  # output the prepared list of files
  - (output ): fileList

# ------------------------------
- name: Analyze files for photos
  to  :
  # Give the prepared list of files to a LLM model for analysis
  # (assuming an OAFP_MODEL environment is set (e.g. "(type: ollama, model: '...', url: '...', temperature: 0, timeout: 900000)" ))
  - (llm      ): From the provided list of files add an extra booelan 'isImage' field to indicate which files, given their extension, are photos.
    ((context)): list of files
    ((inKey  )): fileList
    ((inPath )): files
    ((outPath)): result
    ((env    )): OAFP_MODEL
    ((debug  )): false

  # Display the LLM model result as a table
  - (output   ): args
    ((path   )): result.files
    ((format )): ctable
    
```

Executing this oJob you should be able to see a similar result to:

```bash
$ ojob example.yaml

      filename       │isImage
─────────────────────┼───────
.0.png               │true    
Dockerfile           │false  
LICENSE              │false   
Media 2.jpeg         │true   
Media.jpeg           │true   
README.md            │false   
a.class              │false  
a.csv                │false  
a.html               │false  
a.js                 │false  
a.json               │false  
a.md                 │false  
a.toml               │false  
a.xml                │false  
a.yaml               │false   
birthday.png         │true    
test.txt             │false  
test0.png            │true   
update.sh            │false   
[#19 rows]
```