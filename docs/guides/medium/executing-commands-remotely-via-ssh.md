---
layout: default
title: "Medium: Executing commands remotely via SSH"
parent: Guides
grand_parent: OpenAF docs
---

# Executing commands remotely via SSH

All the functionality to access SSH & SFTP is encapsulated within the OpenAF's SSH plugin. You can use it directly but it might be hard to keep up with methods and function parameters. On oJob definitions it's easy using the [oJob-common functionality](https://github.com/OpenAF/oJob-common#ojob-sh). Directly on OpenAF code to make it easy to use and read there is a shortcut: $ssh

The $ssh is a function that receives the details on how to access a host via SSH as a map. The returned object can then be used to chain command to be executed remotely and finally execute them returning an array of maps with the executions result. Let's check a simple example:

````javascript
$ssh({
   host: "some.host",
   login: "aUser",
   pass: "aPass"
})
.sh("id")
.get();
/*[
  {
    "stdout": "uid=12345(user) gid=500(users) groups=500(users)",
    "stderr": "",
    "exitcode": 0,
    "cmd": "id"
  }
]*/
````

Why is the _get_ function returning an array? Can a private key be used? What if the SSH server has  different port? How do I provide stdin contents? Let's take it into parts.

## Connection options

In the previous example we used host, login and pass but there are more possible options. Some of them have default values like port = 22. Here is the list (you can also check it out in openaf-console executing "_help $ssh.get_"):

  * *host* - The SSH host address
  * *port* - The SSH port (defaults to 22)
  * *login* - The login username (encrypted or not)
  * *id* - The filepath to a SSH identity key file
  * *pass* - The password of the login or the identity key
  * *timeout* - The connection timeout in ms
  * *compress* - A boolean determining if the connection should be compressed or not

It's also possible to write all these options in a single url:

`ssh://[login]:[pass]@[host]:[port]/[id]?timeout=[timeout]&compression=[compression`

## The execution function

The main execution function is "*sh*". This function receives a command as the first argument and a *stdin* as a second argument. They can be chained to a reasonable amount of calls that will be executed sequentially:

````javascript
$ssh("ssh://aUser:aPass@somehost")
.sh("cd /some/dir && ./start.sh")
.sh("perl", "print(123)")
.get();
````

_Note: despite being able to chain execution commands they are still "independent". Check in the example how you can change directory and then execute a command._

## Retrieve results

To execute the chained commands there are two options: "_get_" and "_exec_". "_get_" will pack all the executions into an array of maps, each map with the corresponding command execution _stdout_, _stderr_ and _exitcode_.  But the resulting map is only returned upon the end of the commands chain execution. Using "_.exec_" will still return the map on the end of the execution but any _stdout_ and _stderr_ output will be redirected to the scripts _stdout_ and _stderr_.

If you have several $ssh entries in your script executing remote commands that return a lot of lines you might need "line labels" to understand them. This can easily be achieve using the "_.cb_" function (callback):

````javascript
> ow.loadFormat();
> $ssh("ssh://aUser:aPass@somehost").cb(ow.format.streamSHPrefix("somehost")).sh("ls").exec()
/*
[somehost] Mail
[somehost] bin
[somehost] tmp
*/
````