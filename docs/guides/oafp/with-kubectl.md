---
layout: default
title: oafp with Kubectl
parent: oafp
grand_parent: Guides
---

# oafp with Kubectl

List of examples of use of oafp with Kubectl:

### List of pods per namespace and kind

```bash
oafp cmd="kubectl get pods -A -o json" path="items[].{ns:metadata.namespace,kind:metadata.ownerReferences[].kind,name:metadata.name,status:status.phase,restarts:sum(status.containerStatuses[].restartCount),node:spec.nodeName,age:timeago(status.startTime)}" sql="select * order by status,name" output=ctable
```

Result:
```
    ns     │   kind   │                 name                 │ status  │restarts│          node          │     age      
───────────┼──────────┼──────────────────────────────────────┼─────────┼────────┼────────────────────────┼──────────────
kube-system│ReplicaSet│coredns-77ccd57875-5m44t              │Running  │0       │k3d-k3s-default-server-0│66 minutes ago
kube-system│ReplicaSet│local-path-provisioner-957fdf8bc-24hmf│Running  │0       │k3d-k3s-default-server-0│66 minutes ago
kube-system│ReplicaSet│metrics-server-648b5df564-hzbwb       │Running  │0       │k3d-k3s-default-server-0│66 minutes ago
kube-system│ReplicaSet│socks-server-d7c8c4d78-r6jc9          │Running  │0       │k3d-k3s-default-server-0│66 minutes ago
kube-system│DaemonSet │svclb-socks-server-78b973ca-zvf58     │Running  │0       │k3d-k3s-default-server-0│66 minutes ago
kube-system│DaemonSet │svclb-traefik-e1776788-7z2gf          │Running  │0       │k3d-k3s-default-server-0│66 minutes ago
kube-system│ReplicaSet│traefik-64f55bb67d-g2vps              │Running  │0       │k3d-k3s-default-server-0│66 minutes ago
kube-system│Job       │helm-install-traefik-6j5zx            │Succeeded│1       │k3d-k3s-default-server-0│66 minutes ago
kube-system│Job       │helm-install-traefik-crd-z59fs        │Succeeded│0       │k3d-k3s-default-server-0│66 minutes ago
[#9 rows]
```

### CPU, memory and storage stats per node

```bash
oafp cmd="kubectl get nodes -o json" path="items[].{node:metadata.name,totalCPU:status.capacity.cpu,allocCPU:status.allocatable.cpu,totalMem:to_bytesAbbr(from_bytesAbbr(status.capacity.memory)),allocMem:to_bytesAbbr(from_bytesAbbr(status.allocatable.memory)),totalStorage:to_bytesAbbr(from_bytesAbbr(status.capacity.\"ephemeral-storage\")),allocStorage:to_bytesAbbr(to_number(status.allocatable.\"ephemeral-storage\")),conditions:join(\`, \`,status.conditions[].reason)}" output=ctable
```

Result:
```
          node          │totalCPU│allocCPU│totalMem│allocMem│totalStorage│allocStorage│                                        conditions                                         
────────────────────────┼────────┼────────┼────────┼────────┼────────────┼────────────┼───────────────────────────────────────────────────────────────────────────────────────────
k3d-k3s-default-server-0│4       │4       │3.85 GB │3.85 GB │77.6 GB     │73.8 GB     │KubeletHasSufficientMemory, KubeletHasNoDiskPressure, KubeletHasSufficientPID, KubeletReady
[#1 row]
```

### Build an output table from kubectl get pods with namespace, pod name, container name and corresponding resources

```bash
kubectl get pods -A -o json | oafp path="items[].amerge({ ns: metadata.namespace, pod: metadata.name }, spec.containers[].{ container: name, resources: to_slon(resources) })[]" sql="select ns, pod, container, resources order by ns, pod, container" out=ctable
```

Result:
```
    ns     │                 name                 │      container       │                           resources                            
───────────┼──────────────────────────────────────┼──────────────────────┼────────────────────────────────────────────────────────────────
kube-system│coredns-77ccd57875-25jr4              │coredns               │[(limits: (memory: 170Mi), requests: (cpu: 100m, memory: 70Mi))]
kube-system│svclb-socks-server-00fc08b8-zgw8m     │lb-tcp-1080           │[()]                                                            
kube-system│local-path-provisioner-957fdf8bc-7vc8g│local-path-provisioner│[()]                                                            
kube-system│metrics-server-648b5df564-prq2r       │metrics-server        │[(requests: (cpu: 100m, memory: 70Mi))]                         
kube-system│svclb-traefik-f37ea49c-tj7lw          │lb-tcp-80,lb-tcp-443  │[() | ()]                                                       
kube-system│helm-install-traefik-crd-xpnrr        │helm                  │[()]                                                            
kube-system│helm-install-traefik-2f4xn            │helm                  │[()]                                                            
kube-system│socks-server-d7c8c4d78-vs4vj          │oaf                   │[()]                                                            
kube-system│traefik-64f55bb67d-tllw7              │traefik               │[()]                                                            
[#9 rows]
```

### Build an output table from kubectl get pods with node, namespace, pod name, container name and corresponding resources

```bash
kubectl get pods -A -o json | oafp path="items[].amerge({ node: spec.nodeName, ns: metadata.namespace, pod: metadata.name }, spec.containers[].{ container: name, resources: to_slon(resources) })[]" sql="select node, ns, pod, container, resources order by node, ns, pod, container" out=ctable
```

Result:
```
          node          │    ns     │                 pod                  │      container       │                          resources                           
────────────────────────┼───────────┼──────────────────────────────────────┼──────────────────────┼──────────────────────────────────────────────────────────────
k3d-k3s-default-server-0│kube-system│coredns-77ccd57875-659xc              │coredns               │(limits: (memory: 170Mi), requests: (cpu: 100m, memory: 70Mi))
k3d-k3s-default-server-0│kube-system│helm-install-traefik-b6l27            │helm                  │()                                                            
k3d-k3s-default-server-0│kube-system│helm-install-traefik-crd-npmc8        │helm                  │()                                                            
k3d-k3s-default-server-0│kube-system│local-path-provisioner-957fdf8bc-kfxkr│local-path-provisioner│()                                                            
k3d-k3s-default-server-0│kube-system│metrics-server-648b5df564-vmjrw       │metrics-server        │(requests: (cpu: 100m, memory: 70Mi))                         
k3d-k3s-default-server-0│kube-system│socks-server-d7c8c4d78-tpwg6          │oaf                   │()                                                            
k3d-k3s-default-server-0│kube-system│svclb-socks-server-dc24b0be-dx4px     │lb-tcp-1080           │()                                                            
k3d-k3s-default-server-0│kube-system│svclb-traefik-9ef3fc4c-sj2ln          │lb-tcp-443            │()                                                            
k3d-k3s-default-server-0│kube-system│svclb-traefik-9ef3fc4c-sj2ln          │lb-tcp-80             │()                                                            
k3d-k3s-default-server-0│kube-system│traefik-64f55bb67d-s6fvf              │traefik               │()                                                            
[#10 rows]
```