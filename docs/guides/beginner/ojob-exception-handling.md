---
layout: default
title: oJob exception handling
parent: Beginner
grand_parent: Guides
---

# oJob exception handling

When you create an OpenAF's oJob each job runs independently and you are responsible for handling exceptions on each. 

But couldn't we have a global try/catch function for all jobs? Yes, you can add a function with _ojob.catch_.

## oJob throwing exceptions example

````yaml
todo:
  - Normal job
  - Bug job
  - Another Bug job

jobs:
  #-----------------
  - name: Normal job
    exec: |
      print("I'm a normal job.");

  #--------------
  - name: Bug job
    exec: |
      print("I'm a buggy job.");
      throw "BUG!";
  
  #----------------------
  - name: Another Bug job
    exec: |
      print("I'm another buggy job.");
      throw "BUG!";
````

This ojob has 3 jobs. _"Normal job"_ will execute without throwing any exceptions. But _"Bug job"_ and _"Another Bug job"_ will throw two exceptions when executed.

Executing you will see the three jobs executing with two of them failing. The entire oJob process will finish with exit code 0.

## oJob general exception example

````yaml
todo:
  - Normal job
  - Bug job
  - Another Bug job

ojob:
  catch: |
    var msg = "Error executing job '" + job.name + "'\n";
    msg += "\nArguments:\n" + stringify(args, void 0, "") + "\n";
    msg += "\nException:\n" + stringify(exception, void 0, "") + "\n";
    logErr(msg, { async: false });

    if (String(exception) == "BUG!") exit(1);

jobs:
  #-----------------
  - name: Normal job
    exec: |
      print("I'm a normal job.");

  #--------------
  - name: Bug job
    exec: |
      print("I'm a buggy job.");
      throw "BUG!";
  
  #----------------------
  - name: Another Bug job
    exec: |
      print("I'm another buggy job.");
      throw "BUG!";
````

This example is equal to the previous one but it adds _ojob.catch_. The _catch_ function receives several arguments:

| Argument | Type | Description |
|----------|------|-------------|
| args | Map | The current args map at the point of the exception. |
| job | Map | The job map where the exception occurred. |
| id | Number | If the job was executed within a specific sub-id. |
| deps | Map | A map of job dependencies. |
| exception | Exception | The exception itself. |

If the function returns __true__ the exception will be recorded as usual and the job will be registered has failed. If the function returns __false__ the exception will be ignored.

In this example the function will actually stop the entire oJob process with exit code 1.