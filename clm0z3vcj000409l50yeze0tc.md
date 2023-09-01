---
title: "Day 34 Task: Working with Services in Kubernetes"
datePublished: Fri Sep 01 2023 19:13:44 GMT+0000 (Coordinated Universal Time)
cuid: clm0z3vcj000409l50yeze0tc
slug: day-34-task-working-with-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693595554658/6a0cd60f-f1cb-46e9-a9b9-006443586452.png
tags: kubernetes, devops, services, 90daysofdevops, trainwithshubham

---

## What are Services in K8s

In Kubernetes, Services are objects that provide stable network identities to Pods and abstract away the details of Pod IP addresses. Services allow Pods to receive traffic from other Pods, Services, and external clients.

## Task-1:

* **Create a Service for your todo-app Deployment from Day-32**
    
* **Create a Service definition for your todo-app Deployment in a YAML file.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693592103794/e7759d18-40e9-4859-b570-b3ab7723a8ec.png align="left")
    

The YAML manifest defines a Kubernetes Service of type NodePort named "todo-service" for exposing your application.

`spec`: Defines the specification for the Service.

* `selector`: Specifies the set of Pods that this Service will route traffic to. It matches Pods with the label "app: todo," which is typically the label used in your Deployment.
    
* `ports`: Defines the ports that the Service should listen on and forward traffic to.
    
    * `protocol`: The network protocol to use (TCP in this case).
        
    * `port`: The port on which the Service should listen within the cluster (usually 80 for HTTP).
        
    * `targetPort`: The port to which traffic should be forwarded in the Pods (8000, which is the container port in your Deployment).
        
* `type`: Specifies the type of Service. In this example, it's "NodePort," which exposes the Service on a high-numbered port on each node in the cluster. Clients can access the Service using any node's IP address and the assigned NodePort.
    
* Apply the Service definition to your K8s (minikube) cluster using the `kubectl apply -f service.yml -n <namespace-name>` command.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693592079373/4609a3d2-8aa8-478f-baf0-28379e7628b2.png align="center")

The **kubectl get svc** command is used to list Services in a Kubernetes cluster. The **\-n** option is used to specify the namespace where the Service is located.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693592326920/3f435ba9-fc31-460d-8dbd-f827365a997c.png align="center")

* Verify that the Service is working by accessing the todo-app using the Service's IP and Port in your Namespace.
    

```yaml
minikube service <service_name> -n=<namespace> --url
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693593239838/f819d51f-53e9-4ec1-ae38-21736d7a245d.png align="center")

Curl request to the Service using its IP address:

1. Access the todo-app using the Service’s IP and Port:
    

```yaml
curl -L <service-ip>:<service-port>
curl -L http://192.168.49.2:30080
```

If the NodePort Service is working correctly, you should see the response from the todo-app.

## Task-2:

* **Create a ClusterIP Service for accessing the todo-app from within the cluster**
    
* **Create a ClusterIP Service definition for your todo-app Deployment in a YAML file.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594036913/6e7dcb31-4ccd-422d-b4ad-58e3217ddf14.png align="center")

* Apply the ClusterIP Service definition to your K8s (minikube) cluster using the `kubectl apply -f cluster-ip-service.yml -n <namespace-name>` command.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693593992973/7649bc7c-64c6-4008-87a0-22643bb54656.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594011524/2d865b8d-4684-4e35-beb9-27f6b3a80b12.png align="center")

* Verify that the ClusterIP Service is working by accessing the todo-app from another Pod in the cluster in your Namespace.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594085454/73a11932-1a51-43e9-8a18-34892dea34ed.png align="center")
    
    Note the name of another Pod in the same Namespace.
    
    Exec into the Pod: go inside container
    
    1. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594207884/3d9373cd-d7ce-443f-8d21-f622f933d7d8.png align="center")
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594327176/259d88fa-f4cb-4ab2-a172-c6df955695fc.png align="left")
    

## Task-3:

**Create a LoadBalancer Service for accessing the todo-app from outside the cluster**

**Create a LoadBalancer Service definition for your todo-app Deployment in a YAML file.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594664067/02b781a7-2a85-4baa-a741-22e942775b61.png align="center")

In this example, the Service is named **todo-lb-service** and is of type **LoadBalancer**. The selector **app: todo** is used to determine which Pods to associate with the Service.

**Apply the LoadBalancer Service definition to your K8s (minikube) cluster using the kubectl apply -f service.yml -n &lt;namespace-name&gt; command.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594737048/725fc915-4cf8-4c52-9109-4c68cefe9cbe.png align="center")

**Verify that the LoadBalancer Service is working by accessing the todo-app from outside the cluster in your Namespace.**

**Get the LoadBalancer service:**

```yaml
kubectl get services -n <namespace> 
```

The Minikube service command is used to interact with services in a Minikube cluster. The --url option will return the URL that you can use to access the Service in your browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693594931172/107a7ceb-a2ad-441d-80e7-8259a1ab79c7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693595003106/cfd89996-1828-4b61-8a97-25c59ebf5dc9.png align="center")

Note the lb ip and port

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693595068389/9b9a15d5-8b67-43e0-94c4-8ca384b7556c.png align="center")

***Happy Learning!***