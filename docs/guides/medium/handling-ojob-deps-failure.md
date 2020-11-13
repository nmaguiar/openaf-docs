---
layout: default
title: "Medium: Handling oJob deps failure"
parent: Guides
grand_parent: OpenAF docs
---

# Handling oJob deps failure

When executing an oJob each job can depend on the successfull execution of other jobs. That means that if a depending job fails the current job execution will fail or stall (if it's an _ojob.sequential = true_).

## Dependency timeout

If _ojob.sequential != true_ any failed job dependency will keep the oJob waiting for a successfull execution of the dependent job. You can avoid that using a dependency timeout:

````yaml
ojob:
  # timeout of 2500ms
  depsTimeout: 2500 
````

In this case whenever a job doesn't execute because another failed it will wait just the amount of specific _ms_ for another successfull execution. Otherwise it will terminate with an error indicating the a dependency timeout has occurred.

## Individual dependency

You can also execute code to decide what should be done if a dependent job fails when _ojob.sequential != true_:

````yaml
todo:
  - Init
  - Test 1
  - Test 2

jobs:
  #-----------
  - name: Init
    exec: |
      // Initialize error flag
      global.inError = false;

  #-------------
  - name: Test 1
    exec: |
      print("Test 1");
      // Throw an error if args.error is defined
      if (args.error) throw("Problem with test 1");

  #-------------
  - name: Test 2
    deps:
      - name  : Init
      - name  : Test 1
        onFail: |
          // if the dependent job fails, 
          // change the global error flag and proceed
          global.inError = true;
          return true;
    exec: |
      if (!global.inError)
        print("Test 2");
      else
        printErr("Can not execute Test 2");
````

In this example there are three jobs:
* **Init** - initializes a global inError flag.
* **Test 1** - generates an error if the _error_ argument is defined during this oJob execution.
* **Test 2** - depends on the _Init_ and _Test 1_ jobs. If _Test 1_ job fails it sets the global inError flag and proceeds with the execution that checks that same flag.

The _onFail_ entry on the list of dependencies for job _Test 2_ is actually the code of a function that receives three parameters:

* **args** - the current job arguments
* **job** - the current job definition
* **id** - the current job execution id

If this _onFail_ functions returns true the job execution will proceed. If it returns false the job execution stalls as it does by default.