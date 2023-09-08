---
title: "Day 41: Setting up an Application Load Balancer with AWS EC2 🚀 ☁"
datePublished: Fri Sep 08 2023 10:36:25 GMT+0000 (Coordinated Universal Time)
cuid: clmagpk77002y08jk5lma4j3e
slug: day-41-setting-up-an-application-load-balancer-with-aws-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694169318531/974d8709-b71a-43df-9776-4849bb0c8193.png
tags: aws, devops, apache, load-balancer, 90daysofdevops

---

## What is Load Balancing?

Load balancing is the distribution of workloads across multiple servers to ensure consistent and optimal resource utilization. It is an essential aspect of any large-scale and scalable computing system, as it helps you to improve the reliability and performance of your applications.

## Elastic Load Balancing:

**Elastic Load Balancing (ELB)** is a service provided by Amazon Web Services (AWS) that automatically distributes incoming traffic across multiple EC2 instances. ELB provides three types of load balancers:

1. **Application Load Balancer (ALB)** - *operates at layer 7 of the OSI model and is ideal for applications that require advanced routing and microservices.*
    
2. **Network Load Balancer (NLB)** - *operates at layer 4 of the OSI model and is ideal for applications that require high throughput and low latency.*
    
3. **Classic Load Balancer (CLB)** - *operates at layer 4 of the OSI model and is ideal for applications that require basic load balancing features.*
    

## 🎯 Today's Tasks:

### Task 1:

* **launch 2 EC2 instances with an Ubuntu AMI and use User Data to install the Apache Web Server**
    

Log in to your AWS Console and go to the EC2 dashboard.

Click on the "Launch Instance" button and select "Ubuntu Server ".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694166608550/5264babc-bea0-4266-a2cf-ca5cce306592.png align="center")

In the "Configure Instance Details" page, scroll down to the "Advanced Details" section and expand the "User data" field.

In the "User data" field, enter the following commands to install and start the Apache web server:

add below data

```yaml
#!/bin/bash
sudo apt update
sudo apt install -y apache2
sudo systemctl start apache2
sudo systemctl enable apache2
```

You can see two instances are created

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694166824222/33f940db-614a-4084-9526-54d2f1c5c5fe.png align="center")

**Modify the index.html file to include your name so that when your Apache server is hosted, it will display your name Also do it for 2nd instance which includes " TrainWithShubham Community is Super Awesome :) ".**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694166973825/6bea7e7f-6041-4eb6-95a2-dd9ecfac6795.png align="center")

Go inside /var/www/html path and edit the index.html file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694167408136/73f8b13c-a20c-4ac2-9c36-988f78c4fd86.png align="center")

Change the `index.html` file in `/var/www/html` directory

Now check the **Public IP** of instance 1 and you will see the **HTML** is running on the IP address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694168108124/9faa1120-2411-4b0d-a873-a6bfd7e5d059.png align="center")

Apache Server 2 Instance:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694168077492/3c1e1b51-be10-4fa5-b434-af61c4bb2189.png align="center")

Change the `index.html` file in `/var/www/html` directory

Now check the **Public IP** of instance 1 and you will see the **HTML** is running on the IP address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694168213508/a98f49cf-64b2-4e34-a900-145c03725fe7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694168394287/7b6a073a-c103-4b68-8b25-166405f630aa.png align="center")

## **Task 2:**

### **Create an Application Load Balancer (ALB) in EC2 using the AWS Management Console.**

Open `EC2 Dashboard` and click on `Create Target Groups` the button.

Let's first specify the group details. Name the target group `ApacheGroup` and select `Instance` the target type. Click on `Next` the button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694168670499/c157c74d-9c7f-424f-badc-8f8a9d77d7b1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694168696862/b11f29cf-19ec-40df-a694-257005f1735e.png align="center")

Now click on `Load Balancers` and click on `Create Application Load Balancer` button here we will add all the instances in the load balancer via `Target Group`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693970257832/2a9a2678-fb4f-4b45-92c2-1ac9d8b69f0e.png?auto=compress,format&format=webp align="left")

Name the Load Balancer `ApacheLB` and select `Internet-facing` the scheme. Click on `Next` the button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693970298804/0a79b458-bf33-4814-a9fd-134b8df82a9b.png?auto=compress,format&format=webp align="left")

Select the VPC `Default VPC` and select all the subnets. Next

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693970346640/3bece113-5a00-4116-919a-c4c48729d5e6.png?auto=compress,format&format=webp align="left")

we will redirect the traffic to the target group.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694169074020/f4211cd2-acec-460d-883f-6415aed193be.png align="center")

Let's check the Register Target to verify the instances are added in the load balancer.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693970538963/21001047-c3ce-4394-a4d0-e716352d01fb.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693970819167/9e23c153-e69c-4533-a62a-757825d1eac4.png?auto=compress,format&format=webp align="left")

***Happy Learning!***