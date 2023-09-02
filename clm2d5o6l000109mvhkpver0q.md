---
title: "Day 35: Mastering ConfigMaps and Secrets in Kubernetes🔒🔑🛡️"
datePublished: Sat Sep 02 2023 18:34:49 GMT+0000 (Coordinated Universal Time)
cuid: clm2d5o6l000109mvhkpver0q
slug: day-35-mastering-configmaps-and-secrets-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693679613664/329b08f4-6703-41b0-84c9-9290bf52316d.png
tags: kubernetes, devops, configmap, 90daysofdevops, trainwithshubham

---

In Kubernetes, ConfigMaps and Secrets are used to store configuration data and secrets, respectively. ConfigMaps store configuration data as key-value pairs, while Secrets store sensitive data in an encrypted form.

* *Example:- Imagine you're in charge of a big spaceship (Kubernetes cluster) with lots of different parts (containers) that need information to function properly. ConfigMaps are like a file cabinet where you store all the information each part needs in simple, labeled folders (key-value pairs). Secrets, on the other hand, are like a safe where you keep important, sensitive information that shouldn't be accessible to just anyone (encrypted data). So, using ConfigMaps and Secrets, you can ensure each part of your spaceship (Kubernetes cluster) has the information it needs to work properly and keep sensitive information secure! 🚀*
    

## Today's task:

* Create a ConfigMap for your Deployment
    
* Create a ConfigMap for your Deployment using a file or the command line
    

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQF3BYNV3LYXSg/article-inline_image-shrink_1500_2232/0/1677929692190?e=1698883200&v=beta&t=Tlx0LVZBfB1hp4t9vUIRaSWf9xF9HCMyNKcVhAC8hZ8 align="left")

* Update the deployment.yml file to include the ConfigMap
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693679192110/47fc44a1-f758-4231-a464-febc7ad03bfa.png align="center")
    
* Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`
    
    ```yaml
    kubectl apply -f configmap.yml 
    ```
    
* Verify that the ConfigMap has been created by checking the status of the ConfigMaps in your Namespace.
    

Here, the environment variable application is included in the pod definition and gets its value from ConfigMap. The key application and the ConfigMap my-config-map are the sources of the value, which is specified in the field value.

**Apply the updated deployment using the command**

```yaml
 kubectl apply -f deployment.yml -n <namespace-name>
```

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQGjdgI73Bo_Hg/article-inline_image-shrink_1500_2232/0/1677937941612?e=1698883200&v=beta&t=pS68tjg8RD9kpHKHO3x7oDfD7y48WhcVo-qbZaZXF0A align="left")

This command will display the ConfigMap's metadata, data, and status are in detail.

```yaml
kubectl describe configmap <configmap-name> -n <namespace-name>
```

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQEruv7UFKpoTA/article-inline_image-shrink_1500_2232/0/1677938326401?e=1698883200&v=beta&t=GIGjd5OCri_J6xuqa8rgAWyRD9MsZ4BsGUR86YanFr4 align="left")

You can also use the following command to see all the environment variables defined in the pod:

```yaml
printenv
```

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQEMwDKvR4v4TQ/article-inline_image-shrink_1500_2232/0/1677938591398?e=1698883200&v=beta&t=-Zo4O2lx8QT2PGgi6DleX5XuCQuJOMr-mA-wuNzfYLw align="left")

## Task 2:

**Create a Secret for your Deployment**

**Create a Secret for your Deployment using a file or the command line**

**create a secret.yml file**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693679092168/7621155d-b83b-4769-a207-fe30b6354568.png align="center")

The secret's name and other details are included in the metadata section. The type indicates the secret's type, which in this instance is opaque. Put the password in the encrypted format.

**Update the deployment.yml file to include the Secret**

The deployment definition includes an environment variable env-secret whose value is taken from the secret. The value from the field specifies the source of the value, which is the Secret my-secret and the key password

**Apply the updated deployment using the command: kubectl apply -f deployment.yml -n &lt;namespace-name&gt;**

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQG_MtCtPZmqqA/article-inline_image-shrink_1500_2232/0/1677939307630?e=1698883200&v=beta&t=70bBhokglyJSkrsTNFKSGnjI6FitkVpv2GJebHCirEI align="left")

```yaml
kubectl get secrets -n <namespace-name>
```

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQHvt8jBD1CbLw/article-inline_image-shrink_1500_2232/0/1677939403014?e=1698883200&v=beta&t=MsywU524FQ_k8sUXyqF3SB7TtKMSWGJ2n1pqmce-I7I align="left")

You can also use the following command to view the details of a specific secret:

```yaml
kubectl describe secret <secret-name> -n <namespace-name>
```

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQGczuJW-klE0w/article-inline_image-shrink_1500_2232/0/1677939436301?e=1698883200&v=beta&t=_dtkug5GaYi26pgvao9JHs6rY6pPLawEQ5O_OmqQZL4 align="left")

***Happy Learning!***