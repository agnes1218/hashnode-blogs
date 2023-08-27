---
title: "Day 30 Task: Kubernetes Architecture"
datePublished: Fri Aug 25 2023 17:46:50 GMT+0000 (Coordinated Universal Time)
cuid: cllqvx5ub000308l36ijcfvy1
slug: day-30-task-kubernetes-architecture
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692985569672/adc5b00c-40cf-4c97-b944-c7904ecfe9b8.png
tags: kubernetes, devops, ci-cd, 90daysofdevops, trainwithshubham

---

## Kubernetes Overview

With the widespread adoption of [containers](https://cloud.google.com/containers) among organizations, Kubernetes, the container-centric management software, has become a standard to deploy and operating containerized applications and is one of the most important parts of DevOps.

Originally developed at Google and released as open-source in 2014. Kubernetes builds on 15 years of running Google's containerized workloads and the valuable contributions from the open-source community. Inspired by Google’s internal cluster management system.

## Tasks

1. **What is Kubernetes? Write in your own words and why do we call it k8s?**
    
    Kubernetes is open open-source container orchestration platform. It makes it easier to deploy and manage applications. It also enables to autoscale the application based on requirements.
    
    K8's is simply shortened to Kubernetes. The number 8 represents the number of letters skipped between the "K" and the "s" in the word "Kubernetes".
    
2. **What are the benefits of using K8s?**
    
    The benefits of using Kubernetes (k8s) :
    
    1. Run applications in containers efficiently.
        
    2. Keep applications up and running even if a node fails.
        
    3. Easily deploy and update applications.
        
    4. Scale applications to meet demand.
        
    5. Improve security for applications.
        
    6. Run applications in different environments with ease.
        
3. **Explain the architecture of Kubernetes.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692984480497/6cd42864-a7ab-4c06-aeb3-f27b4af5d6b5.png align="center")
    
    1. **Master Node**: The Master node acts as the control center for the cluster, managing the desired state of the cluster and ensuring that the actual state matches the desired state.
        
    2. **Worker Nodes**: Worker nodes are where your application containers run. They communicate with the Master node to receive instructions and report their status.
        
    3. **etcd** : etcd is a distributed key-value store that stores the configuration data for the cluster.
        
    4. **API Server** : The API Server is the main interface for communication between the Master node and the worker nodes. It exposes the Kubernetes API, which can be used to manage the cluster and deploy applications.
        
    5. **Controller Manager**: The Controller Manager is responsible for running various controllers that regulate the state of the cluster, such as the replication controller and endpoints controller.
        
    6. **Scheduler**: The Scheduler is responsible for assigning pods to worker nodes based on resource requirements and constraints.
        
    7. **kubelet** : kubelet is a process running on each worker node that communicates with the Master node to receive instructions and ensure the containers are running as intended.
        
    8. **kubectl** : kubectl is the command-line interface for interacting with the Kubernetes API.
        

**4\. What is a Control Plane?**

The Control Plane manages the worker nodes and the Pods in the cluster. In production environments, the control plane usually runs across multiple computers and a cluster usually runs multiple nodes, providing fault-tolerance and high availability. Components of the Control Plane include API server, etcd, scheduler, and controller manager.

**5\. Write the difference between kubectl and kubelets**

kubectl is the command-line interface (CLI) tool for working with a Kubernetes cluster. It communicates with the API server to perform various operations on the cluster, such as deploying applications, scaling resources, and inspecting logs.

Kubelet is the technology that applies, creates, updates, and destroys containers on a Kubernetes node.

**6\. Explain the role of the API server.**

The API server is a main component of Kubernetes that enables users and applications to interact with and manage resources. All administrative operations, including creating, updating, and deleting resources like pods, services, deployments, and namespaces, are initiated by sending API requests to the API server. API Server is also responsible for the authentication and authorization mechanism. All API clients should be authenticated in order to interact with the API Server. REST operations validate them, and update the corresponding objects in etcd.

***Happy Learning!***