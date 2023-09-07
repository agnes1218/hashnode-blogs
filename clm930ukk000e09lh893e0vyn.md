---
title: "Day 39 AWS and IAM Basics☁"
datePublished: Thu Sep 07 2023 11:25:31 GMT+0000 (Coordinated Universal Time)
cuid: clm930ukk000e09lh893e0vyn
slug: day-39-aws-and-iam-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694085862029/6673d942-2c8d-4887-84d9-a38c1442fb9b.png
tags: aws, devops, iam, 90daysofdevops, trainwithshubham

---

## AWS:

Amazon Web Services is one of the most popular Cloud Providers that has a free tier for students and Cloud enthusiasts for their Hands-on while learning (Create your free account today to explore more on it).

## User Data in AWS:

* When you launch an instance in Amazon EC2, you have the option of passing user data to the instance that can be used to perform common automated configuration tasks and even run scripts after the instance starts. You can pass two types of user data to Amazon EC2: shell scripts and cloud-init directives.
    
* You can also pass this data into the launch instance wizard as plain text, as a file (this is useful for launching instances using the command line tools), or as base64-encoded text (for API calls).
    
* This will save time and manual effort every time you launch an instance and want to install any application on it like Apache, docker, Jenkins, etc.
    

## IAM:

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. With IAM, you can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

### **Task1:**

**Launch EC2 instance with already installed Jenkins on it. Once server shows up in console, hit the IP address in browser and you Jenkins page should be visible.**

**Take screenshot of Userdata and Jenkins page, this will verify the task completion**

* Go to the EC2 dashboard after logging into the Amazon Management Console.
    
* To begin the process of launching a new EC2 instance, click the "Launch Instance" button.
    
* Choose a machine image from Amazon (AMI)
    

As we have already installed Jenkins.

Check if jenkins is running and jenkins version

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694084683337/54723ea6-e496-4181-b71e-83ee28347365.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694084810528/d204bc04-ba04-4ee3-9f90-d8d584d5edac.png align="center")

Jenkins is running .Now lets access portal for the same

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694084982409/d45c8faa-837d-4fba-b9f8-42ef39ec69cc.png align="center")

### Task2:

Read more on IAM Roles and explain the IAM users, groups, and roles in your own terms.

Users, groups, and roles may all be managed in your Amazon environment using the IAM (Identity and Access Management) service provided by AWS. These three elements work together to give your AWS resources fine-grained access control and permissions.

**Users of IAM:** For the individuals or programs who need access to your AWS resources, you can create individual AWS accounts called IAM users. User names, passwords, access keys, and permissions are all specific to each user, who also has their own set of security credentials. Users can be created, modified, and deleted as necessary, and you can give them particular permissions to utilize or administer AWS resources.

IAM Groups: Groups of IAM users make up IAM. By giving permissions to a group rather than to specific users, you can use groups to streamline permissions management. You could, for instance, make a group just for developers and give them access to certain resources. The group's permissions are automatically passed on to new members when you add them.

**IAM Roles:** IAM roles offer an additional method for controlling access to Amazon resources. Users and roles are similar, however, users are linked to a specific person or account, whereas roles are not. Instead, trusted entities like EC2 instances, Lambda functions, or other AWS services take on the duties. Permissions policies, which specify the particular permissions that a role is permitted to utilize, can be added to roles.

Create three roles named: DevOps-User, Test-User, and Admin.

* Go to the IAM dashboard after logging into the Amazon Management Console.
    
* The "Create role" button may be found after selecting "Roles" from the left-hand menu.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085197609/d4141f77-03a7-4758-8e03-5f229900af74.png align="center")
    

Choose the appropriate use case for the role. For example, if you want to create a role for an EC2 instance, choose "AWS service" and then "EC2".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085246805/80cee3e7-bb88-4326-9a7a-cdd21439085c.png align="center")

Choose the appropriate use case for the role. For example, if you want to create a role for an EC2 instance, choose "AWS service" and then "EC2".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085365093/4fc904c8-dc6c-4585-b0bc-e000cbdfaf76.png align="center")

Select the appropriate permissions policies for the role. You can choose from existing policies or create a custom policy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085345478/e8e64b18-ecb5-4e25-9491-9acb4241952b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085491000/09b55983-22e2-41ad-ba38-884540b76388.png align="center")

* For each role, you want to create—DevOps-User, Test-User, and Admin—repeat the aforementioned procedures.
    
* Build the Test-User role.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085588042/d55c77ff-465d-4238-baec-c77df110e926.png align="center")
    
* Build the Admin role.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085680188/9a8c1c43-f450-41ab-b01e-9e6652ae89a9.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694085718421/f20dab72-37f4-4ddd-98be-8a59204639b9.png align="center")
    
    Once the roles are created, you can assign them to individual IAM users or groups as needed, and control their access to AWS resources.
    

**Happy Learning :)**