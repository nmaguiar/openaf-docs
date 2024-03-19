---
layout: default
title: oafp with Unix commands
parent: oafp
grand_parent: Guides
---

# oafp with Unix commands

List of examples of use of oafp with unix commands:

### Creates a data.ndjson file where each record is formatted from json files in /some/data

```bash
find /some/data -name "*.json" -exec oafp {} output=json \; > data.ndjson
```

### Parse /proc/cpuinfo into an array

```bash
cat /proc/cpuinfo | sed "s/^$/---/mg" | ./oafp in=yaml path="[?not_null(@)]" out=ctree
```

### Parse the result of the ls command

```bash
ls -lad --time-style="+%Y-%m-%d %H:%M" * | oafp in=lines path="map(&split_re(@,'\\s+').{permissions:[0]
,id:[1],user:[2],group:[3],size:[4],date:[5],time:[6],file:[7]},[])" linesjoin=true out=ctable
```

### Parse the result of the route command

```bash
route | sed "1d" | oafp in=lines linesjoin=true linesvisual=true linesvisualsepre="\s+" out=ctable
```

### Parse the ‘ip tcp_metrics’ command

```bash
ip tcp_metrics | sed 's/^/target: /g' | sed 's/$/\n\n---\n/g' | sed 's/ \([a-z]*\) /\n\1: /g' | head -n -2 | oafp in=yaml path="[].{target:target,age:from_timeAbbr(replace(age,'[sec|\.]','','')),cwnd:cwnd,rtt:from_timeAbbr(rtt),rttvar:from_timeAbbr(rttvar),source:source}" sql="select * order by target" out=ctable
```

### Parse the ‘arp’ command output

```bash
arp | oafp in=lines linesvisual=true linesjoin=true out=ctable
```

### Loop over the current active network connections

```bash
oafp cmd="netstat -tun | sed \"1d\"" in=lines linesvisual=true linesjoin=true linesvisualsepre="\\s+(\\?\!Address)" out=ctable loop=1
```
