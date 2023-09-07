---
title: "Day 38 Getting Started with AWS Basics☁"
datePublished: Thu Sep 07 2023 10:03:32 GMT+0000 (Coordinated Universal Time)
cuid: clm903ezs00080alifot02ygm
slug: day-38-getting-started-with-aws-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694080973432/b2eed13e-60cf-44cb-b270-8852c94c4903.png
tags: aws, cloud-computing, devops, 90daysofdevops, trainwithshubham

---

## AWS:

Amazon Web Services is one of the most popular Cloud Providers that has a free tier for students and Cloud enthusiasts for their Hands-on while learning (Create your free account today to explore more on it).

## IAM:

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. With IAM, you can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

### Task1:

Create an IAM user with the username of your own wish and grant EC2 Access. Launch your Linux instance through the IAM user that you created now and install Jenkins and Docker on your machine via a single Shell Script.

**To create an IAM user with EC2 access, follow these steps:**

Log in to the AWS Management Console.

Go to the IAM service and click on "Users" in the left menu

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694077683560/50ac7f11-ff9d-4f7f-8741-de078c4b00ca.png align="center")

Click on "create user" and enter a username of your choice.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694077761519/f525de68-b854-4ccc-8812-d481085e581e.png align="center")

Select "Programmatic access" and click "Next".

Select "Attach existing policies directly" and select the policy "AmazonEC2FullAccess".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694077827775/9b9da9cb-0c40-4e7f-a764-e7c8149f0aee.png align="center")

Click "Next" until you reach the end, and then click "Create user".

Take note of the username and password, as you will need these to authenticate your IAM user when launching instances.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694077888118/ea86a574-94c6-485c-a61e-b9e9ac923204.png align="center")

**To launch a Linux instance using your IAM user, follow these steps:**

Sign in AWS account as IAM user which we created above.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694077957666/27156e88-3288-42bf-b986-f6922a0d5c80.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694078166709/8c48211c-1de1-4fab-a602-e67f89a4b816.png align="center")

Go to the EC2 service and click on "Launch instance".

Choose a Linux AMI.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694078249094/3f7526c0-aa7b-4a72-93f2-aa2824d0a351.png align="center")

Select an instance type t2.micro and create a new key pair.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694078325755/01d32145-6550-4e7b-bb04-d836424d20bf.png align="center")

Log in ec2 instance using ECW instance connect or we conect with SSH

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694078754191/56ecd44f-37b9-4e7b-85f0-f58519fb8326.png align="center")

Install jenkins and docker on your machine via single Shell Script.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694079470209/672deaa0-18e1-4c8b-8d44-a237a59ca203.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694079201806/275af086-5f00-425e-9861-370d69145511.png align="center")

Check the docker and Jenkins version

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694079517849/86d03b91-c2fa-420a-bdb5-1d8b62e0ab2d.png align="center")

### Task2:

**In this task, you need to prepare a DevOps team of avengers. Create 3 IAM users of Avengers and assign them in devops groups with IAM policy.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694080663534/1a39295c-2ea1-4c02-942b-50113df166d0.png align="left")

Create 3 IAM users of avengers

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694080134155/f4e2a27b-048f-424a-a23a-4894788e4534.png align="center")

Create a avengers devops group by clicking on the "User Groups" link in the left-hand menu and clicking on the "Create New Group" button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694080208823/29a11618-9e6e-41eb-8004-c5744a60e244.png align="center")

In the "Attach Policy" step, search for and select the "AmazonEC2FullAccess", "AmazonS3FullAccess", and "AmazonRDSFullAccess" policies.

Click on the "Create Group" button. below Group DevOps-avengers is created with 3 users.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694080434574/db565759-65f4-400f-80ec-1d17e1a0c9f4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694080520683/cdd18ce1-de8e-4ff7-95d6-a5b01968cff0.png align="center")

Now you have successfully added users in the Avengers group.

Hope you find this article helpful!

***Happy Learning!***