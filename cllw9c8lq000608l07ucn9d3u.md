---
title: "Day 32 Task: Launching your Kubernetes Cluster with Deployment"
datePublished: Tue Aug 29 2023 12:01:20 GMT+0000 (Coordinated Universal Time)
cuid: cllw9c8lq000608l07ucn9d3u
slug: day-32-task-launching-your-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693310376375/570e375b-e46f-4085-aa33-4967fe34eeeb.png
tags: docker, kubernetes, ci-cd, 90daysofdevops, trainwithshubham

---

## What is Deployment in k8s

A Deployment provides a configuration for updates for Pods and ReplicaSets.

You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new replicas for scaling or to remove existing Deployments and adopt all their resources with new Deployments.

## Task-1:

**Create one Deployment file to deploy a sample todo-app on K8s using the "Auto-healing" and "Auto-Scaling" feature**

**Auto-Healing** ensures that if a Pod fails or terminates unexpectedly, Kubernetes automatically replaces it to maintain the desired number of replicas.

**Auto-Scaling** allows you to automatically adjust the number of replicas based on resource utilization, ensuring that your application can handle increased load without manual intervention.

**Add a deployment.yml file**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693308885494/b214364e-9f8e-42e1-a8ce-490eea7a84b9.png align="center")

This manifest defines a Deployment named "todo-app" that manages two replicas of the ToDo application. Each replica runs in a Pod with a single container named "todo," which uses the "agnes1/node-todo" Docker image and listens on port 8000.

**To list a deployment:**

Apply the deployment to your k8s (minikube) cluster by command

`kubectl apply -f deployment.yml`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693309146438/7e653bce-067a-4207-8d9e-3f4a65a7083a.png align="center")

```yaml
kubectl get deployments
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693309188988/4f59e290-a5c9-49eb-a288-1ddd50ca340c.png align="center")

Thank you for reading!  

***Happy Learning!***