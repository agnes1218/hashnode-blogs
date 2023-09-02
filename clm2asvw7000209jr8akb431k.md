---
title: "Deployment of microservices on k8s (Flask-app Mongodb)"
datePublished: Sat Sep 02 2023 17:28:53 GMT+0000 (Coordinated Universal Time)
cuid: clm2asvw7000209jr8akb431k
slug: deployment-of-microservices-on-k8s-flask-app-mongodb
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693672372242/c55b5096-1b16-4ed9-9780-034a624fd7de.png
tags: microservices, deployment, kubernetes, devops, trainwithshubham

---

## Pre-requisites

* Ubuntu OS (Xenial or later)
    
* sudo privileges
    
* Internet access
    
* t2.medium instance type or higher
    

### **Setup Master and Worker Node**

Run the following commands on both the master and worker nodes to prepare them for kubeadm.

```yaml
sudo su
apt update -y
apt install docker.io -y

systemctl start docker
systemctl enable docker

curl -fsSL "https://packages.cloud.google.com/apt/doc/apt-key.gpg" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg
echo 'deb https://packages.cloud.google.com/apt kubernetes-xenial main' > /etc/apt/sources.list.d/kubernetes.list

apt update -y
apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
```

## Master Node

1. Initialize the Kubernetes master node.
    
    ```yaml
    sudo su
    kubeadm init
    ```
    
2. Set up local kubeconfig (both for the root user and normal user):
    
    ```yaml
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
    ```
    
3. Apply Weave network:
    
    ```yaml
    kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
    ```
    
4. Generate a token for worker nodes to join:
    
    ```yaml
    kubeadm token create --print-join-command
    ```
    
    ## Worker Node
    
    1. Run the following commands on the worker node.
        
        ```yaml
        sudo su
        kubeadm reset pre-flight checks
        ```
        
    2. Paste the join command you got from the master node and append `--v=5` at the end.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693672829210/71855c8a-b13d-4bbd-bb66-bc84df004a7b.png align="center")
        
        ## Installation
        
        To install and run the application on your Kubernetes cluster, follow these steps:
        
        1. Clone this repository to your local machine.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693672889534/ee239196-6317-4f52-bd68-ab96bda64a0a.png align="center")
            
        2. Navigate to folder
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693672967778/51fdc4f9-2f7c-4bc5-a13c-30bf0e07c94e.png align="center")
            
        3. Create a manifest file
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693673174935/ded24b1f-5a9b-47c5-b24d-8ec4433a362b.png align="center")
            
            Deployment manifest:
            
            * `apiVersion` and `kind`: These fields specify the API version and the resource type, which is a Deployment in this case.
                
            * `metadata`: This section contains metadata for the Deployment, including its name and labels. Labels are useful for selecting and categorizing resources.
                
            * `spec`: This is where you define the desired state of the Deployment.
                
                * `replicas`: Specifies the number of replicas (pods) that you want to run. In your case, it's set to 1, meaning there will be one pod running.
                    
                * `selector`: Defines how the Deployment selects which pods to manage based on labels. It matches pods with the label `app: taskmaster`.
                    
                * `template`: Describes the pod template that the Deployment uses to create new pods.
                    
                    * `metadata`: Contains labels for pods created by this template.
                        
                    * `spec`: Defines the specification for the pod.
                        
                        * `containers`: Specifies the containers running in the pod. In this case, there's one container named "taskmaster" using the specified Docker image.
                            
                        * `ports`: Lists the ports that the container exposes. Port 5000 is exposed in this example.
                            
                        * `imagePullPolicy`: Specifies the policy for pulling the container image. "Always" means it will always attempt to pull the latest image.
                            
        4. `kubectl apply` command to create the Deployment in your Kubernetes cluster:
            
            ```yaml
            kubectl apply -f taskmaster-deployment.yaml
            ```
            
            1. ```yaml
                kubectl get pods
                ```
                
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693673045935/7857d480-de2e-4461-8306-fe70c5b1c2d9.png align="center")
        
        You can check worker node is app is running or not
        
        `docker ps` command is used to list the running Docker containers on your local system.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693673561447/2add773b-f8cb-4fc2-a194-a179869960fb.png align="center")

To scale the application to 3 apps we can run the below command on a worker node.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693673620286/69190701-fa96-4289-9303-fdaa02eaba86.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693673666344/3c03769f-0186-464e-b430-ab81bd156d46.png align="center")

Now that the app is running we need to communicate these with externally for that we will create a service.yml file in the master node

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693673807275/460d0ff0-01bb-44e6-8dd1-8f04fe3f5032.png align="center")

Kubernetes Service manifest creates a Service named "taskmaster-svc" with the following configuration:

* `metadata`: This section contains metadata for the Service, including its name.
    
* `spec`: This is where you define the specifications for the Service.
    
    * `selector`: Specifies how the Service should select pods to route traffic to. In this case, it selects pods with the label `app: taskmaster`. This label should match the label used in your Deployment or pods.
        
    * `ports`: Defines the ports that the Service should listen on and forward traffic to.
        
        * `port`: Specifies the port on which the Service will listen within the cluster. In this case, it's set to port 80, which means that the Service will listen on port 80 within the cluster.
            
        * `targetPort`: Specifies the port to which traffic should be forwarded inside the pods. It's set to port 5000, which is the port your "taskmaster" application is running on inside the pods.
            
        * `nodePort`: This field specifies a port on the node itself (in this case, 30007) to expose the Service externally. When using `NodePort` type, the Service will be accessible on all cluster nodes at this port.
            
    * `type`: Sets the type of the Service. In this case, it's set to `NodePort`, which means the Service will be accessible from outside the cluster at the specified `nodePort`.
        

