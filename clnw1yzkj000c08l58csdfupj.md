---
title: "Day 64 - Terraform with AWS"
datePublished: Wed Oct 18 2023 17:54:29 GMT+0000 (Coordinated Universal Time)
cuid: clnw1yzkj000c08l58csdfupj
slug: day-64-terraform-with-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697651633711/ce82ace9-f412-4093-b0b6-776b7d5998b9.png
tags: aws, devops, terraform, 90daysofdevops, trainwithshubham

---

## [Prerequisites](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day64/README.md#prerequisites):

### AWS CLI installed

The AWS Command Line Interface (AWS CLI) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

1. Create an EC2 instance.
    
2. SSH into the EC2 instance
    
3. Install AWS CLI
    

```plaintext
sudo apt install awscli
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697649917875/fd9f862a-0937-4d6d-8960-4ceb5491d90a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697649971361/61963cb6-7bf2-4460-b13c-999f57852c85.png align="center")

### [AWS IAM user](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day64/README.md#aws-iam-user)

IAM (Identity Access Management) AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650230988/a604d6e8-8f85-4928-be9f-02fa6b7a20b9.png align="center")

Create Access key for IAM user.

Click on 'Create access key'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650314340/3d983a7b-22ec-465f-9552-026cf35dddbd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650400931/95474823-194b-4450-8c54-ebef70d36d1e.png align="center")

*To connect your AWS account and Terraform, you need the access keys and secret access keys exported to your machine.*

```plaintext
export AWS_ACCESS_KEY_ID=<access key>
export AWS_SECRET_ACCESS_KEY=<secret access key>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650519398/750a0f45-1ace-4d4c-9b75-28f33d689803.png align="center")

### Install required providers

```plaintext
terraform {
 required_providers {
        aws = {
        source  = "hashicorp/aws"
        version = "~> 4.16"
}
}
        required_version = ">= 1.2.0"
}
```

The **terraform** block defines the version of Terraform that is required to execute this configuration. In this case, it specifies that the Terraform version must be **\&gt;= 1.2.0**.

The **required\_providers** block declares the AWS provider and its version that Terraform will use for the resources defined in this configuration. In this case, it declares the AWS provider with the source **hashicorp/aws** and specifies that the version of the provider should be **~&gt; 4.16**, which means any version of the AWS provider greater than or equal to 4.16 and less than 5.0 will be acceptable.

Add the region where you want your instances to be

```plaintext
provider "aws" {
region = "ap-south-1"
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650684719/2f6d5ede-afed-487c-95e8-2fd65df08305.png align="center")

## Task-01

Provision an AWS EC2 instance using Terraform

```plaintext
resource "aws_instance" "aws_ec2_demo" {
        count = 2
        ami = "ami-0f8ca728008ff5af4"
        instance_type = "t2.micro"
        tags = {
            Name = "TerraformTestInstance"
  }
}
```

The resource block has a resource type of "aws\_instance" and a resource name of "aws\_ec2\_demo". The count parameter is set to 2, which means that two instances will be created.

The ami parameter specifies the Amazon Machine Image (AMI) to use for the instances. In this case, the AMI ID is "ami-0f8ca728008ff5af4".

The instance\_type parameter specifies the type of instance to create. In this case, the instance type is "t2.micro".

The tags parameter specifies metadata to attach to the instance, in this case, a tag named "Name" with the value "TerraformTestInstance".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650796353/126b66af-a4bc-4d60-ac2e-72b0ef5dbaf2.png align="center")

Initialize the working directory with the necessary plugins and modules by executing the **Terraform init**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650876451/8f5ebcbd-4272-4978-9701-749e6ca1bf9a.png align="center")

It will create an execution plan by analyzing the changes required to achieve the desired state of your infrastructure with a **terraform plan.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697650963957/2fd9490d-7001-4dd7-a1f3-d7c646233d1c.png align="center")

it will apply the changes to create or update resources as needed with **terraform apply**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697651378018/2a0099b0-7e99-4a2e-a82e-18fa22cd3dd9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697651399967/832344df-59c8-47e4-88b5-4c756efb9aa9.png align="center")

Two instances should be created using Terraform.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697651477719/968424e7-1696-40ed-a5f5-ed77686152b4.png align="center")

***Happy Learning!***