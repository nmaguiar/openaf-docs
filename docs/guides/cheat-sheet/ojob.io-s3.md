---
layout: default
title: ojob.io s3
parent: cheat-sheet
grand_parent: Guides
---

# ojob.io s3

The ojob.io/s3/ops allows you to perform quick S3 actions directly from the command-line without the need to install a specific S3 client if you already have OpenAF installed (uses the S3 oPack)

## Authentication

| Type | Example |
|------|---------|
| AWS S3 without credentials | ````ojob ojob.io/s3/ops region=eu-west-1```` |
| AWS S3 compatible with credentials | ````ojob ojob.io/s3/ops region=eu-west-1 accessKey=anAccessKey secret=anEncryptedSecret```` |
| Using OpenAF's SecBuckets | ````ojob ojob.io/s3/ops secBucket=default secKey=myS3```` |

> If you really need to use the credentials encrypt the secret first to avoid writing it in the console by executing: ````oaf -c 'print(askEncrypt())'````

### Basic setup of OpenAF's $sec:

Steps:

1. Setting up (just hit enter when asked for the sec bucket pass): ````ojob ojob.io/sec/ops op=setobj secobj=s3.s3 secbucket=default seckey=myS3````
2. Using: ````ojob ojob.io/s3/ops secBucket=default secKey=myS3````

> For more secure setups use a specific secBucket and password. See more in [OpenAF's Sec Buckets](../../concepts/sBuckets.md)

## Commands

Use the authentication fields replacing "..." in the examples.

| Command | Example | Comments |
|---------|---------|----------|
| lsbuckets | ````ojob ojob.io/s3/ops ... op=buckets```` | You can also use 'buckets' |
| mkbucket | ````ojob ojob.io/s3/ops ... op=mkbucket bucket=mynewbucket````| |
| rmbucket | ````ojob ojob.io/s3/ops ... op=rmbucket bucket=myoldbucket```` |  |
| ls | ````ojob ojob.io/s3/ops ... op=ls bucket=mybucket remote=my/folder/ recursive=true```` | In some cases you case also use full=yes for more details |
| put | ````ojob ojob.io/s3/ops ... op=put bucket=mybucket local=my/folder/file.txt remote=my/list/file.txt```` | |
| get | ````ojob ojob.io/s3/ops ... op=get bucket=mybucket remote=my/list/file.txt local=my/folder/file.txt```` | |
| mput | ````ojob ojob.io/s3/ops ... op=mput bucket=mybucket local=list remote=my/list```` | Supports windows-style wildcards |
| mget | ````ojob ojob.io/s3/ops ... op=mget bucket=mybucket remote=my/list local=list```` | Processes windows-style wilcards in your local memory |
| cp | ````ojob ojob.io/s3/ops ... op=cp sourceBucket=original targetBucket=target source=my/file.txt target=archive/file.txt```` | |
| mv | ````ojob ojob.io/s3/ops ... op=cp sourceBucket=original targetBucket=target source=my/file.txt target=archive/file.txt```` | Actually copies and deletes |
| rm | ````ojob ojob.io/s3/ops ... op=rm bucket=mybucket remote=my/list/file.txt```` |
| rmdir | ````ojob ojob.io/s3/ops ... op=rm bucket=mybucket remote=my/list/```` | Actually deletes all objects with the provided prefix on 'remote' |
| syncRemote | ````ojob ojob.io/s3/ops ... op=syncremote bucket=mybucket local=. remote=my/list go=true```` | For preview of actions use go=false |
| syncLocal | ````ojob ojob.io/s3/ops ... op=synclocal bucket=mybucket local=. remote=my/list go=true```` | For preview of actions use go=false |
| sync | ````ojob ojob.io/s3/ops ... op=sync bucket=mybucket local=. remote=my/list go=true```` | For preview of actions use go=false |
| stat | ````ojob ojob.io/s3/ops ... op=stat bucket=mybucket remote=my/lisT/file.txt```` | |