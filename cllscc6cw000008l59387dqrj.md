---
title: "Day 31 Task: Launching your First Kubernetes Cluster with Nginx running"
datePublished: Sat Aug 26 2023 18:14:11 GMT+0000 (Coordinated Universal Time)
cuid: cllscc6cw000008l59387dqrj
slug: day-31-task-launching-your-first-kubernetes-cluster-with-nginx-running
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693073605485/1ed6868b-e8c1-4418-913e-e9453810c330.png
tags: kubernetes, devops, minikube, 90daysofdevops, trainwithshubham

---

1. **What is minikube?**
    

*Ans*:- Minikube is a tool that quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. It can deploy as a VM, a container, or on bare metal.

Minikube is a pared-down version of Kubernetes that gives you all the benefits of Kubernetes with a lot less effort.

This makes it an interesting option for users who are new to containers, and also for projects in the world of edge computing and the Internet of Things.

1. **Features of minikube**
    

*Ans* :-

(a) Supports the latest Kubernetes release (+6 previous minor versions)

(b) Cross-platform (Linux, macOS, Windows)

(c) Deploy as a VM, a container, or on bare-metal

(d) Multiple container runtimes (CRI-O, containerd, docker)

(e) Direct API endpoint for blazing-fast image load and build

(f) Advanced features such as LoadBalancer, filesystem mounts, FeatureGates, and network policy

(g) Addons for easily installed Kubernetes applications

(h) Supports common CI environments

## Task-01:

## Install minikube on your local

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693071021714/c920e56d-2704-481f-ae7f-5c9597e3617e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693071671949/3c5fcc04-2f20-48e4-a749-8f55b4adba7c.png align="center")

To confirm the successful installation of both a hypervisor and Minikube, you can run the following command to start up a local Kubernetes cluster

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693072386909/086c9aee-4ad3-477a-8212-ffe2874026ad.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693072452881/c7a0ebbe-4d04-4193-939c-608974255bae.png align="center")

Now Minikube is installed and ready.

## Let's understand the concept of **pod**

**Pods** are the smallest deployable units of computing that you can create and manage in Kubernetes.

A Pod (as in a pod of whales or pea pod) is a group of one or more containers, with shared storage and network resources, and a specification for how to run the containers. A Pod's contents are always co-located and co-scheduled, and run in a shared context. A Pod models an application-specific "logical host": it contains one or more application containers that are relatively tightly coupled.

**Task 2:**

### Create your first pod on Kubernetes through Minikube.

Install kubectl using command

```bash
sudo snap install kubectl --classic
```

Create a folder, inside the folder create yml file/manifest file

pod.yml

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693073144937/a75c1d23-9500-4fec-af46-794bd686b76a.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693073048331/055523fc-fcf8-42b5-b6b1-02afe9546f0a.png align="left")

To check the list of pods:

```bash
kubectl get pods
```

You can view list of pods (ngnix pod) in the running state

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693073235834/c9ad0972-451c-4378-ae18-cc36e91b0871.png align="center")

**Happy Learning!**