---
title: "Day 44: Relational Database Service in AWS"
datePublished: Sat Sep 09 2023 17:29:13 GMT+0000 (Coordinated Universal Time)
cuid: clmcaw9rm000809icao0fcvmu
slug: day-44-relational-database-service-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694280491171/9cd25d21-4b18-4a5f-b162-37ae3cac01c7.png
tags: aws, devops, aws-rds, 90daysofdevops, trainwithshubham

---

Amazon Relational Database Service (Amazon RDS) is a collection of managed services that makes it simple to set up, operate, and scale databases in the cloud

## Task-01

Create a Free tier RDS instance of MySQL

Go to the Amazon EC2 console.

Click "Launch Instance".

Choose a Linux AMI.

Choose an instance type, such as t2.micro.

Choose a VPC and subnet.

Configure security group rules to allow inbound traffic on the appropriate port for the type of database you are using (e.g. port 3306 for MySQL).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694277889910/4429156a-4d8c-4789-a6a5-b38985f280c6.png align="center")

1. ### **Create a Free tier RDS instance of MySQL**
    

Go to the Amazon RDS console. Click "Create database".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278102369/f48a6e86-cbdd-4209-be3f-c2d51f77fd61.png align="center")

Select "MySQL" as the engine type.

Choose the "Free tier" template for "DB instance class".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278190305/1402e7d7-0cd6-4c8b-aeb4-d3269bd2bef0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278265609/de951948-a9b7-4b5f-bd34-49f1dbc69871.png align="center")

Set the "Virtual Private Cloud (VPC)" and "Subnet group" to create the instance in.

Leave the other settings at their default values.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278379776/f6efe2c3-2189-4182-9a00-3cdd290ea1f7.png align="center")

Select ec2-instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278460683/84f62a1f-c78d-4a54-a425-76b64ca0f05a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278497169/1b13047a-d3ca-4433-b6c8-eb81a0329677.png align="center")

Choose the VPC security group

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278579351/597c2dd3-488d-4333-93ca-6b51c878f15d.png align="center")

Click "Create database" to start the instance creation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694278769776/121ac861-e4dd-43eb-990f-179141d09667.png align="center")

Database is created

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279045296/79b1464b-b3ff-4881-8c48-f5a890adba6a.png align="center")

**3\. Create an IAM role with RDS access.**

Go to the IAM console. Click "Roles". Click "Create role".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279109808/ef502565-8031-4330-aeba-dc617003a779.png align="center")

Choose the 'AWS service'.

Choose "Allows EC2 instances to call AWS services

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279155179/b669d310-3bd3-46b6-b8a5-b72bc63b24c0.png align="center")

Attach the "AmazonRDSFullAccess" policy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279220486/5bd42d47-e9be-45ac-90a1-ed3b51e991bc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279270197/43ad224e-4019-4d4e-88a9-02fce6df15ee.png align="center")

**Assign the role to EC2 so that your EC2 Instance can connect with RDS**

Go to the EC2 console.

Select the instance you just created.

Click "Actions", then "Security", then "Modify IAM Role".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279412966/f83b78ea-7123-4b20-bcc7-285c9f393e06.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279443422/66aa8a70-0de6-4a68-81dd-e74820bf1ce3.png align="center")

Choose the IAM role you just created.

Click "Update IAM role".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279492836/4185a450-b617-40e5-9fc1-d73a1c7cc242.png align="center")

**5\. Once the RDS instance is up and running, get the credentials and connect your EC2 instance using a MySQL client.**

Go to the RDS console.

Select the instance you just created.

Click "Configuration" and note the endpoint address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279616837/aa2c34e5-54f2-49fd-87e2-ed4d54db533b.png align="center")

Click "Security" and note the username and password.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694279962819/d90e90cf-c9c1-422b-ba6b-ea0168021781.png align="center")

SSH into your EC2 instance using a terminal or remote access tool.

Install a MySQL client, such as "mysql".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694280098288/a9157475-cddc-47de-959e-d8d2b1084b83.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694280128734/40371c9e-d6fb-4d47-b6c4-3b90e7353ea5.png align="center")

Now connect the **RDS instance** with the **EC2 instance** using the **MySQL client**.

```yaml
mysql -h <endpoint-name> -P <port-name> -u <username> -p
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694280245384/aeb11794-9b84-412e-811d-4ed216306098.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694280316958/d11cd1ae-6bb9-46c1-a1dd-9b2001a35891.png align="center")

Thank you for reading!

***Happy Learning!***