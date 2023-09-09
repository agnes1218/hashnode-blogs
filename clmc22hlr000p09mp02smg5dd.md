---
title: "Day 43: S3 Programmatic access with AWS-CLI 💻 📁"
datePublished: Sat Sep 09 2023 13:22:06 GMT+0000 (Coordinated Universal Time)
cuid: clmc22hlr000p09mp02smg5dd
slug: day-43-s3-programmatic-access-with-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694265636228/48cc1b84-344a-4018-8ce1-2eaba14dfbac.png
tags: aws, devops, 90daysofdevops, trainwithshubham, s3-bucket

---

# S3

Amazon Simple Storage Service (Amazon S3) is an object storage service that provides a secure and scalable way to store and access data on the cloud. It is designed for storing any kind of data, such as text files, images, videos, backups, and more.

## Task-01

* **Launch an EC2 instance using the AWS Management Console and connect to it using Secure Shell (SSH).**
    

Log in to the AWS Management Console.

Navigate to the EC2 service and launch an EC2 instance using the console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694260026308/7cee88f4-424b-4ccc-a60b-535e5c6e0d43.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694261040604/48f48795-cfb3-4957-94de-54d62885913a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694261201626/68b85349-d5ef-4ee0-ae92-4ad85f9e90c0.png align="center")

* Create an S3 bucket and upload a file to it using the AWS Management Console.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694261264922/14e1c2a7-bce8-41ad-9fa5-d94b8b0a5834.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694261304949/4f4aa85f-fd13-4076-8a71-8b48ad997d9d.png align="center")
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694261445204/292342cc-e25b-43d5-837e-f3e77ccf65ae.png align="center")

Click on 'Create Bucket'

Once your bucket is created, click on its name to open it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694261554666/619f549c-fb47-4f18-a61f-c77e08453b94.png align="center")

Click on the "Upload" button to upload a file.

In the "Upload" window, click on the "Add files" button to select the file you want to upload.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694261619207/ae26fee0-5fcf-4807-b064-681c816ca3fa.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694262477362/82294ee9-71ea-4ba7-aaf0-3d62f7829b7c.png align="center")

**Access the file from the EC2 instance using the AWS Command Line Interface (AWS CLI).**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694263041363/161c8612-21b9-4190-8601-8d3782531121.png align="center")

To confirm if CLI is installed or not

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694263398961/99901639-45e7-43ba-b30a-08b49f09b08f.png align="center")

Once you have installed the AWS CLI, open a terminal and run the command **aws configure** to configure your account credentials.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694263652367/fda33d1a-f60d-4314-acfc-77b68089d038.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694263609761/23d0a647-1d70-44d0-aabb-9b132bbc8be3.png align="left")

You can use the **aws s3 cp** command to copy the file from your S3 bucket to your EC2 instance and view the content of the file using the cat command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694263853812/537583ef-a61c-4a33-9cb3-6d8bf35d8c15.png align="center")

## Task-02

* **Create a snapshot of the EC2 instance and use it to launch a new EC2 instance.**
    
    Select the EC2 instance that you want to create a snapshot of.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694264157443/53ddc5fa-37bb-4cb5-b573-fa8b717c2802.png align="center")
    
    Click on "Create Snapshot"
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694264201193/3722a8e9-5823-4f29-9277-a58f344ac137.png align="center")
    
    Once the snapshot is created use the snapshot to create a new instance.
    
    On the right side, click on Actions and select 'Create image from snapshot'
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694264356174/222eb0a9-a2ad-4697-8198-4361d6694ffc.png align="center")
    
    In the "Create Image from snapshot" window, enter a name and description for the image.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694264421647/8e7c0c90-890a-435a-952a-8b9182dd8fd8.png align="center")
    
    Once the image is created, go to the "AMIs" section in the EC2 Dashboard.
    
    Select the newly created AMI, right-click on it, and select "Launch Instance."
    
* In the "Launch Instance" window, choose the configuration options for the new instance.
    
* Choose the VPC and subnet you want to launch the new instance in.
    
* In the "Add Storage" section, you can choose to modify the storage volumes as per your requirements.
    
* Review the instance details and click "Launch instance" to launch the new instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694264770191/338e5a70-5090-4b4f-99c1-886ae461476c.png align="center")
    

Once the instance is launched, connect using SSH

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694264929062/05f8cdc2-c3da-42da-a6b0-0757ad20777f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694265242008/647f1bfe-2cd0-477f-afde-327490f567b2.png align="center")

**Download a file from the S3 bucket using the AWS CLI.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694265397003/a357fbf4-afd1-487f-87c1-7ceb6b40e62a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694265437973/82842a6a-2e0e-44ed-ad42-2ed76b59a817.png align="center")

**AWS CLI Commands:**

Here are some commonly used AWS CLI commands for Amazon S3:

`aws s3 ls` - This command lists all of the S3 buckets in your AWS account.

`aws s3 mb s3://bucket-name` - This command creates a new S3 bucket with the specified name.

`aws s3 rb s3://bucket-name` - This command deletes the specified S3 bucket.

`aws s3 cp file.txt s3://bucket-name` - This command uploads a file to an S3 bucket.

`aws s3 cp s3://bucket-name/file.txt .` - This command downloads a file from an S3 bucket to your local file system.

`aws s3 sync local-folder s3://bucket-name` - This command syncs the contents of a local folder with an S3 bucket.

`aws s3 ls s3://bucket-name` - This command lists the objects in an S3 bucket.

`aws s3 rm s3://bucket-name/file.txt` - This command deletes an object from an S3 bucket.

`aws s3 presign s3://bucket-name/file.txt` - This command generates a pre-signed URL for an S3 object, which can be used to grant temporary access to the object.

`aws s3api list-buckets` - This command retrieves a list of all S3 buckets in your AWS account, using the S3 API.

***Happy Learning!***