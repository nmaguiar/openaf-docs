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

### Output a table with the docker stats broken down for each value

```bash
oafp cmd="docker stats --no-stream" in=lines linesvisual=true linesjoin=true out=ctree path="[].{containerId:\"CONTAINER ID\",pids:PIDS,name:\"NAME\",cpuPerc:\"CPU %\",memory:\"MEM USAGE / LIMIT\",memPerc:\"MEM %\",netIO:\"NET I/O\",blockIO:\"BLOCK I/O\"}|[].{containerId:containerId,pids:pids,name:name,cpuPerc:replace(cpuPerc,'%','',''),memUsage:from_bytesAbbr(split(memory,' / ')[0]),memLimit:from_bytesAbbr(split(memory,' / ')[1]),memPerc:replace(memPerc,'%','',''),netIn:from_bytesAbbr(split(netIO,' / ')[0]),netOut:from_bytesAbbr(split(netIO,' / ')[1]),blockIn:from_bytesAbbr(split(blockIO,' / ')[0]),blockOut:from_bytesAbbr(split(blockIO,' / ')[1])}" out=ctable
```

Result:

```
containerId │pids│       name        │cpuPerc│memUsage │ memLimit  │memPerc│ netIn │netOut│ blockIn │blockOut
────────────┼────┼───────────────────┼───────┼─────────┼───────────┼───────┼───────┼──────┼─────────┼────────
e010058293cf│23  │abcde-grafana-1    │0.16   │212756070│14656575898│1.45   │108544 │26829 │136314880│0
78028d4d69e2│12  │abcde-prometheus-1 │0.04   │178572493│14656575898│1.22   │6647972│621568│113246208│14155776
76cfc6cb26fd│1   │openvpn            │0.00   │10113516 │14656575898│0.07   │2038   │0     │9216983  │67072
5b65df9ef7db│6   │abcde-appapp-1     │0.01   │58185482 │14656575898│0.40   │45978  │0     │45717914 │209920
67605fed6ccd│29  │abcde-nginx-proxy-1│0.43   │81558241 │14656575898│0.56   │45875  │0     │23068672 │5274337
cf2debb6a676│6   │abcde-wiki-1       │0.01   │56172216 │14656575898│0.38   │45875  │0     │45508198 │20992
[#6 rows]
```