---
layout: default
title: oafp with OpenAF's channels
parent: oafp
grand_parent: Guides
---

# oafp with OpenAF's channels

List of examples of use of oafp with OpenAF's channels:

## Etcd

### Copy the json result of a command into an etcd database
```bash
oaf -c "\$o(io.listFiles('.').files,{__format:'json'})" | oafp out=ch ch="(type: etcd3, options: (host: localhost, port: 2379), lib: 'etcd3.js')" chkey=canonicalPath
```

### Getting all data stored in an etcd database
```bash
echo "" | oafp in=ch inch="(type: etcd3, options: (host: localhost, port: 2379), lib: 'etcd3.js')" out=ctable
```

## MVS

### Store the json results of a command into a H2 MVStore file
```bash
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=ch ch="(type: mvs, options: (file: data.db))" chkey=canonicalPath
```

### Retrieve all keys stores in a H2 MVStore file
```bash
echo "" | oafp in=ch inch="(type: mvs, options: (file: data.db))" out=ctable
```

## Prometheus

### Perfom a query to a metric & label, with a start and end time, to a Prometheus server 
```bash
oafp in=ch inch="(type:prometheus,options:(urlQuery:'http://prometheus.local'))" inchall=true data="(start:'2024-03-22T19:00:00.000Z',end:'2024-03-22T19:05:00.000Z',step:60,query:go_memstats_alloc_bytes_total{job=\"prometheus\"})" path="[].values[].{date:to_date(mul([0],to_number('1000'))),value:[1]}" out=ctable
```