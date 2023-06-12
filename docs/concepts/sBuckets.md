---
layout: default
title: SBuckets
parent: Concepts
grand_parent: OpenAF docs
---

# SBucket

OpenAF's SBucket allow you to store secret strings and/or objects and to refer them by specific keys on the code. It can help even to directly create objects (e.g. DB, SSH, etc...) or even execute functions (e.g. ow.obj.pool.DB, ow.obj.pool.SSH, etc...).

These secrets can be divided into different buckets and bucket repositories to make it easy to be "transported" to different systems or quickly applied as a text json/yaml file through an external secrets management service (e.g. Kubernetes secrets).

## How to use it

### Setting up a secret

To set a simple secret on the default repository and bucket just execute:

````javascript
$sec().set("pass", "Password123")
````

Secrets can either be strings (even in encrypted form) or maps:

````javascript
$sec().set("passObj", {
    login: "myUser",
    pass : "myPassword"
})
````

**Note:** _this secret will actually be stored on the home directory in .openaf-sec.yml. The default repository master key will be automatically created and stored in the home directory in .openaf-sec._

### Obtaining a secret

After setting a secret on can use it by simply invoking:

````javascript
$sec().get("pass")
````

### Using different sbuckets and repos

To use a different SBucket and repository, from the default ones, just set your secret indicating the corresponding sbucket and it's specific lock key:

````javascript
var testSBucket = $sec("testRepo", "testBucket", "testBucketPass123");

testSBucket.set("pass", "PaSsWoRd");
````

to access the secret:

````javascript
testSBucket.get("pass");
````

**Note:** _the new repository will be stored on the home directory in .openaf-sec-testRepo.yml. You can specify a different repository master key with an extra argument in $sec. See more by executing "help $sec.$sec" in the openaf-console._

### Transporting a SBucket between systems

Let's examplify transporting a sbucket between a system A to B.

**System A**

Setting secrets in system A:

````javascript
> var testSBucket = $sec("testRepo", "testBucket", "testBucketPass123");
> testSBucket.set("pass", "PaSsWoRd");
> testSBucket.getBucket()
"QTU5RDlGMzEzQTNEMEQ4Q0VFQjQ1N..."
````

**System B**

Setting the testBucket in system B (on the default repo):

````javascript
> $sec().setBucket("QTU5RDlGMzEzQTNEMEQ4Q0VFQjQ1N...", "testBucket", "testBucketPass123");
> var sb = $sec(__, "testBucket", "testBucketPass123");
> sb.get("pass");
"PaSsWoRd"
````

To delete a bucket after is no longer necessary:

````javascript
> sb.unsetBucket("testBucket");
````

## Using secrets from a secrets file

In certains scenarios, such as running from a container, a set of secrets might be provided as a secrets file (a YAML file). These secrets files can container buckets and corresponding keys. For example:

````yaml
bucket1:
  serviceA:
    url  : https://1.2.3.4:1234/serviceA
    login: &USER myUser
    pass : &PASS myEncryptedPass

  serviceB:
    url  : https://1.2.3.4:1234/serviceB
    login: *USER
    pass : *PASS

bucket2:
  db:
    jdbcURL: jdbc:mysql://localhost:3306/sonoo
    login  : dbUser
    pass   : dbEncryptedUser
````

To obtain these secrets you would simple have to provide the secrets file location, the corresponding bucket (e.g. bucket1, bucket2) and the corresponding key (e.g. serviceA, serviceB, db):

````javascript
var sb = $sec(__, "bucket1", __, __, "/secrets/secrets.yaml")
sb.get("serviceB")
````

If you are writing an oJob you can use the ["oJob get sec" job](../guides/ojob/ojob-building-blocks.html#ojob-sec-get):

````yaml
- name: Use service B
  from:
  - name: ojob get sec
    args:
      secFile  : /secrets/secrets.yaml
      secBucket: bucket1
      secKey   : serviceB
  # ...
````

## Using secrets from environment variables

In certains scenarios, such as running from a container, a secret might be provided as an environment variable. For these cases there is a simple way to use OpenAF's SBucket. Simply use the repository **"system"** and the bucket **"envs"**. The _key_ used to obtain the secret should be equal to the environment variable name.

For example, let's say you need to store the _passObj_, as referenced above in the "Setting up a secret" example, with the environment variable "MY_SECRET". In this case then environment variable would be equal to the JSON representation:

````
MY_SECRET='{login:"myUser",pass:"myPassword"}'
````

To get this secret you simple have to write:

````javascript
var testSBucket = $sec("system", "envs")
testSBucket.get("MY_SECRET")
````

## Security tips

* In order to avoid writing the SBucket password and/or the repository master key on code or OpenAF's console use _askEncrypt()_ function to ask for user input to introduce the passwords/keys.
* In containers or batch processing store the SBucket passwords in an encrypted string (output from _askEncrypt()_).
* When a sbucket repository is no longer needed just delete the corresponding file (_.openaf-sec-[repository name].yml_) from the home directory.

## Additionaly tips

You can use the [ojob.io sec ops jobs](https://ojob.io/sec/ops.md) for easier setting and transport of OpenAF's SBuckets. It has options to set secrets for objects ($sec.setObj), functions ($sec.setFn) and even to instantiate OpenAF's objects ($sec.setObj) with the corresponding secrets. 
Additionally if you provide _secRepo=system_ and _secBucket=envs_ it will automatically build you the value string needed to set an environment variable with a secret.