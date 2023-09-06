---
title: "Day 36 Task: Managing Persistent Volumes in Your Deployment 💥"
datePublished: Wed Sep 06 2023 08:09:27 GMT+0000 (Coordinated Universal Time)
cuid: clm7gkux3000209lbficm8rr1
slug: day-36-task-managing-persistent-volumes-in-your-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693987704966/b5e681ff-97cd-416f-99a1-ad9f421c290f.png
tags: kubernetes, devops, 90daysofdevops, kubernetes-persistent-volumes, trainwithshubham

---

## What are Persistent Volumes in K8s

In Kubernetes, a Persistent Volume (PV) is a piece of storage in the cluster that has been provisioned by an administrator. A Persistent Volume Claim (PVC) is a request for storage by a user. The PVC references the PV, and the PV is bound to a specific node.

## Today's tasks:

### Task 1:

**Add a Persistent Volume to your Deployment todo app.**

* Create a file `pv.yaml` and write the code for Persistent Volume.
    
    ```yaml
    apiVersion: v1
    kind: PersistentVolume
    metadata:
      name: pv-todo-app
    spec:
      capacity:
        storage: 1Gi
      accessModes:
        - ReadWriteOnce
      persistentVolumeReclaimPolicy: Retain
      hostPath:
        path: "/tmp/data"
    ```
    
    ```yaml
    kubectl apply -f pv.yaml
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693984650765/e7ee1017-1fe6-4edc-b01e-f1ec5a43a23b.png align="center")
    
    * Create a file `pvc.yaml` and write the code for Persistent Volume Claim.
        
        ```yaml
        apiVersion: v1
        kind: PersistentVolumeClaim
        metadata:
          name: pvc-todo-app
        spec:
          accessModes:
            - ReadWriteOnce
          resources:
            requests:
              storage: 500Mi
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693984936856/77af087a-183b-4523-80dc-db6a782bbcea.png align="center")
        
        * Create a file `deploymentvolumes.yaml` and write the code for Deployment.
            

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
  labels:
    app: todo
spec:
  replicas: 1
  selector:
    matchLabels:
      app: todo
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
      - name: todo
        image: agnes1/todo
        ports:
        - containerPort: 8000
        volumeMounts:
         - name: todo-app-data
           mountPath: /app
      volumes:
        - name: todo-app-data
          persistentVolumeClaim:
            claimName: pvc-todo-app
```

```yaml
kubectl apply -f Deployment.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693985309551/3a09c278-f09f-4af6-9ec8-594af0d838b9.png align="center")

* Verify that the Persistent Volume has been added to your Deployment by checking the Pods and Persistent Volumes status in your cluster. Use these commands.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693985419815/d107b784-5de2-46da-80d6-5f9fa6401733.png align="center")
    

### Task 2:

Accessing data in the Persistent Volume,

```yaml
kubectl exec -it <pod-name> -- /bin/bash
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693986383540/c9f088ce-ce68-4a39-9079-6ab0d363d75a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693986358554/50fcba29-8596-45f9-b4a2-e38851de5ae9.png align="center")

delete the pod that we used in the above step and create a new pod using the command kubectl apply -f deployment.yaml

Go inside a pod using kubectl exec command, then go to the app folder and check the todo.txt file.

Hope you find this article helpful!

***Happy Learning!***