---
layout: default
title: Kubernetes nodes image management
parent: oJobIO
grand_parent: Guides
---

# Kubernetes nodes image management

Kubernetes nodes run their own container runtime (e.g. containerd, cri-o, moby) that caches pulled images locally. You might have the need to get a complete list of all images in all, or specific, nodes or to perform certain operations such as removing a specific image, forcing to pull a new one or just for the pruning.

To achieve this you can either go to each Kubernetes node container runtime cli tool and perform the operation or you can run a privileged container on each to achieve the same.

The _ojob.io/kube/criOps_ aims to help to achieve this by interacting with Kubernetes API (assumes you have a kubectl config correclty setup environment with the right permissions) to launch a pod, with the rigth cli tool, on each node. If necessary you can provide a list of nodes instead of the default of running in all nodes (using the option _"node=node-1,node-2,node-3"_). Each pod will be prefixed with a name that you can also customize using the option _"name=myjobs-"_.

The oJob uses the [nmaguiar/imgutils](https://github.com/nmaguiar/imgutils) but you can replace by any other image that has the _crictl_ CLI tool using the option "jobimg=my/custom/image:1.2.3". The _crictl_ CLI tool is used, on each node, to perform the necessary operations.

Finally depending on the Kubernetes "distribution" you are using you will need to provide the correct socket where each node runs the container runtime API. The following is a reference table for major distributions:

| Distribution | Socket option to use | Extra options |
|--------------|----------------------|---------------|
| K3S | socket=/run/k3s/containerd/containerd.sock | |
| OpenShift or CRI-O based | socket=/var/run/crio/crio.sock | crio=true |
| AWS EKS, GCP GKE, Azure AKS or other containerd based | socket=/run/containerd/containerd.sock | |

> By default the pods will be launched on the 'kube-system' namespace but you can control this using the option 'ns=some-namespace'.

## Listing images

To get a list all images on all nodes just execute:

**K3S:**

```bash
ojob ojob.io/kube/criOps op=list socket=/run/k3s/containerd/containerd.sock __format=ctable
```

**OpenShift/CRI-O**

```bash
ojob ojob.io/kube/criOps op=list socket=/var/run/crio/crio.sock crio=true __format=ctable
```

**ContainerD**

```bash
ojob ojob.io/kube/criOps op=list socket=/run/containerd/containerd.sock __format=ctable
```

> You can run with ```[...] __format=csv > list.csv``` to export the list to another tool.

## Removing an image

To remove a specific image from all nodes just execute (assuming you want to remove the image 'library/nginx:latest')

**K3S:**

```bash
ojob ojob.io/kube/criOps op=rmi socket=/run/k3s/containerd/containerd.sock image=library/nginx:latest
```

**OpenShift/CRI-O**

```bash
ojob ojob.io/kube/criOps op=rmi socket=/var/run/crio/crio.sock crio=true image=library/nginx:latest
```

**ContainerD**

```bash
ojob ojob.io/kube/criOps op=rmi socket=/run/containerd/containerd.sock image=library/nginx:latest
```

## Pulling an image

To pull an image in all nodes just execute (assuming you want to pull the image 'library/nginx:latest'):

**K3S:**

```bash
ojob ojob.io/kube/criOps op=list socket=/run/k3s/containerd/containerd.sock image=library/nginx:latest
```

**OpenShift/CRI-O**

```bash
ojob ojob.io/kube/criOps op=list socket=/var/run/crio/crio.sock crio=true image=library/nginx:latest
```

**ContainerD**

```bash
ojob ojob.io/kube/criOps op=list socket=/run/containerd/containerd.sock image=library/nginx:latest
```

> This can be useful to avoid the startup time it takes for each node to retrieve a container image from a registry service for images that you are almost sure will be needed in all nodes for your case.

## Notes

* You can also use the option _op=prune_ to force the "clean-up" in all nodes.
* If you specify only one node you can use the _op=interactive_ option to use _crictl_ directly on the given node.
* Everytime the ojob runs it will print out the corresponding "kubectl delete" command you will need to run if something "goes south" to properly clean your cluster.
* The pods are launched by the oJob as privileged pods, so you will need the right Kubernetes permissions to run them succesfully.
* Either if you use the image nmaguiar/imgutils or your own that image will always be retrieved for the nodes you run the oJob on.

## Running without Internet (air-gap)

You will just need the following files:

* The [static OpenAF file](../../concepts/static-installation.md#list-of-direct-links) to run on the target host
* Download the Kube oPack: https://openaf.io/opacks/Kube.opack
* Download the criops oJob: https://ojob.io/kube/criOps.yaml

Then with the three files on the target host:

```bash
# run the static OpenAF file
sh ./oaf-*

# install the Kube oPack
./opack install Kube.opack

# you are ready to run
./ojob criOps.yaml op=list ...
```
