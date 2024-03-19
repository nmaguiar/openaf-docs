---
layout: default
title: oafp with external APIs
parent: oafp
grand_parent: Guides
---

# oafp with external APIs

List of examples of use of oafp with external APIs:

### Generating a simple table of the current public IP address
```bash
curl -s https://ifconfig.co/json | oafp flatmap=true out=map
```

### Converting the Cloudflare DNS trace info
```bash
curl -s https://1.1.1.1/cdn-cgi/trace | oafp in=ini out=ctree
```