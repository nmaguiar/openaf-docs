# oJob Check for stall

When running an oJob there might be situations that you want to ensure that the entire process won't enter into a stall (e.g. being stopped on a "dead-end" waiting for some service or lock or whatever).

In oJob there is actually a feature to allow you to ensure, no matter what, your oJob won't run pass a specific timeout or for a function to be executed to determine if the oJob is at a stall situation.

## Killing after x seconds

The easiest configuration is ensuring that there is a general timeout for the entire oJob:

````yaml
ojob:
  checkStall:
    # check for a stall every x seconds (default 60)
    everySeconds    : 1
    # kill the entire process after x seconds
    killAfterSeconds: 4

todo:
  - Test job

jobs:
  #---------------
  - name: Test job
    exec: |
      args.wait = _$(args.wait).default(5000);

      log("Waiting for " + args.wait + "ms...");
      sleep(args.wait, true);
      log("Done");
````

Executing this oJob you will get different results depending on the amount of time the "Test job" takes. It's configured to "kill it self" if it takes longer than 4 seconds and it will check for that every second (e.g. on real situations you should use the default of 60 seconds).

For 1,5 seconds:

````bash
$ ojob test.yaml wait=1500
>> [Test job] | STARTED | 2019-11-11T12:13:17.199Z------------------------
2019-11-11 12:13:17.230 | INFO | Waiting for 1500ms...
2019-11-11 12:13:18.736 | INFO | Done

<< [Test job] | Ended with SUCCESS | 2019-11-11T12:13:18.740Z ============
````

For 5 seconds:

````bash
$ ojob test.yaml wait=5000
>> [Test job] | STARTED | 2019-11-11T12:22:00.058Z -----------------------
2019-11-11 12:22:00.085 | INFO | Waiting for 5000ms...
oJob: Check stall over 4000
2019-11-11 12:22:03.878 | ERROR | oJob: Check stall over 4000
````

## Killing depending on a function

If you have certain conditions that can be easily checked to determine if the oJob is stalled you can use a function:

````yaml
ojob:
  checkStall:
    everySeconds    : 1
    checkFunc       : |
      print("checking for stall...");
      if (global.canDie) {
        print("should die.");
        return true;
      }

todo:
  - Init
  - Test job

jobs:
  #-----------
  - name: Init
    exec: |
      global.canDie = false;

  #---------------
  - name: Test job
    exec: |
      log("Waiting for 2500ms...");
      sleep(2500, true);

      log("Setting canDie to true...");
      global.canDie = true;

      log("Waiting for another 2500ms...");
      sleep(2500, true);

      log("Done");
````

In this case a global variable _canDie_ is only set to true after the first 2,5 seconds of execution of the _Test job_ job. As soon as the _checkFunc_ is executed and confirms the conditions by returning a _true_ value the oJob is immediatelly stopped.

````bash
$ ojob test2.yaml
checking for stall...
>> [Init] | STARTED | 2019-11-11T12:32:02.828Z -----------------------------
<< [Init] | Ended with SUCCESS | 2019-11-11T12:32:02.857Z ==================
>> [Test job] | STARTED | 2019-11-11T12:32:02.893Z -------------------------
2019-11-11 12:32:02.924 | INFO | Waiting for 2500ms...
checking for stall...
checking for stall...
2019-11-11 12:32:05.429 | INFO | Setting canDie to true...
2019-11-11 12:32:05.430 | INFO | Waiting for another 2500ms...
checking for stall...
should die.
````

You can see the several _checkFunc_ executions by the output "checking for stall..." and once the global variable _canDie_ was true all the oJob stopped it's execution.

## Checking at the job level

All the previous options checked for stall for the entire oJob execution but you can specify the same at the job level using _typeArgs.timeout_ and _typeArgs.stopWhen_ that are available for all types of jobs in oJob.

### Example with typeArgs.timeout

In this example the _Test job_ job is set to timeout after 1,5 seconds:

````yaml
todo:
  - Init
  - Test job
  - Done

jobs:
  #-----------
  - name: Init
    exec: |
      global.canDie = false;

  #-----------
  - name: Done
    exec: |
      log("Everything is done.");

  #-------------------
  - name    : Test job
    typeArgs:
      timeout: 1500
    exec    : |
      log("Waiting for 2500ms...");
      sleep(2500, true);

      log("Setting canDie to true...");
      global.canDie = true;

      log("Waiting for another 2500ms...");
      sleep(2500, true);

      log("Done");
````

Executing it the job will actually end in error after the specified timeout:

````bash
>> [Init] | STARTED | 2019-11-11T12:47:25.568Z ----------------------------
<< [Init] | Ended with SUCCESS | 2019-11-11T12:47:25.624Z =================
>> [Test job] | STARTED | 2019-11-11T12:47:25.662Z ------------------------
2019-11-11 12:47:25.684 | INFO | Waiting for 2500ms...

!! [Test job] | Ended in ERROR | 2019-11-11T12:47:27.197Z =================
- id: 8ebbf961-822d-3b95-ca09-8dfb335ab6cb
  error: Job exceeded timeout of 1500ms

===========================================================================
>> [Done] | STARTED | 2019-11-11T12:47:27.277Z ----------------------------
2019-11-11 12:47:27.297 | INFO | Everything is done.

<< [Done] | Ended with SUCCESS | 2019-11-11T12:47:27.300Z =================
````

### Example with typeArgs.stopWhen

In this example the _Test job_ job is set stop whenever the _stopWhen_ function returns a _true_ value:

````yaml
todo:
  - Init
  - Test job
  - Done

jobs:
  #-----------
  - name: Init
    exec: |
      global.canDie = false;

  #-----------
  - name: Done
    exec: |
      log("Everything is done.");

  #-------------------
  - name    : Test job
    typeArgs:
      stopWhen: |
        if (global.canDie) {
           print("should die...");
           return true;
        }
    exec    : |
      log("Waiting for 2500ms...");
      sleep(2500, true);

      log("Setting canDie to true...");
      global.canDie = true;

      log("Waiting for another 2500ms...");
      sleep(2500, true);

      log("Done");
````

Executing the job will actually stop without any error if the _stopWhen_ function returns the a _true_ value. To end the job with an error simply throw an exception on the _stopWhen_ function.

````bash
>> [Init] | STARTED | 2019-11-11T12:38:54.232Z -----------------------------
<< [Init] | Ended with SUCCESS | 2019-11-11T12:38:54.263Z ==================
>> [Test job] | STARTED | 2019-11-11T12:38:54.298Z -------------------------
2019-11-11 12:38:54.330 | INFO | Waiting for 2500ms...
2019-11-11 12:38:56.837 | INFO | Setting canDie to true...
should die...
2019-11-11 12:38:56.838 | INFO | Waiting for another 2500ms...

<< [Test job] | Ended with SUCCESS | 2019-11-11T12:38:56.857Z ==============
>> [Done] | STARTED | 2019-11-11T12:38:56.012Z =============================
2019-11-11 12:38:56.025 | INFO | Everything is done.

<< [Done] | Ended with SUCCESS | 2019-11-11T12:38:56.098Z ==================
````