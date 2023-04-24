---
layout: default
title: Installation global oJobs
parent: How To
grand_parent: OpenAF docs
---

# Installation global oJobs

(since OpenAF version >= 20220822)

After installing OpenAF you can run [oJobs](../concepts/oJob.md) by pointing to a YAML or JSON file. You can also run remote YAMLs/JSONs like [oJob.io](../concepts/oJobIO.md). If you do this often usually you end up with a set of YAML/JSON files that you run often and you might want an easy/quick way to reference them.

For that you can use "global" oJobs. These YAML/JSON files just need to be copied to a folder in ````[OpenAF installation folder]/ojobs````. After creating the folder and copying the YAML/JSON files you want you will be abloe to quickly list them by just calling:

````
$ ojob -global
       oJob       │                                description                                │# todo
──────────────────┼───────────────────────────────────────────────────────────────────────────┼──────
myLogParser.yaml  │Parser logs the way I want                                                 │3
myMorningNews.yaml│Makes my a summary of news I want to be aware                              │2
quickBackup.yaml  │Quickly makes an object storage backup of any folder updating my backups db│5
````

To execute any of them, as long as you don't have a similar file in the current path, just execute:

````
$ ojob quickBackup.yaml folder=myfolder remotePath=backups/myfolder name=stuff
````

or 

````
tail -f my-wierd-log.log | ojob myLogParser.yaml
````

What if I want to be sure when I execute ````ojob myMorningNews.yaml```` from where oJob is running? Simply execute:

````
$ ojob myMorningNews.yaml -which
/home/myuser/bin/oaf/ojobs/myMorningNews.yaml
````
