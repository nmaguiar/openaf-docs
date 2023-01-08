---
layout: default
title: oJob
parent: oJob
grand_parent: Guides
---

# oJob

To enrich the oJob building blocks there is a set of jobs to help minimize coding (low-code). For this, the oPack ojob-common provides __ojob.yaml__. 

## What's provided

| Area | Job | Description |
|------|-----|-------------|
| Control | [ojob if](#ojob%20if) | If the provided "condition" is evaluated as true it will execute the "then" jobs otherwise it will execute the "else" jobs |
| Control | [ojob repeat](#ojob%20repeat) | Repeats sequentially, for a specific number of "times", the provided list of "jobs" (one or more) |
| Control | [ojob repeat with each](#ojob%20repeat%20with%20each) | Repeats the configured "jobs" (one or more jobs) sequentially for each element of the provided "key" list. |
| Debug | [ojob debug](#ojob%20debug) | Outputs the current args and res values to help debug an ojob flow. |
| Debug | [ojob job debug](#ojob%20job%20debug) | Provides an alternative to print based debug. |
| Function | [ojob function](#ojob%20function) | Executes the provided function mapping any args to the function arguments using the odoc help available for the provided function. |
| Input | [ojob get](#ojob%20get) | Retrieves a specific map key (or path) using $get | 
| Input | [ojob file get](#ojob%20file%20get) | Retrieves a specific map key (or path) from an YAML or JSON file provided. |
| Input | [ojob split to items](#ojob%20split%20to%20items) | Splits an args source into an array of maps. |
| Query | [ojob query](#ojob%20query) | Performs a query (using ow.obj.filter) to the existing args. | 
| Options | [ojob job](#ojob%20job) | Provides a way to organize idempotent jobs. |
| Options | [ojob job report](#ojob%20job%20report) | Outputs a job jobs report (e.g. job name, action and plan) |
| Options | [ojob job final report](#ojob%20job%20final%20report) | Outputs a job jobs report (e.g. job name, action and plan) upon ojob termination. |
| Options | [ojob options](#ojob%20options) | Adds new "todo" entries depending on the value of a provided args variable. | 
| Output | [ojob set](#ojob%20set) | Sets a "key" with the current value on a "path" using $set. |
| Output | [ojob set envs](#ojob%20set%20envs) | Sets job args based on environment variables. |
| Output | [ojob output](#ojob%20output) | Prints the current arguments to the console. |
| Report | [ojob report](#ojob%20report) | Outputs a jobs report (e.g. job name, status, number of executions, total time, avg time and last execution). |
| Report | [ojob final report](#ojob%20final%20report) | Outputs a jobs report (e.g. job name, status, number of executions, total time, avg time and last execution) upon ojob termination. |
| Security | [ojob sec get](#ojob%20sec%20get) | This job will get a SBucket secret and map it to oJob's args. |
| State | [ojob state](#ojob%20state) | Changes the current state depending on the value of a provided args variable. |
| State | [ojob get state](#ojob%20get%20state) | Gets the current state into args.state. |
| State | [ojob set state](#ojob%20set%20state) | Changes the current state. |

## How to start using it 

You can include it in different ways depending on the OpenAF version you are using.

For OpenAF version >= 20230103:

````yaml
ojob:
  includeOJob: true
````

For older OpenAF versions

````yaml
ojob:
  opacks:
    oJob-common: 20230103

include:
- ojob.yaml
````

or (requiring internet access)

````yaml
include:
- ojob.io/common/ojob
````

## Control

### ojob if

If the provided "condition" is evaluated as true it will execute the "then" jobs otherwise it will execute the "else" jobs

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__condition|no|An OpenAF code condition with templating functionality|
|__then|no|One job or a list of jobs to execute if the "condition" is true|
|__else|no|One job or a list of jobs to execute if the "condition" is false|
|__debug|no|Boolean to indicate if should log the original condition and the parsed condition for debug proposes|


### ojob repeat

Repeats sequentially, for a specific number of "times", the provided list of "jobs" (one or more)

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__times|no|The number of times to repeat the provided list of jobs|
|__jobs|no|One job or a list of jobs to execute each time|

### ojob repeat with each

Repeats the configured "jobs" (one or more jobs) sequentially for each element of the provided "key" list.

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__key|no|The key or path for an existing list in args|
|__jobs|no|One job or a list of jobs to execute each time|

## Debug

### ojob debug

Outputs the current args and res values to help debug an ojob flow.

### ojob job debug

Provides an alternative to print based debug.

Example:
````yaml
  # ----------------
  - name: Sample job
    exec: |
      //@ Declaring array
      var ar = [ 0, 1, 2, 3, 4, 5 ]

      //@ Start cycle
      var ii = 0;
      while(ii < ar.length) {
        print("II = " + ii)
        ii++
        //# ii == 3
      }
      //@ End cycle
      //? ii

      //?s args
      //?y args
````

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|job|no|The job to change to include debug|
|jobs|no|The jobs array to change to include debug|
|lineColor|no|The line color around the debug info|
|textColor|no|The text color around the debug info|
|theme|no|The withSideLineThemes theme to use|
|emoticons|no|If emoticons should be used or not|
|signs|no|A custom map of emoticons (keys: checkpoint, assert and print)|
|includeTime|no|A boolean value to indicate if a time indication should be included|

## Function

### ojob function

Executes the provided function mapping any args to the function arguments using the odoc help available for the provided function.
Note: accessing odoc might be slow on a first execution.

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__key|yes|The key string to retrieve previous results (defaults to 'res')|
|__fn|no|The function to execute|
|__path|no|If defined the args path for the function arguments to consider|
|__fnPath|no|If defined the args path where to set the function result|

## Input

### ojob get

Retrieves a specific map key (or path) using $get

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__key|no|Map key or path (key is also checked for compatibility)|

### ojob file get

Retrieves a specific map key (or path) from an YAML or JSON file provided.

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__file|yes|The file path to an YAML or JSON file|
|__key|no|Map key or path on the file contents|
|__cache|no|Boolean value that if false it won't cache the file contents (default: true)|
|__ttl|no|If cache is enabled lets you define a numeric ttl|
|__out|no|The path on args to set the map key/path contents|

### ojob split to items

Splits an args source into an array of maps (_list).

Example:
````
  a source string with the value "abc, xyz, 1"
  + separator = ','
  transforms into:

  - item: abc
  - item: xyz
  - item: 1
````

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|source|no|A object path to the string source to split|
|separator|no|The separator for the source string (defaults to \n)|

## Query 

### ojob query

Performs a query (using ow.obj.filter) to the existing args.

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__query|no|The query map for ow.obj.filter|
|__from|no|The path to the args key to perform the query|
|__to|no|The path to where the results should be stores|
|__key|no|If __from and __to not provided defaults to $get/$set on the provided key|

## Options

### ojob job

Provides a way to organize idempotent jobs. One or more "checks" jobs will be called to determine an args._action.
Initially the args._action is set to "none". If the "checks" jobs determine an action it will call the corresponding
jobs on "actions" jobs. If "_go=true" is not provided, instead of running, it will only return a plan of actions. 
For example:

````yaml
  - name: Write Hello World
    to  : ojob job
    args:
      _checks : Check Hello World
      _actions:
        create   : Create Hello World
        overwrite: Overwrite Hello World
        delete   : Delete Hello World
````

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|_checks|no|A list of one or more jobs to be called to perform checks to determine an args._action|
|_actions|no|A map of possible values of args._action whose values are one or more jobs to execute|
|_go|no|A boolean value (defaults to false) that controls if the _actions jobs are called (when true) or not|

### ojob job report

Outputs a job jobs report (e.g. job name, action and plan)

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__format|no|Can be json, yaml, table (default) or any other ow.oJob.output format|

### ojob job final report

Outputs a job jobs report (e.g. job name, action and plan) upon ojob termination

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__format|no|Can be json, yaml, table (default) or any other ow.oJob.output format|

### ojob options

Adds new "todo" entries depending on the value of a provided args variable.

Example:

  __optionOn : mode
  __lowerCase: true
  __todos    :
    mode1:
    - Job 1
    - Job 2
    mode2:
    - Job 2
    - Job 3
  __default:
  - Job 2


__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__optionOn|yes|The variable in args that will define which set of "todo"s will be added (trimmed)|
|__lowerCase|no|Boolean value to determine if should compare the optionOn in lower case (defaults to false)|
|__upperCase|no|Boolean value to determine if should compare the optionOn in upper case (defaults to false)|
|__todos|yes|Map where each option value should have a list/array of "todo"s|
|__default|no|Default array of "todo"s|
|__async|no|Boolean value that if true, run the todos in async mode|

## Output

### ojob set

Sets a "key" with the current value on a "path" using $set

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__key|no|Map key|
|__path|no|A key or path to a value from the current args|

### ojob set envs

Sets job args based on environment variables.

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|envs|no|A map where each key corresponds to an environment variable and the value to the args path where it should be placed|

### ojob output

Prints the current arguments to the console.

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__key|no|The key string to retrieve previous results (defaults to 'res')|
|__path|no|A path string to a map/array over the results set on key.|
|__format|no|The output format (e.g. see ow.oJob.output help)|
|__title|no|Encapsulates the output map/array with a title key.|
|__internal|no|Boolean value that if true it will display the internal oJob entries on the arguments (default false)|

## Report

### ojob report

Outputs a jobs report (e.g. job name, status, number of executions, total time, avg time and last execution)

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__format|no|Can be json, yaml, table (default) or any other ow.oJob.output format|

### ojob final report

Outputs a jobs report (e.g. job name, status, number of executions, total time, avg time and last execution) upon ojob termination

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__format|no|Can be json, yaml, table (default) or any other ow.oJob.output format|

## Security

### ojob sec get

This job will get a SBucket secret and map it to oJob's args

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|secIn|no|The args path where all the remaining sec arguments should be read from (defaults to no path)|
|[secIn].secOut|no|The args path to be mapped with the secret (defaults to secIn)|
|[secIn].secKey|no|The SBucket key|
|[secIn].secRepo|no|The SBucket repository|
|[secIn].secBucket|no|The SBucket name|
|[secIn].secPass|no|The SBucket password|
|[secIn].secMainPass|no|The SBucket repository password|
|[secIn].secFile|no|Optional provide a specific sbucket file|
|[secIn].secDontAsk|no|Determine if passwords should be asked from the user (default=false)|
|[secIn].secIgnore|no|If true will ignore errors of sec parameters not being provided (default=false)|

__Returns:__

| name | required? | description |
|------|-----------|-------------|
|[secIn].[secOut]|no|The args path to be mapped with the secret (defaults to secIn)|

## State

### ojob state 

Changes the current state depending on the value of a provided args variable.

  Example:

    stateOn  : mode
    lowerCase: true
    default  : Help


__Expects:__

| name | required? | description |
|------|-----------|-------------|
|stateOn|no|The variable in args that will define the current global set (to execute todo.when)|
|lowerCase|no|A boolean value to determine if should compare the stateOn in lower case (defaults to false)|
|upperCase|no|A boolean value to determine if should compare the stateOn in upper case (defaults to false)|
|validStates|no|An array of valid states to change to. If not included the default will be choosen (or none).|
|default|no|Default value of state|

### ojob get state

Gets the current state into args.state.

__Returns:__

| name | required? | description |
|------|-----------|-------------|
|state|no|The current state|

### ojob set state

Changes the current state.

__Expects:__

| name | required? | description |
|------|-----------|-------------|
|__state|no|The state to change to (to execute todo.when)|