---
title: "Project - Deployment of a Reddit-Clone Application On Kubernetes"
datePublished: Sun Aug 27 2023 17:28:01 GMT+0000 (Coordinated Universal Time)
cuid: clltq4ngn000709kv34eacaud
slug: project-deployment-of-a-reddit-clone-application-on-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693150673080/9c86d201-4b67-415f-9628-d342e8ccb9d7.png
tags: kubernetes, devops, reddit, ingress, trainwithshubham

---

## Pre-requisite:

We need to make sure we have the following prerequisites installed:

1. EC2 ( AMI- Ubuntu, Type- t2.medium )
    
2. Docker
    
3. Minikube
    
4. kubectl
    

# Steps:-

# For Docker Installation

sudo apt-get update

sudo apt-get install [docker.io](http://docker.io) -y

sudo usermod -aG docker $USER && newgrp docker

# For Minikube & Kubectl

curl -LO [https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64](https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64) sudo install minikube-linux-amd64 /usr/local/bin/minikube

sudo snap install kubectl --classic

minikube start --driver=docker

`Kubectl get pods` \- To verify kubectl is installed

Once everything is set, let's start with deploying the Reddit clone app.

# **Step 1: Clone the source code**

The first step is to clone the source code for the app. You can do this by using this command `git clone` [`https://github.com/LondheShubham153/reddit-clone-k8s-ingress.git`](https://github.com/LondheShubham153/reddit-clone-k8s-ingress.git)

# **Step 2: Containerize the Application using Docker**

* Write a Dockerfile with the following code:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693138193825/0d919ba4-a980-460c-8963-b4f0d406444c.png align="center")

* **Base Image**: The Dockerfile starts with a `node:19-alpine3.15` base image, which is the official Node.js image from version 19 with Alpine Linux 3.15.
    
* **Working Directory**: The working directory inside the container is set to `/reddit-clone`.
    
* **Copy Source Code**: The contents of the local directory where the Dockerfile resides are copied into the `/reddit-clone` directory in the container.
    
* **Install Dependencies**: The `npm install` command is executed to install the Node.js application's dependencies.
    
* **Expose Port**: The Dockerfile exposes port 3000 in the container, which is where the Node.js application will listen for incoming connections.
    
* **Default Command**: The default command for the container is set to, which likely starts the Reddit clone application in development mode.
    

# **Step 3) Building Docker-Image**

Now it's time to build a Docker Image from this Dockerfile. `docker build -t <DockerHub_Username>/<Imagename> .` use this command to build a docker image

## **Step 4)Push the Image to DockerHub**

1. `Docker login` - Log in to the docker hub account with username and password.
    
2. Then use `docker push <DockerHub_Username>/<Imagename>` for pushing to the DockerHub.
    
3. Once the docker image is push to docker hub you can check the image from login to docker hub
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693151758806/2bcc44e1-333e-4fc4-828f-4539e24ac7fd.png align="center")
    

## **Step 5) Creating a Manifest file**

Deploy to Kubernetes or create Kubernetes resources like a pod, replica-set, config map, secret, deployment, etc., You need to write a file called manifest that describes that object and its attributes either in yaml or JSON. Each YAML file typically corresponds to a single Kubernetes resource, such as a Deployment, Service, ConfigMap, or Ingress.

## **Deployment Server**

* Create a folder named "K8s" on the Deployment Server.
    
* Inside the "K8s" folder, create a file named "Deployment.yml" and add the following content
    

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: reddit-clone-deployment
  labels:
    app: reddit-clone
spec:
  replicas: 2
  selector:
    matchLabels:
      app: reddit-clone
  template:
    metadata:
      labels:
        app: reddit-clone
    spec:
      containers:
      - name: reddit-clone
        image: agnes1/reddit-clone
        ports:
        - containerPort: 3000
```

* `apiVersion`: Specifies the API version of the resource. In this case, it's using the `apps/v1` version for Deployments.
    
* `kind`: Specifies the kind of resource, which is a Deployment in this case.
    
* `metadata`: Provides metadata about the Deployment resource, including its name and labels.
    
* `spec`: Defines the desired state of the Deployment.
    
    `replicas`: Specifies the desired number of replicas (instances) of the application to run, which is set to 2.
    
    `selector`: Specifies the label selector used to match the Pods managed by this Deployment.
    

* `template`: Specifies the Pod template used to create the Pods.
    
    `metadata`: Defines labels for the Pod template.
    
* `spec`: Defines the specification of the Pod template.
    
    `containers`: Defines the containers to run in the Pods.
    
    `name`: Specifies the name of the container.
    
    `image`: Specifies the Docker image to use for the container.
    
    `ports`: Specifies the ports that the container listens on.
    
    `containerPort`: Specifies the port number that the container listens on.
    

**Apply the Deployment file to create pods:**

```yaml
kubectl apply -f Deployment.yml
```

### **Kubernetes Service**

Inside the "K8s" folder, create a file named "Service.yml" and add the following content:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: reddit-clone-service
  labels:
    app: reddit-clone
spec:
  type: NodePort
  ports:
  - port: 3000
    targetPort: 3000
    nodePort: 31000
  selector:
    app: reddit-clone
```

