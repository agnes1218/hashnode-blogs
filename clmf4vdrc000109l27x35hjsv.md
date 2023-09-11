---
title: "TerraWeek Day 1: Introduction to Terraform and Terraform Basics"
datePublished: Mon Sep 11 2023 17:03:52 GMT+0000 (Coordinated Universal Time)
cuid: clmf4vdrc000109l27x35hjsv
slug: terraweek-day-1-introduction-to-terraform-and-terraform-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694451682308/29e61022-720c-4ee9-89da-f29f47fd4372.avif
tags: devops, terraform, iac, trainwithshubham, terraweekchallenge

---

## What is Terraform**❓**

Terraform is an infrastructure as code (IaC) tool that allows you to build, change, and version infrastructure safely and efficiently. This includes low-level components such as compute instances, storage, and networking, as well as high-level components such as DNS entries, SaaS features, etc. Terraform can manage both existing service providers and custom in-house solutions.

Infrastructure as Code (IaC) is ***the managing and provisioning of infrastructure through code or configuration files instead of through manual processes.*** Using IaC, you write instructions in a special language that tells your computer how to create and manage your infrastructure.

There are various IaC tools available like Terraform, Chef, Puppet, and Ansible. Read the blog to know why *Terraform* is preferred over other IaC tools

### **Why do we need Terraform and How Does it Simplify Infrastructure Provisioning❓**

Managing infrastructure manually is prone to human errors, is time-consuming, and lacks consistency. This is where Terraform comes to the rescue! Here’s why we need Terraform and how it simplifies infrastructure provisioning:

Terraform provides such a platform that will store the configuration of infrastructure with configuration, provision, and management features as code. We call that Infrastructure Code (IaC).

**Infrastructure as Code**: Terraform allows you to describe your infrastructure using code, which provides several benefits:

1. * **Version Control**: Infrastructure code can be versioned and tracked using Git or other version control systems, enabling collaboration, change management, and rollbacks.
        
        * **Reproducible Infrastructure:** With Terraform, you can recreate your entire infrastructure consistently, eliminating manual setup and configuration errors.
            
        * **Documentation and Collaboration**: Infrastructure code serves as living documentation that can be shared, reviewed, and improved collaboratively.
            
2. **Multi-Cloud and Hybrid Cloud Support:** Terraform provides a unified language and framework for managing infrastructure across multiple cloud providers (such as AWS, Azure, and Google Cloud) and on-premises data centers. It helps avoid vendor lock-in and allows you to deploy resources to different environments seamlessly.
    
3. **Infrastructure Automation**: Terraform automates the provisioning and configuration of infrastructure resources. It can create and manage a wide range of resources, including virtual machines, networks, storage, load balancers, and more. This reduces manual effort, improves efficiency, and ensures consistency across deployments.
    

## How can you install Terraform and set up the environment for AWS, Azure, or GCP**❓**

**Steps to install Terraform and set up the environment for AWS**

To install Terraform and set up the environment for AWS, you can follow these steps:

1. **Install Terraform:**
    

* Download the Terraform binary suitable for your operating system from the official Terraform website ([https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html)).
    

In this demo, We are setting up Terraform in an AWS EC2 instance(Ubuntu AMI):

![](https://miro.medium.com/v2/resize:fit:875/1*rLi6oVuDdEPEf72VUtZM9g.png align="left")

Verify the installation using terraform — version:

![](https://miro.medium.com/v2/resize:fit:875/1*ssFB8ic2UHk1QW0CivI7Wg.png align="left")

2\. **Set Up AWS Credentials:**

* Sign in to the AWS Management Console.
    
* Create an IAM user or use an existing one with appropriate permissions for managing AWS resources. Ensure the user has permissions for EC2, VPC, S3, and other services you plan to work with.
    
* Generate an access key and secret key for the IAM user. Make a note of these credentials as they will be required for Terraform to interact with AWS.
    
* Configure the AWS CLI on your EC2 machine by running the following command in your terminal:
    

3. **Create a Terraform configuration file:**

* Create a new directory for your Terraform configuration files.
    
* Open a terminal and navigate to the new directory.
    
* Create a new Terraform configuration file with an `.tf` extension (e.g., [`main. tf`](http://main.tf/)). This file will contain your infrastructure code.
    
* In the configuration file, specify the AWS provider and any resources you want to create or manage. For example, you can add the following code to create an AWS EC2 instance:
    

![](https://miro.medium.com/v2/resize:fit:875/1*0NZyXrQBWjYn8Zl3p-lXNg.png align="left")

## Explain the important terminologies of Terraform with the example at least (5 crucial terminologies).?

some of the common Terraform terminologies with examples using a simple scenario where we want to create an AWS EC2 instance.

1. **Provider:**
    
    The provider block specifies which cloud provider Terraform should use. In this example, we'll use the AWS provider:
    
    ```yaml
    provider "aws" {
      region = "us-west-2"
    }
    ```
    
    Here, we're configuring the AWS provider to operate in the "us-west-2" region.
    
2. **Resource:**
    
    We'll define an AWS EC2 instance as a resource using the `aws_instance` resource type:
    
    ```yaml
    resource "aws_instance" "example" {
      ami           = "ami-0c55b159cbfafe1f0" # Amazon Linux 2 AMI ID
      instance_type = "t2.micro"
    }
    ```
    
    This defines an EC2 instance named "example" using the specified Amazon Machine Image (AMI) and instance type.
    
3. **Variable:**
    
    We can define variables to make our configuration more flexible. For instance, we can define a variable for the instance type:
    
    ```yaml
    variable "instance_type" {
      description = "The type of EC2 instance to create"
      default     = "t2.micro"
    }
    ```
    
    Now, we can use this variable in our resource block to make it customizable.
    
4. **Output:**
    
    If we want to display information about the created EC2 instance after running `terraform apply`, we can define an output block:
    
    ```yaml
    output "instance_id" {
      value = aws_instance.example.id
    }
    ```
    
    This output block will display the instance ID of the created EC2 instance.
    
5. **State:**
    
    The Terraform state is a critical component that keeps track of the current state of your infrastructure. It stores information about the resources, their configurations, and dependencies. The state file (`terraform.tfstate`) is used by Terraform to plan and apply changes.
    
    Example: Terraform automatically manages the state for you, and you typically don't interact with it directly. However, you can use `terraform state` commands to inspect or manipulate the state if needed.
    
      
    With Terraform, you can embrace the power of declarative configuration, treat your infrastructure as code, and leverage state management for smooth operations. So, take a deep breath, embrace the magic of Terraform, and say goodbye to a tedious manual infrastructure setup.
    
    **Happy Learning!**