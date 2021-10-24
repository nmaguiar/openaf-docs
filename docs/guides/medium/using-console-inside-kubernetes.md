---
layout: default
title: Using console inside Kubernetes
parent: Medium
grand_parent: Guides
---

# Using console inside Kubernetes

Often using the OpenAF console inside a container might be useful to test connectivity or quickly perform some operations.

To quickly execute an OpenAF console on a Kubernetes cluster just adapt the following command:

````bash
$ kubectl run -i --tty test --image=openaf/oafc --image-pull-policy=Always --rm=true --restart=Never --leave-stdin-open=true -n default
````

Do change the Kubernetes namespace (option -n) or add more options as needed.

> Keep in mind that if you cluster doesn't have access to the internet you will need to push the openaf/oafc image.

## Examples of quick tests to perform

### Testing network accessibility inside a Kubernetes Pod

````javascript
> ow.loadNet()
> ow.net.testPort("elasticsearch", 9200)
true
> ow.net.testPort("dns.google.com", 53)
false
````

This means that elasticsearch is "resolvable" in the container and port 9200 can be accessed. But dns.google.com on port 53 can not be accessed.

### Testing network latency from a Kubernetes Pod

````javascript
> ow.loadNet();
> ow.net.testPortLatency("postgresql", 5432)
2
> ow.net.testPortLatency("yahoo.co.jp", 443)
245
````

This means that postgresql can be accessed on port 5432 with a socket network latency of 2ms. The site yahoo.co.jp on port 443 is also accessible but with a socket network latency of 245ms.

### Testing resolving DNS in a Kubernetes Pod

````javascript
> ow.loadNet()
> ow.net.getHost2IP("minio.default.svc.cluster.local")
10.97.189.52
> ow.net.getHost2IP("minio")
10.97.189.52
````

This means that in the Kubernetes Pod the address "minio" and the address "minio.default.svc.cluster.local" will resolve to the same IP address: 10.97.189.52

You can also perform reverse DNS lookups

````javascript
> ow.loadNet()
> ow.net.getIP2Host("10.97.189.52")
minio.default.svc.cluster.local
````
 
### Testing JDBC latency

````javascript
> ojob ojob.io/net/jdbc jdbc=jdbc:postgresql://hh-pgsql-public.ebi.ac.uk:5432/pfmegrnargs user=reader pass=NWDMCE5xdipIjRrp
Connecting to the database 'jdbc:postgresql://hh-pgsql-public.ebi.ac.uk:5432/pfmegrnargs' with user 'reader'...
Connected in 167ms

Performing query...
Reply from database: payload=32 time=29ms
Reply from database: payload=32 time=15ms
Reply from database: payload=32 time=15ms
Reply from database: payload=32 time=16ms

Statistics:
    Queries: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip time in milli-seconds:
    Minimum = 15ms, Maximum = 29ms, Average = 18ms

>
````

This means that in average the latency, through the JDBC driver, is around 18ms to this database.

> Note: even if the target database is reachable this test requires internet access to retrive ojob.io/net/jdbc

### Checking the returned SSL certificates

````
> ow.net.getTLSCertificates("slashdot.org")
╭─────┬───────────────┬───────────────────────────────────────────────────────────┬─────┬────────────────╮
│ [0] │     issuerDN: │ CN=R3, O=Let's Encrypt, C=US                              │     │                │
│     │    subjectDN: │ CN=slashdot.org                                           │     │                │
│     │    notBefore: │ Wed Aug 25 2021 03:06:21 GMT-0000 (UTC)                   │     │                │
│     │     notAfter: │ Tue Nov 23 2021 03:06:20 GMT-0000 (UTC)                   │     │                │
├─────┼───────────────┼───────────────────────────────────────────────────────────┼─────┼────────────────┤
│     │ alternatives: │                                                       [0] │ [0] │ 2              │
│     │               │                                                           │ [1] │ *.slashdot.org │
├─────┼───────────────┼───────────────────────────────────────────────────────────┼─────┼────────────────┤
│     │               │                                                       [1] │ [0] │ 2              │
│     │               │                                                           │ [1] │ slashdot.org   │
├─────┼───────────────┼───────────────────────────────────────────────────────────┼─────┼────────────────┤
│ [1] │     issuerDN: │ CN=ISRG Root X1, O=Internet Security Research Group, C=US │     │                │
│     │    subjectDN: │ CN=R3, O=Let's Encrypt, C=US                              │     │                │
│     │    notBefore: │ Fri Sep 04 2020 00:00:00 GMT-0000 (UTC)                   │     │                │
│     │     notAfter: │ Mon Sep 15 2025 16:00:00 GMT-0000 (UTC)                   │     │                │
├─────┼───────────────┼───────────────────────────────────────────────────────────┼─────┼────────────────┤
│ [2] │     issuerDN: │ CN=DST Root CA X3, O=Digital Signature Trust Co.          │     │                │
│     │    subjectDN: │ CN=ISRG Root X1, O=Internet Security Research Group, C=US │     │                │
│     │    notBefore: │ Wed Jan 20 2021 19:14:03 GMT-0000 (UTC)                   │     │                │
│     │     notAfter: │ Mon Sep 30 2024 18:14:03 GMT-0000 (UTC)                   │     │                │
╰─────┴───────────────┴───────────────────────────────────────────────────────────┴─────┴────────────────╯
````

