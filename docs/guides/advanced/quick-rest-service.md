---
layout: default
title: "Advanced: Quickly build a REST service in OpenAF"
parent: Guides
grand_parent: OpenAF docs
---

# Quickly build a REST service in OpenAF

Whenever you need a REST service on a rush you can have a fully functional REST service with OpenAF in a couple of minutes. 

## 1. The function(s)

Let's start with a sample function in OpenAF that you need it to be available as a REST service:

````javascript
function addNumbers(inputMap) {
	inputMap   = _$(inputMap).isMap().default({});
	inputMap.a = _$(inputMap.a).default(0);
	inputMap.b = _$(inputMap.b).default(0);

	return {
		a: Number(inputMap.a),
		b: Number(inputMap.b),
		res: Number(inputMap.a) + Number(inputMap.b)
	}
}
````
_Advice: it's easier if it receives a map and returns a map._

Now save the _addNumbers_ function in _mylib.js_.

## 2. Install some helper oPacks

````bash
$ opack install ojob-common
$ opack install openaf-templates
````

## 3. Setup the main oJob

Copy the openaf-templates/ojobs/restServices/restServices.yaml to your current folder, together with _mylib.js_ from step 1, with the name _main.yaml_.

````bash
$ cp openaf-templates/ojobs/restServices/restServices.yaml main.yaml
````

Now let's edit the main.yaml:

1. Change the piddir line to _"piddir: &PIDDIR myService.pid"_
2. On the "Prepare my service" job change to something like this:
````yaml
  - name: Prepare my service
    to  : REST Service
    args: 
      uri       : /add     # That's your new URI
      port      : *PORT

      # Your code for the GET verb
      execGET   : |
        loadLib("mylib.js");
        return addNumbers(request.params);

      # Your code for the POST verb
      execPOST  : |
        loadLib("mylib.js");
        return addNumbers(data);
      execPUT   : "return { result: 0 }"
      execDELETE: "return { result: 0 }"
````

You can quickly test it by executing:

````bash
$ ojob main.yaml
````

Now, on your favourite REST client, execute something similar to:
````bash
$ curl "http://127.0.0.1:8090/add?a=5&b=5"
{"a":5,"b":5,"res":10}
$ curl -XPOST "http://127.0.0.1:8090/add" -d "{'a':1,'b':3}" -H "Content-Type: application/json"
{"a":1,"b":3,"res":4}
````

It's working!

## Let's docker it

Create a Dockerfile:

````dockerfile
FROM openaf/openaf-ojobc

COPY mylib.js /openaf/mylib.js
COPY main.yaml /openaf/main.yaml
````

Build it:

````bash
$ docker build . -t myservice
````

Start it:

````bash
$ docker run --rm -ti -p 8090:8090 myservice
````

Test it:

````bash
$ curl "http://127.0.0.1:8090/add?a=5&b=5"
{"a":5,"b":5,"res":10}
$ curl -XPOST "http://127.0.0.1:8090/add" -d "{'a':1,'b':3}" -H "Content-Type: application/json"
{"a":1,"b":3,"res":4}
````

It's that easy.