To deploy this Service, save it to a YAML file (e.g., `taskmaster-service.yaml`) and use the `kubectl apply` command to create the Service in your Kubernetes cluster:

```yaml
kubectl apply -f taskmaster-service.yaml
```

Once applied, you can access your "taskmaster" application externally by connecting to any node in your cluster on the specified `nodePort`, which in this case is 30007. For example, if your cluster's node has an IP address of `<NODE_IP>`, you can access your service at `<NODE_IP>:30007`.

Keep in mind that using `NodePort` for external access may not be suitable for production environments as it exposes your service on a static port on every node, which may not scale well.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693673907630/c5131819-9bef-4704-bf3b-15ebe723750a.png align="center")

Now application is deployed and able to external access.

Let's move ahead and deploy MongoDB .

Firstly we need to create a persistent volume  
**Create a Persistent Volume (PV)**: You can define a Persistent Volume that represents a piece of storage in your cluster. PVs can be provisioned statically or dynamically, depending on your needs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693674593417/f3a00ced-d3a3-4ef0-b99f-64f2af1ea138.png align="center")

* `apiVersion` and `kind`: These fields specify the API version and resource type, which is a Persistent Volume (`v1` and, respectively).
    
* `metadata`: This section contains metadata for the Persistent Volume, including its name.
    
* `spec`: This is where you define the specifications for the Persistent Volume.
    
    * `capacity`: Specifies the storage capacity of the PV. In this case, it's set to 256Mi (256 megabytes).
        
    * `accessModes`: Describes how the PV can be accessed by pods. In this example, it's set to "ReadWriteOnce," which means the PV can be mounted as read-write by a single pod at a time.
        
    * `hostPath`: Specifies that the storage for this PV will be provided by a directory on the host machine (`/tmp/db` in this case). This is often used for development and testing purposes, but it's not suitable for production deployments because it doesn't provide data persistence across nodes or cluster failures.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693674508284/f7047ef1-3228-43e2-8568-5f77647aec43.png align="center")

**Create a Persistent Volume Claim (PVC)**: PVCs are requests for storage by pods. They are used to claim storage from available PVs

This PVC definition is requesting storage resources with read-write access and a capacity of 256Mi.

To use this PVC, you would typically include it in a pod definition as a volume claim.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693674717658/6f5199e0-b9a0-433b-90ea-ee1f75ae0ea5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693674862337/c7a4e495-99bc-402b-ba65-ef8443d27d57.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693674877703/f08de4ce-326a-4171-bf2e-895dc8e758f2.png align="center")

The YAML manifest defines a Kubernetes Deployment for a MongoDB containerized application that uses a Persistent Volume Claim (PVC) for data storage.

Let's break down the key components of this Deployment:

* `apiVersion` and `kind`: These fields specify the API version and resource type, which is a Deployment (`apps/v1` and deployment, respectively).
    
* `metadata`: This section contains metadata for the Deployment, including its name and labels.
    
* `spec`: This is where you define the desired state of the Deployment.
    
    * `selector`: Specifies how the Deployment selects pods to manage based on labels. In this case, it selects pods with the label `app: mongo`.
        
    * `template`: Describes the pod template that the Deployment uses to create new pods.
        
        * `metadata`: Contains labels for pods created by this template. In this case, pods created by this Deployment will have the label `app: mongo`.
            
        * `spec`: Defines the specification for the pod.
            
            * `containers`: Specifies the containers running in the pod. There's one container named "mongo" using the official MongoDB image. It exposes port 27017, which is the default MongoDB port.
                
            * `volumeMounts`: This section defines where the PVC will be mounted inside the pod. It mounts the PVC named "storage" at the path `/data/db`.
                
    * `volumes`: Defines the volumes that can be used by the pods created by this template.
        
        * `name`: Specifies the name of the volume, which is "storage" in this case.
            
        * `persistentVolumeClaim`: This section specifies that the volume is backed by a Persistent Volume Claim (PVC) named "mongo-pvc."
            

This Deployment is designed to create pods running the MongoDB container with access to persistent storage. The "storage" volume is backed by the "mongo-pvc" PVC, ensuring that data stored in the `/data/db` path inside the pod persists across pod restarts and reschedules.

```yaml
kubectl apply -f mongo.yaml
```

Kubernetes will create the Deployment, and the pods it manages will automatically have access to the specified PVC for data storage.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693675079952/74dddc23-89ed-4c54-8311-c8ca568a9be2.png align="center")

You can verify the db by accessing the worker node.

Now get external access with the below service.yml file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693675267851/c65d2474-d80e-4560-8561-463cb77d7e26.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693675299226/77c516dc-85ce-4827-8732-d34d6b8bae91.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693675118460/5394d62a-d9f3-4024-a312-7f7f30d9228d.png align="left")

***Happy Learning!***