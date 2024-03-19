---
layout: default
title: oafp with Docker commands
parent: oafp
grand_parent: Guides
---

# oafp with Docker commands

List of examples of use of oafp with Docker commands:

### Output a table with the list of running containers

```bash
oafp cmd="docker ps --format json" input=ndjson ndjsonjoin=true path="[].{id:ID,name:Names,state:State,image:Image,networks:Networks,ports:Ports,Status:Status}" sql="select * order by networks,state,name" output=ctable
```

Result:

```
     id     │          name          │ state │            image             │       networks       │                         ports                         │  Status  
────────────┼────────────────────────┼───────┼──────────────────────────────┼──────────────────────┼───────────────────────────────────────────────────────┼──────────
af3adb5b8349│registry                │running│registry:2                    │bridge,k3d-k3s-default│0.0.0.0:5000->5000/tcp                                 │Up 2 hours
cba6e3807b44│k3d-k3s-default-server-0│running│rancher/k3s:v1.27.4-k3s1      │k3d-k3s-default       │                                                       │Up 2 hours
b775ad480764│k3d-k3s-default-serverlb│running│ghcr.io/k3d-io/k3d-proxy:5.6.0│k3d-k3s-default       │80/tcp, 0.0.0.0:1080->1080/tcp, 0.0.0.0:45693->6443/tcp│Up 2 hours
[#3 rows]
```