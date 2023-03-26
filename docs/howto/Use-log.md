---
layout: default
title: How To - Use log functions
parent: How To
grand_parent: OpenAF docs
---
# How to - Use log functions

Most OpenAF code needs somehow to log it's activity. The usual obvious choice is to use the _print_ functions but once you start logging production code the requirements usually go beyond just simply outputing a string to the console/_stdout_.

To encapsule this extra functionality and, at the same time, keep the simplicity of the _print_ functions OpenAF provides the _log_ functions:

| Function | Quick description |
|----------|-------------------|
| log(msg, options) | Logs the _mgs_ as a normal information (INFO) message. One-time options can also be provided. |
| logErr(msg, options) | Logs the _mgs_ as an error (ERROR) message. One-time options can also be provided. |
| logWarn(msg, options) | Logs the _mgs_ as a warning (WARN) message. One-time options can also be provided. |
| lognl(msg, options) | Same as the _log_ function but won't end with a new-line. |

Examples:

````javascript
log("This is a test") 
// 2020-01-02 12:13:14.567 | INFO | This is a test
logErr("Hups! There was an error!") 
// 2020-01-02 12:13:16.765 | ERROR | Hups! There was an error!
logWarn("Be careful...") 
// 2020-01-02 12:13:18.555 | WARN | Be careful...
````

As you might have noticed, for simplicity, there are 3 main loggging levels: INFO, ERROR and WARN. 

## Template-based log functions

Equivalent to the _log*_ functions OpenAF also provides template-based (using the ow.template internal library) equivalent functions:

| Function |
|----------|
| tlog(msg, data, options) |
| tlogErr(msg, data, options) |
| tlogWarn(msg, data, options) |
| tlognl(msg, data, options) |

The main difference is the extra _data_ map-type parameter. This should be a map with the data to be used on the provided template on the _msg_ parameter.

Simple example:

````javascript
{% raw %}
tlog("The current version is: {{version}}", { version: getVersion() })
// 2020-01-03 13:14:15.678 | INFO | The current version is: 20200102
{% endraw %}
````

If no _data_ map is provided the current scope will be used:

````javascript
{% raw %}
var distribution = getDistribution()
tlog("The current distribution is: {{distribution}}")
// 2020-01-03 13:14:17.876 | INFO | The current distribution is: nightly
{% endraw %}
````

## Log functions options

As described previously each _log_ function can have one-time options provided but you can also change the current settings used using the function _setLog(aOptionsMap)_. 

The options available are:

| Option | Type | Default | Description |
|--------|------|---------| -------------| 
| off | boolean | false | If true no stdout/stderr output attempt will be executed |
| offInfo | boolean | false | If true all INFO type messages won't be output. |
| offError | boolean | false | If true all ERROR type messages won't be output. |
| offWarn | boolean | false | If true all WARN type messages won't be output. |
| dateFormat | string | "yyyy-MM-dd HH:mm:ss.SSS" | This a _ow.format.fromDate_ date format to be used. |
| dateTZ | string | | The time zone to use (refer to _ow.format.fromDate_). If not defined it will use the current Java  |
| separator | string | "\|" | The log fields separator to use (when using the default "human" format) |
| async | boolean | true | If _false_ logging will stop the execution to output the log message. |
| asyncLevel | number | 3 | When _async_ is _true_ the _asyncLevel_ determines the maximum number of queued log messages for logging. When the maximum number is reached the current execution will wait for log execution until the queued level is re-established. | 
| profile | boolean | false | Whenever a log message is captured the current Java memory and system load stats will also be gathered. | 
| format | string | "human" | This allows to change the stdout/stderr output format to other alternatives (e.g. json, slon) |

Example setting global options:

````javascript
setLog({ offInfo: true })
logWarn("The INFO messages are off")
// 2020-01-01 12:13:14.567 | WARN | The INFO messages are off
log("this is just a info message")
setLog({ offInfo: false })
logWarn("The INFO messages are now on")
// 2020-01-01 12:13:14.678 | WARN | The INFO messages are now on
log("this is just an info message")
// 2020-01-01 12:13:15.123 | INFO | this is just an info message
````

Example setting an on-time option:

````javascript
logWarn("POINT OF NO RETURN!", { async: false })
// 2020-01-02 12:13:14.123 | WARN | POINT OF NO RETURN!
````

## Logging to an OpenAF channel

It's also possible to configure OpenAF to log to an [OpenAF channel](/docs/concepts/OpenAF-Channels). This allows logging to fully use the OpenAF channels functionality including output to external targets like ElasticSearch and others.

To start the functionality you just need to use the function _startLog(anOpenAFChannelSubscribeFunction, keepItems)_. The numeric _keepItems_ argument (which defaults to 100) determines how many entries to keep internally (in memory) for the OpenAF channel functionality (if you specify -1 no life-cycle will be used).

The _anOpenAFChannelSubscribeFunction_ will receive a key and a value map for each logged entry:

__Key:__

| Field | Type | Description | 
|-------|------|-------------|
| n | number | Current system time in nanoseconds (_nowNano()_) |
| t | string | The logging level (e.g. INFO, WARN, ERROR) |

__Value:__

| Field | Type | Description |
|-------|------|-------------|
| n | number | Current system time in nanoseconds (_nowNano()_) |
| d | date | The javascript date |
| t | string | The logging level (e.g. INFO, WARN, ERROR) |
| m | string | The logged message |
| freeMem | number | (if the option _profile_ is _true_) the current Java free memory |
| totalMem | number | (if the option _profile_ is _true_) the current Java total memory |
| systemLoad | number | (if the option _profile_ is _true_) the current operating system load |

If there is a need to stop the output of log messages to an OpenAF channel you can simply execute the function _stopLog_.

Example:

````javascript
// Executes a custom function with the log data
startLog((aCh, aOp, aKey, aVal) => { if (aOp == "set") print(aVal.t + " --> " + aVal.m) })
// Turns off the standard stdout/stderr output
setLog({ off: true })
log("Script started")
// INFO --> Script started
// ...
log("Script ended")
// INFO --> Script ended
stopLog()
````

## Check also

* [How to log to files](/docs/guides/medium/logging-to-log-files) with automated compression of old files and life-cycle/house-keeping management. 