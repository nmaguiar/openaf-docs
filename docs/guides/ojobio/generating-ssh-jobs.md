---
layout: default
title: Generating SSH oJobs
parent: oJobIO
grand_parent: Guides
---

# Generating SSH oJobs

oJobs are not only restricted to OpenAF's javascript or shell script. They can actually handle [multiple languages](../medium/running-different-ojob-langs.md). One of the bundled languages is **ssh**. 

The **ssh** oJob's job language allows you to define jobs that execute shell scripts in other hosts acesssible through SSH. Given the oJob features of being able to run jobs in parallel, declaring dependencies between them, modularity, etc... allows you to build, on a simple YAML oJob definition, complex multi-target actions. For example: 

* being able to execute a shell script template in multiple hosts at the same time
* gathering the results of running multiple commands in multiple hosts

## Getting started

To get started quickly simple execute:

````bash
$ ojob ojob.io/ojob/templates/ssh num=3 > example.yaml
````

This will generate an _example.yaml_ ready for you change and execute commands in three hosts.

> You can change the number of hosts at any time, read the hosts from another file or even implement dynamic logic (using an API, for example) to determine the current list of hosts

## Changing the generated oJob

On the begining of the file you have a fix list to get started. You can use YAML's achors, as generated, to make it easier and faster to build these lists. Basically each list entry needs:

| Entry | Comment | 
|-------|---------|
| name | Just an unique name to identify the target for easier identification on logs. |
| host | The hostname or IP address of the target. |
| port | The SSH port (e.g. usually 22). |
| login | The SSH login to use. | 
| pass | The SSH password to use or the private SSH identification certificate password (can be in encrypted form). |
| id | The file path to a private SSH identifcation certificate password. |
| timeout | The connection timeout in ms. |

````yaml
# The password will be asked and set for all. To disable and provide no password or a specific password
# for each: (1) uncomment "pass:"; (2) comment "Ask pass" in the todo section;
#
list: &LIST
- ssh:
    name   : Host A
    host   : 1.2.3.4
    port   : &PORT 22
    login  : &LOGIN aLogin
    #pass   : &PASS theLoginOrKeyPasswordEncrypted
    id     : &ID /path/to/private_key.id
    timeout: &TIMEOUT 2500
- ssh:
    name   : Host B
    host   : 1.2.3.5
    port   : *PORT
    login  : *LOGIN
    #pass   : *PASS
    id     : *ID
    timeout: *TIMEOUT
# [...]
````

## Asking for the password

If a password is not defined it will be interactively asked through the "Ask pass" job:

````yaml
todo:
- Ask pass
- Run commands
````

## Connectivity check

Included in the template there is a specific job, "Check connectivity", to use the *host* and *port* to understand if the target is network reachable:

````yaml
# ------------------------
- name: Check connectivity
  exec: |
    ow.loadNet()
    var _r = ow.net.testPort(args.ssh.host, args.ssh.port)
    if (!_r) throw templify("Cannot connect to : ()!", args)
````

## The commands to execute

Finally, the commands to execute in each host in the "Run commands" job. Since the *args* is a list of entries the job will automatically run in parallel. The *typeArgs.shellPrefix* determines what will be used to identify the logs lines for each target execution:

````yaml
# ----------------------
- name    : Run commands
  from    :
  - Set pass
  - Check connectivity
  lang    : ssh
  typeArgs:
    shellPrefix: ssh.name
  args    : *LIST
  exec    : |
    # write here any sh commands you need like it was a shell script
    #
    id
````

> To avoid running in parallel simply add typeArgs.single to *true*.

````
▷ [Ask pass] | 77496 | STARTED ─────────────────────────────────────────────────────── 2023-06-03 12:05:07.626
✓ Password: [---]

✓ [Ask pass] | 77496 | SUCCESS ═══════════════════════════════════════════════════════ 2023-06-03 12:05:10.178
▷ [Run commands] | 77496 | STARTED ─────────────────────────────────────────────────── 2023-06-03 12:05:10.196
[Host B] Darwin b.host 22.5.0 Darwin Kernel Version 22.5.0: Mon Apr 24 20:51:50 PDT 2023; root:xnu-8796.121.2~5/RELEASE_X86_64 x86_64
[Host C] Linux c.host 4.19.0-23-amd64 #1 SMP Debian 4.19.269-1 (2022-12-20) x86_64 GNU/Linux
[Host A] Linux a.host 5.4.0-74-generic #83-Ubuntu SMP Sat May 8 02:35:39 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

✓ [Run commands] | 77496 | SUCCESS ═══════════════════════════════════════════════════ 2023-06-03 12:05:11.842
````