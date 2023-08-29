---
title: "Day 33 Task: Working with Namespaces and Services in Kubernetes"
datePublished: Tue Aug 29 2023 17:55:24 GMT+0000 (Coordinated Universal Time)
cuid: cllwlzkqc000909m98sjd2h4j
slug: day-33-task-working-with-namespaces-and-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693331625639/b56c3ccd-117f-4009-b060-0992d0004807.png
tags: deployment, kubernetes, 90daysofdevops, trainwithshubham, kubernetes-namespaces

---

## What are Namespaces and Services in k8s

In Kubernetes, Namespaces are used to create isolated environments for resources. Each Namespace is like a separate cluster within the same physical cluster. Services are used to expose your Pods and Deployments to the network.

### TASK 1

**Create a Namespace for your Deployment**

**Use the below command  to create a Namespace**

```yaml
kubectl create namespace <namespace-name>
```

Create a . yml file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693330113552/544fcf06-b1d7-4ee0-8465-3fb757cd7ff0.png align="center")

The namespace in which the resources should be generated or changed is specified using the -n flag.

```yaml
kubectl apply -f namespace.yml -n <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693330205485/52be9b54-575f-45c9-b4ac-c8637f272f75.png align="center")

Check the status of the namespaces in your cluster to confirm that the namespace has been created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693330295945/221ef8cf-a7c2-4b58-81eb-c15717eec4e3.png align="center")

**Verify that the Namespace has been created by checking the status of the Namespaces in your cluster.**

```yaml
kubectl get namespaces
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693330225985/3f4f4be3-bb81-4326-abe3-be94c95d5b1c.png align="center")

### Task 2:

**Read about services, load balancing, and networking in Kubernetes.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693331138410/8d45d0bf-89e1-407b-b130-9e27c1465ace.png align="center")

**Service**: A set of pods and the access policies for them are defined by a Kubernetes service, which is an abstraction layer. Services can load balance traffic between pods and give a consistent IP address and DNS name. This allows for inter-pod communication and separates the client from the backend pods.

**Load balancing:** The built-in load balancer service provided by Kubernetes enables you to split incoming traffic among many pods in a cluster. This enhances the scalability and dependability of your applications.

**Networking:** In Kubernetes, networking is in charge of establishing connections between pods and between the cluster and external networks. Routing, IP address management, and network policy enforcement are all included in this. Plugins that are integrated with the underlying network infrastructure are used to implement networking in Kubernetes.

***Happy Learning!***