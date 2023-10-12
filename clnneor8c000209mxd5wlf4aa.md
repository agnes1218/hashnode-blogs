---
title: "Day 60 - Terraform🔥"
datePublished: Thu Oct 12 2023 16:40:31 GMT+0000 (Coordinated Universal Time)
cuid: clnneor8c000209mxd5wlf4aa
slug: day-60-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697128757370/a7a4084d-20f4-49dd-a504-4d17536b040a.png
tags: devops, terraform, iac, trainwithshubham, 90daysofdevops-chanllenge

---

## [What is Terraform?](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day60/README.md#what-is-terraform)

Terraform is an infrastructure as code (IaC) tool that allows you to create, manage, and update infrastructure resources such as virtual machines, networks, and storage in a repeatable, scalable, and automated way.

## [Task 1:](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day60/README.md#task-1)

## **Install Terraform on your system.**

Create an EC2 instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697128194542/4a1ddbf0-a3f1-4d32-b2d3-d7f3d110496d.png align="center")

SSH into your Ubuntu EC2 instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697128228102/aa77e309-c994-419b-9e90-9094323be7de.png align="center")

Download the appropriate package for your system from the official Terraform website ([https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html)).

Select Linux as the operating system and Ubuntu as the package manager.

Copy and paste below three commands to the instance terminal.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697128261149/64c6032d-1693-4e8d-8f34-0dec2ff5ff8e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697128359752/c82c6845-ed9e-4976-a590-a7870e678c88.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697128410460/ac6e59dc-1445-4a25-b1a1-6ad4f6b628d4.png align="center")

Install Terraform by running the following command:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697128603122/71dd8c8f-ae53-4070-855b-b3050be066d4.png align="center")

Verify that Terraform is installed correctly by running the following command:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697128646929/b3ff4feb-4dc2-4d83-b715-628d29e4c423.png align="center")

## Task 2: Answer the below questions

**Why do we use terraform?**

Terraform is a tool for building, changing, and versioning infrastructure in a safe, repeatable way. It enables teams to manage infrastructure as code, providing a single source of truth for the infrastructure and ensuring that it is always in the desired state. Terraform can be used to manage infrastructure across multiple cloud providers and on-premises infrastructure, and it supports a wide range of resource types.

**What is Infrastructure as Code (IaC)?**

Infrastructure as Code (IaC) is a practice of managing and provisioning infrastructure using code instead of manual processes. By treating infrastructure as code, teams can version control their infrastructure, automate the provisioning process, and improve collaboration between different teams. IaC enables teams to make changes to infrastructure in a safe and repeatable way, and it helps to reduce the risk of human error and inconsistencies.

**What is a Resource?**

In Terraform, a resource is a declarative representation of a component in a cloud infrastructure, such as a virtual machine, database, or network interface. Resources define the desired state of the component, and Terraform uses the resource definition to create, modify, or delete the component as needed.

**What is a Provider?**

In Terraform, a provider is a plugin that interfaces with a specific cloud infrastructure provider or service. Providers define the resources that Terraform can manage, as well as the methods for creating, updating, and deleting those resources. Examples of providers include AWS, Google Cloud, and Microsoft Azure.

**What is a State file in Terraform? What’s the importance of it?**

The Terraform state file is a JSON file that stores the state of the infrastructure managed by Terraform. It includes information about the resources that have been created, their current state, and any dependencies between them. The state file is critical to Terraform's operation, as it is used to plan and execute changes to the infrastructure. The state file should be kept in a safe and secure location, as it contains sensitive information about the infrastructure.

**What is the Desired and Current State?**

In Terraform, the desired state is the state that you want your infrastructure to be in, as defined in your Terraform configuration files. The current state is the actual state of the infrastructure, as represented in the Terraform state file. When you run Terraform apply, Terraform compares the desired state with the current state and makes changes as needed to bring the infrastructure into the desired state.

***Happy Learning!***