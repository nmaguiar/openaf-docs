---
layout: default
title: Kubernetes nodes image management
parent: oJobIO
grand_parent: Guides
---

# Kubernetes nodes image management

Each Kubernetes node keeps a *"cache"* of the container images that it downloads from container registries. Each node will manage it's cache to ensure there is enough filesystem space by deleting old unused images. 

In Kubernetes you can define an *imagePullPolicy* with the possible values: *IfNotPresent*, *Always* and *Never*. The default is to use the *IfNotPresent* value to keep container images *"cached"* on each node avoiding constant network connections to the corresponding container registry and delays on subsequent executions on the same node using the same image.

For this reason it's a common practice to use different labels whenever there is a need to use a different image version. But the tag "latest" and others are also used for ease of use. Unfortunatelly this type of tags or updating the same image with the same tag would require to use the policy *Always* or risk getting into "wired" results (e.g. one node could use an older version of an image and another node could use a newer).

A solution is to interact directly with the container runtime of each Kubernetes node using a container image with the "crictl" or "docker" clients running in *privileged* mode.

To automate all the necessary operations you can use: **ojob.io/kube/criOps**

## Usage

The _ojob.io/kube/criOps_ aims to help to achieve this by interacting with Kubernetes API (assumes you have a kubectl config correclty setup environment with the right permissions) to launch a pod, with the rigth cli tool, on each node. If necessary you can provide a list of nodes instead of the default of running in all nodes (using the option _"node=node-1,node-2,node-3"_). Each pod will be prefixed with a name that you can also customize using the option _"name=myjobs-"_.

The oJob uses the [nmaguiar/imgutils](https://github.com/nmaguiar/imgutils) but you can replace by any other image that has the _crictl_ CLI tool using the option "jobimg=my/custom/image:1.2.3". The _crictl_ CLI tool is used, on each node, to perform the necessary operations.

> By default the pods will be launched on the 'kube-system' namespace but you can control this using the option 'ns=some-namespace'.

> You can use the image _nmaguiar/imgutils:lite_ which is smaller than the original _nmaguiar/imgutils_.

### Requirements

You will need to execute *ojob.io/kube/criOps* on a machine where you have *kubectl* correclty configured to access the target Kubernetes cluster with enough permissons to create privileged containers.

Additionally you will need to know which container runtime the Kubernetes distribution you are using uses and if the Unix socket to connect to the corresponding container runtime is different from *"/run/container.d/containerd.sock"*.

For a quick reference (information at the time of writing):

| Kubernetes distribution | Container runtime | Socket path | Options for ojob.io/kube/criOps |
|-------------------------|-------------------|-------------|---------------------------------|
| K3S/K3D | containerd | /run/k3s/containerd/containerd.sock | socket=/run/k3s/containerd/containerd.sock |
| AWS EKS | containerd | /run/containerd/containerd.sock | |
| GCP GKE | containerd | /run/containerd/containerd.sock | |
| Azure AKE | containerd | /run/containerd/containerd.sock | |
| RedHat OpenShift | CRI-O | /var/run/crio/crio.sock | crio=true |

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

After listing you might find a specific image in some or all nodes that you want to remove. To do this first ensure that there isn't any container running with the image you want to remove. If there is, the image on the node where the container is running won't be removed (you will see an error message for that node).

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
* a copy of the *nmaguiar/imgutils* on an accessible private registry
* Download the Kube oPack: https://openaf.io/opacks/Kube.opack
* Download the criops oJob: https://ojob.io/kube/criOps.yaml

Then with the three files on the target host:

```bash
# run the static OpenAF file
sh ./oaf-*

# install the Kube oPack
./opack install Kube.opack

# you are ready to run
./ojob criOps.yaml op=list jobimg=myregistry/nmaguiar/imgutils [...]
```
