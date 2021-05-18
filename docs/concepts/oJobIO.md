---
layout: default
title: oJob.io
parent: Concepts
grand_parent: OpenAF docs
---

# oJob.io

oJob.io is a service providing easy-to-access OpenAF [oJobs](/docs/concepts/oJob) for frequent routines across several domains. With OpenAF installed you simply execute
"ojob" to a specific address and the oJob will be downloaded and executed with the arguments provided. You can check the source code in [GitHub](https://github.com/OpenAF/oJob.io) 
and/or even build your own local [ojob.io service](https://github.com/OpenAF/openaf-opacks/tree/master/oJobIO). To start simply execute:

````bash
$ ojob ojob.io
````

and follow the instructions. You also have extra documentation for each ojob.io through the [website](https://ojob.io).

## Examples:

If you need a quick HTTP server to browse through the current folder from another machine's browser:
````bash
$ ojob ojob.io/httpServers/EasyHTTPd port=12345 path=.
````

If you need a quick HTTPs server to browse through the current folder and eventually upload files from a browse using a self-signed 
SSL certificate generated for a short period of time.
````bash
$ ojob ojob.io/httpServers/uploadHTTPSd cn=myserver.local port=12345
````

oJob.io can also be piped. Let's build an Excel with all the current environment variables:
````bash
$ ojob ojob.io/pipe 0=ojob.io/envs 1=ojob.io/formats/toXLS
````

Let's say you wanna retrieve the same environment variables but on HTML

````bash
$ ojob ojob.io/pipe 0=ojob.io/envs 1=ojob.io/html
````

## Some of the basic ojob.io

| ojob.io | Description | Example |
|---------|-------------|---------|
| check   | Check the syntax of an existing oJob for syntax errors | ````ojob ojob.io/check job=myjob.yaml```` |
| doc     | Generates a markdown output based on the oJob help     | ````ojob ojob.io/doc job=myjob.yaml output=myjob.md```` |
| echo    | Debug ojob to output all arguments provided            | ````ojob ojob.io/echo hello=world```` |
| envs    | Outputs the current environment variables              | ````ojob ojob.io/envs```` |
| generate | Generates a prebuild oJob                             | ````ojob ojob.io/generate > myNewOJob.yaml```` |
| get     | Retrieves the code of ojob.io                          | ````ojob ojob.io/get job=ojob.io/envs > envs.yaml```` |
| help    | Downloads and returns the corresponding oJob help      | ````ojob ojob.io/help job=ojob.io/generate```` |
| html    | Tries to open a browser with the map/array HTML representation | ````ojob ojob.io/pipe 0=ojob.io/help 0.job=ojob.io/generate 1=ojob.io/html```` |
| map     | Selects only specific fields/keys from a map | ````ojob ojob.io/pipe 0=ojob.io/envs 1=map.yaml 1.fields=TEMP,TMP```` |
| pipe    | Pipes oJobs passing their output maps or lists between them | ````ojob ojob.io/pipe 0=ojob.io/news/bbc 1=ojob.io/map 1.fields=title,link 2=ojob.io/html```` |
