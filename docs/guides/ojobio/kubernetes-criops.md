---
layout: default
title: Kubernetes per node image operations
parent: oJobIO
grand_parent: Guides
---

# Kubernetes per node image operations

Each Kubernetes node keeps a *"cache"* of the container images that it downloads from container registries. Each node will manage it's cache to ensure there is enough filesystem space by deleting old unused images. 

In Kubernetes you can define an *imagePullPolicy* with the possible values: *IfNotPresent*, *Always* and *Never*. The default is to use the *IfNotPresent* value to keep container images *"cached"* on each node avoiding constant network connections to the corresponding container registry and delays on subsequent executions on the same node using the same image.

For this reason it's a common practice to use different labels whenever there is a need to use a different image version. But the tag "latest" and others are also used for ease of use. Unfortunatelly this type of tags or updating the same image with the same tag would require to use the policy *Always* or risk getting into "wired" results (e.g. one node could use an older version of an image and another node could use a newer).

A solution is to interact directly with the container runtime of each Kubernetes node using a container image with the "crictl" or "docker" clients running in *privileged* mode.

To automate all the necessary operations you can use: **ojob.io/kube/criOps**

## Requirements

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

## Listing images on nodes

Get a list of all images on all nodes just execute: 

```bash
ojob ojob.io/kube/criOps op=list __format=ctable [options for your kube distribution]
```

You can also create a CSV with the collected data:

```bash
ojob ojob.io/kube/criOps op=list __format=csv [options for your kube distribution] > list.csv
```

If you have a large cluster you can specify a list of nodes for which the list should be retrived:

```bash
ojob ojob.io/kube/criOps op=list __format=ctable node=node1,node2,node3 [options for your kube distribution]
```

## Removing a specifc image from all nodes

After listing you might find a specific image in some or all nodes that you want to remove. To do this first ensure that there isn't any container running with the image you want to remove. If there is, the image on the node where the container is running won't be removed (you will see an error message for that node).

```bash
ojob ojob.io/kube/criOps op=rmi image=my/image:latest [options for your kube distribution]
```

You can remove just from specific nodes if necessary:

```bash
ojob ojob.io/kube/criOps op=rmi image=my/image:latest node=node1,node2,node3 [options for your kube distribution]
```

## Other operations

### Prune

To remove all ununsed images from nodes:

```bash
# From all nodes
ojob ojob.io/kube/criOps op=prune [options for your kube distribution]

# From specific nodes
ojob ojob.io/kube/criOps op=prune node=node1,node2,node3 [options for your kube distribution]

```

### Pull

To pull an image on all nodes to accelearate the pod startup time:

```bash
# From all nodes
ojob ojob.io/kube/criOps op=prune image=my/image:latest [options for your kube distribution]

# From specific nodes
ojob ojob.io/kube/criOps op=prune image=my/image:latest node=node1,node2,node3 [options for your kube distribution]

```

## Interactive mode

Additionaly you also have the option of launching a container on a specific node and use *crictl* directly:

```bash
ojob ojob.io/kube/criOps op=interacted node=node1 [options for your kube distribution]
```

## Custom options

| Option | Default value | Description |
|--------|---------------|-------------|
| ns | kube-system | The namespace to use to run the privileged container images to execute commands in each node |
| name | img* | The name of the pod, deployed in each node, that should be used. Note: to keep resource usage low the pods are launched sequentially in each node and not as a daemonset. |
| jobimg | nmaguiar/imgutils | You can specify a copy of the nmaguiar/imgutils running on a private registry. You can also provide another image as long as it provide *crictl* |

## Running without internet

To run without internet you will need:
* an OpenAF runtime (you can use a [static installation]](../concepts/static-installation.md) )
* the ojob.io/kube/criOps yaml file (e.g. wget https://ojob.io/kube/criOps.yaml)
* a copy of the *nmaguiar/imgutils*
* the OpenAF's Kube oPack (e.g. wget https://openaf.io/opacks/Kube.opack)

Then, on a folder of a target unix machine after installing the OpenAF runtime execute:

```bash
./opack install Kube.opack
```

Afterwards you are ready to run:

```bash
./ojob criOps.yaml op=list jobimg=myregistry/nmaguiar/imgutils [options for your kube distribution]
```