* `type: NodePort`: This specifies the type of service to create, which is a NodePort service. A NodePort service exposes a specific port on all nodes of the cluster, allowing external traffic to be routed to the service.
    
* `ports`: This section specifies the port configuration for the service.
    
    * `port: 3000`: This is the port number that the service will listen on. It's the port that you'll use to access the service from outside the cluster.
        
    * `targetPort: 3000`: This is the port number that the pods of the associated Deployment or Pods are listening on. It's where the service will route incoming traffic.
        
    * `nodePort: 31000`: This is the node port that will be assigned within the range 30000-32767. It's the port you'll use to access the service externally through the node's IP address.
        
    
    **Apply the Service file to create a service:**
    
    ```yaml
    kubectl apply -f Service.yml
    ```
    

## **Step 6) Configure Ingress**

Ingress resources in Kubernetes provide a way to manage external access to your services using rules and configurations. They are particularly useful for managing HTTP and HTTPS traffic and allow you to centralize and manage routing rules without modifying your service deployments.

**write ingress.yml and put the following code in it:**

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-reddit-app
spec:
  rules:
  - host: "domain.com"
    http:
      paths:
      - pathType: Prefix
        path: "/test"
        backend:
          service:
            name: reddit-clone-service
            port:
              number: 3000
  - host: "*.domain.com"
    http:
      paths:
      - pathType: Prefix
        path: "/test"
        backend:
          service:
            name: reddit-clone-service
            port:
              number: 3000
```

* `apiVersion`: Specifies the API version for the Ingress resource.
    
* `kind`: Specifies the kind of resource, which is an Ingress in this case.
    
* `metadata`: Provides metadata about the Ingress resource, including its name.
    
* `spec`: Defines the specifications for the Ingress resource.
    
* `rules`: Specifies routing rules based on different hostnames.
    
    * The first rule routes traffic from the hostname "[domain.com](http://domain.com)" to the "Reddit-clone-service" on path "/test". The path type is set to Prefix, which means it matches URLs that start with "/test".
        
    * The second rule uses a wildcard (`*.`[`domain.com`](http://domain.com)) to match any subdomain of "[domain.com](http://domain.com)" and route traffic to the same "reddit-clone-service" on the same "/test" path.
        

Each rule has a `http` section, which defines the path-based routing within that rule.

* `paths`: Specifies the path routing configuration.
    
    * `pathType: Prefix`: Specifies that the path should match URLs that start with the specified path.
        
    * `path: "/test"`: Specifies the path to match.
        
* `backend`: Defines the backend service to route traffic to.
    
    * `service`: Specifies the name of the service, which is "reddit-clone-service" in this case.
        
    * `port`: Specifies the port number of the service to route traffic to, which is 3000.
        

In summary, this Ingress resource defines routing rules for accessing the "Reddit-clone-service" based on different hostnames and paths. It routes traffic to the service on the "/test" path for both the main domain ("[domain.com](http://domain.com)") and any subdomains ("\*.[domain.com](http://domain.com)").

In Minikube, the Ingress addon needs to be enabled explicitly before you can use it to manage Ingress resources.

`minikube addons enable ingress` command.

check the current setting for addons in Minikube use `minikube addons list` command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693150986908/75355d50-77e8-4ac1-b9fd-3ad2af798da3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693150965864/ff624ddf-86c9-45ee-85d1-779decd9dc89.png align="center")

### **Step 7) Expose the Application to the Internet**

1. We need to expose our deployment so use `kubectl expose deployment reddit-clone-deployment --type=NodePort` command.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693150928680/59deed92-7d13-4b19-981f-e69e609519e3.png align="center")

The `kubectl expose` The command provided is used to create a Service that exposes a Kubernetes Deployment. In this case, you're exposing the `reddit-clone-deployment` Deployment as a NodePort Service. This will make the pods managed by the deployment accessible from outside the cluster.

After running this command, Kubernetes will create a new NodePort Service based on the specified Deployment.

1. You can test your deployment using curl -L [http://54.193.116.32:3100/](http://54.193.116.32:3000/) is a [54.193.116.32](http://54.193.116.32:3000/) minikube ip & Port **31000** is defined in Service.yml
    
2. We have to expose our app service `kubectl port-forward svc/reddit-clone-service 3000:3000 --address 0.0.0.0 &`
    
    By running this command, you'll be able to access the application running inside your cluster using a web browser or any other tool that can connect to [`http://localhost:3000`](http://localhost:3000). The forwarded traffic is proxied through your local machine to the selected pod in your cluster.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693150904638/5bb1e5f9-f195-4dfe-92e4-fd3f10abbbdb.png align="center")

1. Make sure the port 3000 inbound rule is added in the security group.
    

## **Step 8 ) Acess your Reddit clone app**

You can access the Reddit clone app **Ec2\_ip:3000**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693156897045/7105777f-b789-4fd8-831f-a4280b1691d8.png align="center")

You've successfully deployed a Reddit clone web app on a Kubernetes cluster hosted on AWS

*Happy Learning!*