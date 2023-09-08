---
title: "Day 40 AWS EC2 Automation ☁"
datePublished: Fri Sep 08 2023 06:42:57 GMT+0000 (Coordinated Universal Time)
cuid: clma8dbgt001009jzgp7tfuzl
slug: day-40-aws-ec2-automation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694155341964/3236c437-44d6-43da-8746-f1a7d8871bb3.png
tags: aws, automation, devops, 90daysofdevops, trainwithshubham

---

## Automation in EC2:

Amazon EC2 or Amazon Elastic Compute Cloud can give you secure, reliable, high-performance, and cost-effective computing infrastructure to meet demanding business needs.

Also, if you know a few things, you can automate many things.

## Launch template in AWS EC2:

* You can make a launch template with the configuration information you need to start an instance. You can save launch parameters in launch templates so you don't have to type them in every time you start a new instance.
    
* For example, a launch template can have the AMI ID, instance type, and network settings that you usually use to launch instances.
    
* You can tell the Amazon EC2 console to use a certain launch template when you start an instance.
    

## Instance Types:

Amazon EC2 has a large number of instance types that are optimized for different uses. The different combinations of CPU, memory, storage, and networking capacity in instance types give you the freedom to choose the right mix of resources for your apps. Each instance type comes with one or more instance sizes, so you can adjust your resources to meet the needs of the workload you want to run.

## AMI:

An Amazon Machine Image (AMI) is an image that AWS supports and keeps up to date. It contains the information needed to start an instance. When you launch an instance, you must choose an AMI. When you need multiple instances with the same configuration, you can launch them from a single AMI.

### Task1:

* **Create a launch template with Amazon Linux 2 AMI and t2.micro instance type with Jenkins and Docker setup (You can use the Day 39 User data script for installing the required tools.**
    

Open the Amazon EC2 console.

In the left navigation pane, choose "Launch Templates".

Choose "Create launch template".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694153128754/1423a2ae-5415-4000-85bc-4c919835cd17.png align="center")

In the "Create a launch template" page, enter a name for the launch template.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694153241539/d79e1781-adc3-4b77-9e98-1144bb27ea1b.png align="center")

For "Amazon Machine Image (AMI)", choose "Amazon Linux 2"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694153319756/46c2baa5-1baf-427d-ad3f-cba5bb068df6.png align="center")

For "Instance type", choose "t2.micro"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694153437519/29d4fde8-496d-434f-9e81-1866c2cd1b47.png align="center")

In the "Advanced Details" section, paste the user data script for installing Jenkins and Docker in the "User data" field.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694153860098/637e5c4b-0a7f-4a64-ba4f-ad81abacb02b.png align="center")

**Create 3 Instances using Launch Template, there must be an option that shows number of instances to be launched ,can you find it?**

**To launch three instances using the launch template**

In the Amazon EC2 console, choose "Launch instance from templates" in the left navigation pane.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694153936416/b73ad4ab-8175-4a61-a04b-3a81da217287.png align="center")

Select the launch template that you just created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694153976776/a1fe46f8-9a87-4d36-a5dc-fe95a8ce12fd.png align="center")

Specify the number of instances you want to launch in the "Number of instances" field on the right side.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154030779/229fea14-b037-472f-8437-399a0b1550b1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154169732/1aff2be8-c273-4272-8a95-f2dfa579c70f.png align="center")

**Let's go one step ahead and create an auto-scaling group**

In the left navigation pane, choose "Auto Scaling Groups".

Choose "Create Auto Scaling Group".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154205826/c33c88a5-a61f-448d-abfe-9c764d588ba4.png align="center")

In the "Create Auto Scaling Group" page, enter a name for the auto-scaling group.

For "Launch Template", choose the launch template we created earlier

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154314190/a5cc796d-5d21-4ed8-8ab1-32f9850c00a8.png align="center")

For "Network", choose the VPC and subnet you want the instances to launch in.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154418994/41569b2e-89e3-42f7-8692-53fcdfa79ddc.png align="center")

For "Load balancing", choose any option as per your requirement.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154512709/51ccfcaf-5ae9-41c0-9b3e-9bd8d0f8a5c4.png align="center")

In the "Group Size" page, enter the desired capacity for the auto-scaling group, such as 2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154619962/90eb26f9-a8b2-4d96-b7b8-22cb7c21f354.png align="center")

Choose the policy target tracking policy, to set the scaling policy based on requirements. Here, we are setting policy for CPU utilization.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154711149/75072600-4c55-4215-b1e4-3988c7cdccbe.png align="center")

Next Review and create an auto-scaling group

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154829036/09efc8ab-466a-4ca5-9129-0b139c18c18c.png align="center")

The auto-scaling group will launch the desired number of instances based on the launch template and the configuration you specified.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694154995769/7906244a-b875-443b-98fc-4d7219f7b1a0.png align="center")

Hope you like the article!.

***Happy Learning!***