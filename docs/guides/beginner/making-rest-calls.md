---
layout: default
title: "Beginner: Making REST service calls from OpenAF"
parent: Guides
grand_parent: OpenAF docs
---

# Making REST service calls from OpenAF

OpenAF includes several ways to make HTTP connections and retrieve data from them. An usually the most usefull connections are to services that expose some kind of REST API "talking" in JSON. To make it easy in OpenAF to make these calls and parse the corresponding output the shortcut _$rest_ was created.

## Simple examples

### GET 

Performing a simple REST GET operation:

````javascript
> $rest().get("https://ifconfig.co/json");
{
  "ip": "1.2.3.4",
  "country": "Ireland",
  "country_eu": true,
  "country_iso": "IE",
  "city": "Dublin",
  "hostname": "ec2-1-2-3-4.eu-west-1.compute.amazonaws.com",
  "latitude": 53.3338,
  "longitude": -6.2488,
  "asn": "AS16509",
  "asn_org": "Amazon.com, Inc."
}
````

The return is a parsed json object ready to use.

### POST

Performing a REST POST operation you can pass the JSON body directly (in this example the httpbin.org service will echo the post request made):

````javascript
> $rest().post("https://httpbin.org/post", { a: 1, b: "xyz", c: true }).json
{
  "a": 1,
  "b": "xyz",
  "c": true
}
````

### PUT

The same goes for the PUT verb.

````javascript
> $rest().put("https://httpbin.org/put", { a: 1, b: "xyz", c: true }).json
{
  "a": 1,
  "b": "xyz",
  "c": true
}
````

### PATCH

And the PATCH verb.

````javascript
> $rest().patch("https://httpbin.org/patch", { a: 1, b: "xyz", c: true }).json
{
  "a": 1,
  "b": "xyz",
  "c": true
}
````

### DELETE

Finally, the DELETE verb.

````javascript
> $rest().delete("https://httpbin.org/delete").json
null
````

## Passing resource/query elements

There are two ways:

1. Using the URI path (resource)

````javascript
// https://some.server/restAPI/category/abc/article/1234
$rest().get("https://some.server/restAPI", { category: "abc", article: 1234 });

$rest().post("https://some.server/restAPI", { 
    article: 1234, title: "My article" 
}, { category: "abc", article: 1234 });

$rest().put("https://some.server/restAPI", { 
    article: 1234, title: "My article updated" 
}, { category: "abc", article: 1234 });

$rest().delete("https://some.server/restAPI", { category: "abc", article: 1234 });
````

2. Using the query string

````javascript
// https://some.server/restAPI?category=abc&article=1234
$rest({ uriQuery: true }).get("https://some.server/restAPI", { category: "abc", article: 1234 });

$rest({ uriQuery: true }).post("https://some.server/restAPI", { 
    article: 1234, title: "My article" 
}, { category: "abc", article: 1234 });

$rest({ uriQuery: true }).put("https://some.server/restAPI", { 
    article: 1234, title: "My article updated" 
}, { category: "abc", article: 1234 });

$rest({ uriQuery: true }).delete("https://some.server/restAPI", { category: "abc", article: 1234 });
````

## What if the body is URL encoded?

When you need the request body to be _"application/x-www-form-urlencoded"_ and instead of _"application/json"_ you can use the option _urlEncode=true_.

````javascript
> $rest({ urlEncode: true }).post("https://httpbin.org/post", { a: 1, b: "xyz" }).form
{
  "a": "1",
  "b": "xyz"
}
````

This was a simple introduction to the _$rest_ shortcut. Check all the available options (e.g. authentication, timeout, exception control, etc&#46;&#46;&#46;) executing "help $rest.get" from an openaf-console.