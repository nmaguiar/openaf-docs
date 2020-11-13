---
layout: default
title: "Medium: Executing a remote SSH command in background"
parent: Guides
grand_parent: OpenAF docs
---

# Executing a remote SSH command in background

Whenever you execute a SSH command on a remote host it will wait until that process ends. Even with Unix targets if you add a "&" on the end of the command and/or add "nohup" on the beginning you will still wait. Same obviously applies in OpenAF:

````javascript
var aTarget = { 
    host : "some.host",
    port : 22,
    login: "me",
    pass : "change"
    //id: "~/.ssh/mykey_rsa"
}

var res = $ssh(aTarget)
.sh("nohup wget https://download.dokuwiki.org/src/dokuwiki/dokuwiki-stable.tgz &")
.get();

// res will have all the output from wget as if '&' was never there in the first place
````

The reason is related to how SSH works. While any of the stdout, stderr or stdin are "open" the execution command won't end. So a simple way to solve it is to change the execution command to:

````javascript
var res = $ssh(aTarget)
.sh("nohup wget https://download.dokuwiki.org/src/dokuwiki/dokuwiki-stable.tgz 2> wget.out > /dev/null < /dev/null &")
.get();

// res.stdout and res.stderr now don't shown anything since the process was
// left running on the server
````

Later you can check the execution command output:

````javascript
var res = $ssh(aTarget).sh("cat wget.out").get(0).stdout;
````

## What about promises?

Yes, you could code something like:

````javascript
var res;
var promise = $do(() => {
    res = $ssh(aTarget)
          .sh("wget https://download.dokuwiki.org/src/dokuwiki/dokuwiki-stable.tgz")
          .get();
});
````

But if you are running on a cloud function (e.g. AWS Lambda) payed by execution time you don't want to wait for the promise to be fullfilled (specially if the download will or might take some time).