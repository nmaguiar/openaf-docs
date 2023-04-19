---
layout: default
title: $cache
parent: Concepts
grand_parent: OpenAF docs
---
# $cache

Whenever you have multiple concurrent needs to access specific data you might end up in the a bad pattern of having several parts of the code trying to retrieve the same data generating multiple requests and/or slowing down the entire code. 
An obvious way to solve this is by caching the data so other concurrent needs for the same data will use an internal copy of it.

In OpenAF the function "$cache" facilitates the creation and the use of data caches.

## Creating a cache

To create a cache you need to determine:
* The cache name
* A function that given a key will retrieve the necessary data whenever needed
* If the data has any TTL (Time To Live) period after which the cost of using a copy of the data becomes bigger than the cost of retrieving it again to ensure its update OR if there is only an initial cost (in which case there isn't a need to define a TTL)

### A TTL example

As an example you might need to retrieve the listing of files, through a remote SSH connection, for a specific remote path. We will call it "remotelist"; we will define a function that given a remote path retrieves the list of files; and we will assume that the cost of performing the remote listing outweighs the benefits of keeping a copy after 5 seconds:

````javascript
$cache("remotelist")
.ttl(5000)
.fn(aPath => {
  var remoteList = $ssh(connectionDetails).listFiles(aPath)
  return remoteList
})
.create()
````

### A non-TTL example

As a non-TTL example we might need to call an external REST service that provide us the weather for a specific location for the next couple of days. Since the OpenAF script will always end in minutes and the weather forecast won't change for 24 hours we can assume there is no need to retrieve the data ever again during the OpenAF script execution:

````javascript
$cache("weather")
.fn(aLocation => $rest({ uriQuery: true }).get("https://a.weather.service", { loc: aLocation }))
.create()
````

> You can create a cache with a dummy key if the data you are retrieving doesn't require a specific key.

## Using a cache

Now that we have created the necessary caches when can use them directly in any other point of the OpenAF code:

````javascript
var inputFilesList = $cache("remotelist").get("/input/folder/path")
var outputFilesList = $cache("remotelist").get("/output/folder/path")
````

> In the "remoteList" cache example the first call will retrieve the list of files and any other subsequent calls will use the same data for the next 5 seconds. After 5 seconds have passed since the end of the first call, the next first call will actually result in calling the function to retrieve data again. There is a lock mechanism to ensure that only one call will execute and the others will use the cached results.

````javascript
var weatherInLondon = $cache("weather").get("London-UK")
var weatherInParis = $cache("weather").get("Paris-France")
````

## Deleting a cache

By default the cached data is kept in memory for performance reasons. If that data is no longer needed it's a good practice to delete the corresponding cache to free up the used memory:

````javascript
$cache("remotelist").destroy()
$cache("weather").destroy()
````

## Restricting the memory utilization

In some case you might not know how many cache keys will be used and thus potentially having the issue of entirely filling up the memory used by the cache. To avoid those situations you can limit the number of keys in memory.

For example, let's limit the of remote path listings to 2 and the number of weather forecasts to only 5 locations:

````javascript
$cache("remotelist")
.ttl(5000)
.maxSize(2)
.fn(aPath => {
  var remoteList = $ssh(connectionDetails).listFiles(aPath)
  return remoteList
})
.create()

$cache("weather")
.maxSize(5)
.fn(aLocation => $rest({ uriQuery: true }).get("https://a.weather.service", { loc: aLocation }))
.create()
````

> Whenever the limit of *maxSize* is reached the oldest data associated with a key will be deleted and the new one retrieved.

## Persisting a cache

Sometimes you might want the cache to "survive" multiple OpenAF script executions. A solution for this is to persist the cache data into a file. Any TTL and max size settings that you defined previously will be kept and honored whenever use in other script executions.

````javascript
$cache("weather")
.inFile("weatherForecast.cache")
.ttl(12 * 60 * 60000)
.maxSize(5)
.fn(aLocation => $rest({ uriQuery: true }).get("https://a.weather.service", { loc: aLocation }))
.create()
````

In this example whenever a weather forecast is retrieved it will be stored also in the file "weatherForecast.cache". In subsequent executions, within a 12 hours period, if the same weather forecast is requested and there isn't more than 5 location forecasts in cache the data will be retrieved from the local file directly.

> The default implementation is to use a [MVS](OpenAF-Channels.md#mvs) (H2 MVStore) file. If you want to share cache data across multiple scripts and potentially in different hosts you should use a different implementation. Check the ["Advance considerations"](#advance-considerations) section.

## Advance considerations

The *$cache* function is actually a wrapper around an [OpenAF channel](OpenAF-Channels.md) which by default is the "simple" type and for persisting is the "mvs" type. This means that it's possible to use any of the other types to build a specific cache. 

For example, you can have a JSON file based cache using the "file" type:

````javascript
$ch("cacheFile").create("file", { file: "cacheData.json" })

$cache("weather")
.ch("cacheFile")
.ttl(12 * 60 * 60000)
.maxSize(5)
.fn(aLocation => $rest({ uriQuery: true }).get("https://a.weather.service", { loc: aLocation }))
.create()
````

It also means you can built a common cache across multiple scripts via network:

Script A
````javascript
$ch("cacheData").create()
$ch("cacheData").peer(12345, "/cacheData", [ "http://script.b:12346/cacheData" ])

$cache("weather")
.ch("cacheFile")
.ttl(12 * 60 * 60000)
.maxSize(5)
.fn(aLocation => $rest({ uriQuery: true }).get("https://a.weather.service", { loc: aLocation }))
.create()

// First call to get the weather forecast in London
$cache("weather").get("London-UK")
````

Script B
````javascript
// Same code as Script A just changing the peering data
$ch("cacheData").create()
$ch("cacheData").peer(12346, "/cacheData", [ "http://script.a:12345/cacheData" ])

$cache("weather")
.ch("cacheFile")
.ttl(12 * 60 * 60000)
.maxSize(5)
.fn(aLocation => $rest({ uriQuery: true }).get("https://a.weather.service", { loc: aLocation }))
.create()

// Second call to get the weather forecase in London that will get the cached result from Script A
$cache("weather").get("London-UK")
````