---
layout: default
title: How To - Update the JVM version
parent: How To
grand_parent: OpenAF docs
---

# How to - Update the JVM version

OpenAF is a Java application thus it relies on an installed JVM. Whenever you run the OpenAF commands _"oaf"_ , _"oafc"_, _"ojob"_, _"opack"_, etc... you are actually running a script that execute an installed JVM together with OpenAF's Java binary (e.g. openaf.jar). 

The system you are using might already have a Java JRE (Java Runtime Enviroment) on a specific path. Unfortunatelly it's common to include in the corresponding path the Java version: _/usr/java/jdk1.8.0_192-amd64/jre/bin/java_. So any change on the Java version will imply a change in the path.
 
## When Java is on an operating system folder

After a system adminsitrator has updated Java, on the system you are using, you just need to execute the following commands afterwards:

````shell
cd /to/the/openaf/folder
/usr/java/jdk1.8.0_372-amd64/jre/bin/java -jar openaf.jar --install
````

This will regenerate the OpenAF's script, on the same folder, pointing now to the new Java version. 

## When there is a "jre" sub-folder

If you are not using Java from an operating system folder chances are that you have a "jre" sub-folder on [OpenAF folder]/jre. If you have a new Java JRE/JDK installation:

1. Backup the existing "jre" folder to a different backup folder
2. Delete the current "jre" folder
3. Create a new "jre" folder and then extract your new JRE/JDK installation into it

That's it. Since Java is in the same path nothing needs to change.

> Before starting the upgrade, on a system with Internet access and OpenAF, you can follow the [instructions to prepare a Java JRE tgz](../guides/ojobio/quickly_download_java.md).

> You can use ```ojob ojob.io/oaf/javaUpdate``` to determine if an update is needed and download a jre.tgz accordingly.

## In container images

There is no need to upgrade the JVM inside an OpenAF image. Just simply update the image and it should bring the latest JVM avalable at time of build.