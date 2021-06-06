---
layout: default
title: oJob SSH Basics
parent: Beginner
grand_parent: Guides
---

# oJob SSH Basics

As part of the OpenAF series of oPacks there is one called [oJob-common](https://github.com/OpenAF/oJob-common) which provides common building blocks to make some tasks easier in oJobs.

One of those tasks is handling SSH operations ([oJobSSH](https://github.com/OpenAF/oJob-common#ojobssh)). For example: sending a file to a remote host, receiving a file or executing commands.

To include in your oJob simple add:

````yaml
include:
- oJobSSH.yaml
````

Additionally, to make sure the oJob-common oPack is installed you can also the following entry to the _ojob_ entry:

````yaml
include:
- oJobSSH.yaml

ojob:
  opacks:
  - oJob-common
````

## Providing credentials

When providing the SSH credentials to run the specific operations you can provide it directly, through [OpenAF SBuckets](../../concepts/sBuckets.md) or through an external list. 

The following provides different examples of how to execute _"uname -a"_ in a remote host.

### Directly

To provide the credentials directly:

````yaml
include:
- oJobSSH.yaml

ojob:
  opacks:
  - oJob-common

todo:
- name: Run uname
  args:
    host : 1.2.3.4
    port : 22
    login: somelogin
    pass : somepass   # this password can be encrypted

jobs:
# ---------------
- name: Run uname
  to  : SSH Exec
  args:
    cmd: uname -a
````

As you can see the credentials are passed on the _todo_ arguments and the command is generically placed on the specific _job_ definition arguments.

As always, if instead of providing a single map entry you provided an array the _Run uname_ job will be executed in parallel for each entry.

### External list

In the previous example we saw how a single entry or several can be provided. If you need to have a list of remote hosts the better solution becomes building an external file with that list:

**list.yaml**
````yaml
- name : my host 1
  host : host1.local
  login: user1
  pass : pass1234
  key  : key.rsa

- name : my host 2
  host : host2.local
  login: user1
  pass : pass1234
  key  : |
    -----BEGIN RSA PRIVATE KEY-----
    abc123xyz...
    -----END RSA PRIVATE KEY-----
````

> Note: when you provide a private _key_ (either an external file or the entire text) the _pass_ entry will refer to the private key password if necessary.

````yaml
include:
- oJobSSH.yaml

ojob:
  opacks:
  - oJob-common

todo:
# Loads from the list.yaml file into an internal myhosts OpenAF channel
- name: SSH Load hosts
  args:
    chHosts: myhosts
    file   : list.yaml

# Executes the uname command but using "myhosts" for credentials
- name: Run uname
  args:
    chHosts: myhosts

jobs:
# ---------------
- name: Run uname
  to  : SSH Exec
  args:
    cmd: uname -a
````

### SBuckets

An even more secure way is to use [OpenAF SBuckets](../../concepts/sBuckets.md) which is provided generically by the _oJobBasics.yaml_ included in the same _oJob-common_ oPack.

You can use in a similar fashion to the "External List" and "Directly", previsouly described, but just mentioning the _secKey_, _secBucket_ and _secPass_ (optionally you can also provide _secRepo_ and _secMainPass_ if you want to load from a different SBucket repository)

````yaml
init:
  sec: &SEC
    secBucket: hosts
    secPass  : ...    # should be encrypted

include:
- oJobBasics.yaml
- oJobSSH.yaml

ojob:
  opacks:
  - oJob-common

todo:
# Executes the uname command but the SBucket arguments
- name: Run uname
  args: *SEC

jobs:
# ---------------
# the from "oJob Sec Get" will pick up the SBucket arguments and provided the "SSH Exec" in this case
- name: Run uname
  from: oJob Sec Get
  to  : SSH Exec
  args:
    cmd: uname -a
````

## Copy a file to a remote host

For copying a file you can use the _SSH Send file_:

````yaml
jobs:
# --------------------
- name: Send myzip.zip
  to  : SSH Send file
  args:
    source: /my/local/Path/myzip.zip
    target: /my/remote/Path/myzip.zip
````

## Copy a remote host file to the local filesytem

For copying a remote file you can use the _SSH Get file_:

````yaml
jobs:
# -------------------
- name: Get myzip.zip
  to  : SSH Get file
  args:
    source: /my/remote/Path/myzip.zip
    target: /my/local/Path/myzip.zip
````

## Executing remote commands

### Single and multiple remote commands:

You can execute a single command:

````yaml
jobs:
# -------------------
- name: Execute uname
  to  : SSH Exec
  args:
    cmd: uname -a
````

or multiple:

````yaml
jobs:
# -------------------
- name: Execute uname
  to  : SSH Exec
  args:
    cmd:
    - echo -- [You are in `pwd`] -------------

    - >-
      echo -- [Previous directory] ----------- &&
      cd .. &&
      ls -1

    - >-
      echo -- [Current directory] ------------ &&
      cd . &&
      ls -1
````

### Passing values to other jobs

````yaml
include:
- oJobSSH.yaml

ojob:
  opacks:
  - oJob-common
  
todo:
- name: Get public IP and show it
  args:
  # a list of hosts to get the public IP

jobs:
# -------------------------------
- name: Get public IP and show it
  to  :
  - Get public IP
  - Show it

# -------------------
- name: Get public IP
  to  : SSH Exec
  args:
    # Quite disables the output of content and makes it available in args between jobs
    quiet: true
    cmd  : |
      curl https://ifconfig.co/json

# -------------
- name: Show it
  exec: |
    // args.exitcode provides the exit code of the remote command
    if (args.exitcode == 0) {
      // args.stdout the corresponding stdout
      print("Public IP: " + jsonParse(args.stdout).ip);
    } else {
      // args.stderr the corresponding stderr
      printErr(args.stderr);
    }
````