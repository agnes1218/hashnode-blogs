---
title: "Day-48 - ECS"
datePublished: Fri Sep 22 2023 18:20:01 GMT+0000 (Coordinated Universal Time)
cuid: clmuxfom5000008mih5nr4pxq
slug: day-48-ecs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695406764000/e9fce932-2bee-4ee7-85fe-a188be886b5b.png
tags: aws, devops, ecs, trainwithshubham, 90daysofdevops-chanllenge

---

## What is ECS?

* ECS (Elastic Container Service) is a fully managed container orchestration service that Amazon Web Services (AWS) provides. It allows you to run and manage Docker containers on a cluster of virtual machines (EC2 instances) without having to manage the underlying infrastructure.
    

With ECS, you can easily deploy, manage, and scale your containerized applications using the AWS Management Console, the AWS CLI, or the API. ECS supports both "Fargate" and "EC2 launch types", which means you can run your containers on AWS-managed infrastructure or your own EC2 instances.

ECS also integrates with other AWS services, such as Elastic Load Balancing, Auto Scaling, and Amazon VPC, allowing you to build scalable and highly available applications. Additionally, ECS has support for Docker Compose and Kubernetes, making it easy to adopt existing container workflows.

Overall, ECS is a powerful and flexible container orchestration service that can help simplify the deployment and management of containerized applications in AWS.

## Difference between EKS and ECS?

* EKS (Elastic Kubernetes Service) and ECS (Elastic Container Service) are both container orchestration platforms provided by Amazon Web Services (AWS). While both platforms allow you to run containerized applications in the AWS cloud, there are some differences between the two.
    

**Architecture**: ECS is based on a centralized architecture, where there is a control plane that manages the scheduling of containers on EC2 instances. On the other hand, EKS is based on a distributed architecture, where the Kubernetes control plane is distributed across multiple EC2 instances.

**Kubernetes Support**: EKS is a fully managed Kubernetes service, meaning that it supports Kubernetes natively and allows you to run your Kubernetes workloads on AWS without having to manage the Kubernetes control plane. ECS, on the other hand, has its own orchestration engine and does not support Kubernetes natively.

**Scaling**: EKS is designed to automatically scale your Kubernetes cluster based on demand, whereas ECS requires you to configure scaling policies for your tasks and services.

**Flexibility**: EKS provides more flexibility than ECS in terms of container orchestration, as it allows you to customize and configure Kubernetes to meet your specific requirements. ECS is more restrictive in terms of the options available for container orchestration.

**Community**: Kubernetes has a large and active open-source community, which means that EKS benefits from a wide range of community-driven development and support. ECS, on the other hand, has a smaller community and is largely driven by AWS itself.

In summary, EKS is a good choice if you want to use Kubernetes to manage your containerized workloads on AWS, while ECS is a good choice if you want a simpler, more managed platform for running your containerized applications.

# Task :

Set up ECS (Elastic Container Service) by setting up Nginx on ECS.

1. **Create an ECS cluster:**
    

In the ECS service, click on "Create Cluster".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695211928354/6cfc2a71-6e8f-41cc-bd51-1bd81bdeae93.png align="center")

Configure the cluster settings, such as the cluster name, VPC, and subnet.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695211993643/32da746d-f3e5-4c66-878a-b7573338cb86.png align="center")

Click on 'Create'

**The cluster is successfully created**.

**2.Create a task definition:**

In the ECS service, click on "Task Definitions", and then click on "Create new Task Definition".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695404742257/0e71b806-9cdb-4457-9acf-d916e6829f01.png align="left")

Set the container name to "nginx", copy and paste Image url from 'Amazon ECR public gallery' site. Specify the port mappings for HTTP , by setting the "Container port" to 80.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695405865104/600100d5-394a-4b07-a6c5-565558d3139b.png align="center")

Browse Amazon ECR public gallery and search for nginx image and copy that image url.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695405924510/7199d413-c261-4719-8ca5-73800aff4a4d.png align="center")

Click next

Choose the Fargate launch type, Configure the task settings, such as the task memory and CPU limits, here CPU is .5vCPU and memory is 1GB.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695405975410/3f524b03-1168-493b-ac1e-a6c3ccf89168.png align="center")

Click on 'Create'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695406013648/81fedaad-89be-424b-9d5b-d62eb5cb7b37.png align="left")

1. **Create a service:**
    

In the ECS, click on "Clusters", and select the cluster that you created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695406387622/abed608c-6734-485a-b78b-a4ec4df663fd.png align="left")

Click on "Create Service.

Choose the task definition that you created in the above steps.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695406433459/35744f27-b52e-46d3-8bdb-efedae3e2e90.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695406450290/0d20bc40-1f50-4151-a66f-9fcf0c298490.png align="left")

Specify the port mappings for HTTP with port 80.

Click on Create

Service is successfully created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695406524215/1311267d-5729-41e1-9b77-e79a7c487f8e.png align="left")

1. **Test the Nginx container:**
    

Click on the 'Cluster' that you created.

Click on 'Test'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695406583720/e8e7ec8c-4692-4639-8191-53ec6d8f2e92.png align="left")

Browse the Public IP address, you can see the default Nginx welcome page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695406619685/a2fde596-8bd2-4483-9e2e-1b5636cfcf5c.png align="center")

***Happy Learning!***