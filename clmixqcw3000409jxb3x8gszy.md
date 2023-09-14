---
title: "TerraWeek Day 4 🌱"
datePublished: Thu Sep 14 2023 08:55:05 GMT+0000 (Coordinated Universal Time)
cuid: clmixqcw3000409jxb3x8gszy
slug: terraweek-day-4
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694666773136/a534586d-81ba-4680-98e9-427fbd206491.png
tags: devops, terraform, state-management, trainwithshubham, terraweekchallenge

---

![How to Lock Terraform State with S3 bucket in DynamoDB. | by Christopher  Quiles | Medium](https://miro.medium.com/v2/resize:fit:1148/1*fTy-c4tMqwtsMfZsX0ePLw.png align="left")

## Task 1: Importance of Terraform State

📚 **Research**: Dive into the importance of Terraform state in managing infrastructure. Discover how Terraform state helps track the current state of resources and ensures smooth infrastructure provisioning and management.

**State**\- Terraform refers to the record of the resources and their current state within your infrastructure. Terraform state keeps track of the mappings between your configuration files and the real-world resources that exist in your cloud providers, on-premises infrastructure, or other environments.

1. **Resource Tracking**: It records the current state of the infrastructure resource.
    
2. **Dependency Management**: Terraform uses the state to resolve dependencies.
    
3. **Plan & Apply:** `terraform plan` and `terraform apply` to calculate and execute changes.
    
4. **Locking:** State locking prevents conflicts among team.
    
5. **Remote Storage: The** state can be stored remotely for security and accessibility.
    

## Task 2: Local State and `terraform state` Command

📚 **Understand: Explore different methods of storing the state file, such as local or remote storage. Create a simple Terraform configuration file and initialize it to generate a local state file. Get hands-on with the** `terraform state` **command and learn how to use it effectively to manage and manipulate resources.**

1. **Create Terraform Configuration:**
    
    Creating terraform configuration including a variable that provisions an AWS S3 bucket and DynamoDB.
    

**provider. tf**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694667730175/b87439a7-f3dd-4712-a08e-63fe64e93a3a.png align="center")

`provider "aws"`: This line defines the AWS provider block. It tells Terraform that you want to use the AWS provider to manage AWS resources.

`region = "us-east-1"`: This line sets the region to "us-east-1." The AWS region determines where your AWS resources will be created.

**resource.tf**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694667693442/34af8be0-8d38-480a-a2a2-227c440549d6.png align="center")

An AWS DynamoDB table (`aws_dynamodb_table`) and an AWS S3 bucket (`aws_s3_bucket`). These resources are commonly used as part of setting up a remote backend for managing the Terraform state.

1. **AWS DynamoDB Table (**`aws_dynamodb_table`**)**:
    
    * `name = var.state_table_name`: This sets the name of the DynamoDB table to a value specified in the variable `state_table_name`.
        
    * `billing_mode = "PAY_PER_REQUEST"`: This specifies the billing mode for the DynamoDB table as "PAY\_PER\_REQUEST," meaning you pay per request made to the table.
        
    * `hash_key = "LockID"`: This defines the hash key for the DynamoDB table as "LockID." DynamoDB uses this key for data partitioning.
        
    * `attribute {...}`: This block defines the attribute(s) for the DynamoDB table. In this case, it defines a single attribute named "LockID" of type "S" (String).
        
    * `tags {...}`: Tags can be added to the DynamoDB table for identification and categorization purposes.
        
2. **AWS S3 Bucket (**`aws_s3_bucket`**)**:
    
    * `bucket = var.state_bucket_name`: This sets the name of the S3 bucket to a value specified in the variable `state_bucket_name`.
        
    * `tags {...}`: Tags can be added to the S3 bucket for identification and categorization purposes.
        
    
    **terraform. tf**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694669781553/61b1a7e6-1d12-4ff2-98a3-982c76175f8e.png align="center")
    
    * `required_providers`: This is a top-level block in your Terraform configuration. It is used to specify the providers required for your configuration.
        
    * `aws`: This is the name of the provider you are specifying. In this case, it's the AWS provider.
        
    * `source`: This specifies the source of the provider. The value `"hashicorp/aws"` is the official source for the AWS provider provided by HashiCorp.
        
    * `version`: This is the version constraint for the provider. In your example, `~> 5.0` means that Terraform will use a version of the AWS provider that is greater than or equal to version 5.0 but less than version 6.0.
        

**variables.tf**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694669929278/84e98088-08f3-4a18-b887-ff26cd6ff8f5.png align="center")

1. `state_bucket_name`:
    
    * This variable is intended to hold the name of the S3 bucket where your Terraform state will be stored when using an S3 backend.
        
    * `default = "terraweek-demo-state-bucket"`: It provides a default value for the S3 bucket name. You can override this value when using the variable.
        
2. `state_table_name`:
    
    * This variable is intended to hold the name of the DynamoDB table that might be used for state locking when using a DynamoDB backend.
        
    * `default = "terraweek-demo-state-table"`: It provides a default value for the DynamoDB table name. You can override this value when using the variable.
        
3. `aws_region`:
    
    * This variable is used to specify the AWS region where your resources and the backend will be located.
        
    * `default = "us-east-1"`: It provides a default AWS region of "us-east-1." You can override this value when using the variable to specify a different region.
        

2\*\*. Initialize Terraform Configuration\*\*

Initialize Terraform in the directory where your configuration is located.

```yaml
terraform init
```

**Generate a Local state file:**

Terraform stores the state file locally with the name `terraform.tfstate.`

```yaml
terraform plan
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694670490342/e4f34a01-a07f-4c83-af74-27355d0ece53.png align="center")

You can create the state file by running the following commands:

```yaml
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694671976930/0d8a957e-2e2f-475b-952a-b1f1f254df57.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694672030713/5b898a01-1a88-4567-950a-385dd1ff222f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694672479158/4ebd5a8e-0e4a-4237-915e-5c787734cca7.png align="center")

Terraform will create the S3 bucket and DynamoDB table in 'us-east-1'.

4\. Using `terraform state` command to manage and manipulate resources within in state file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694672328641/3937f6bf-8a37-45d3-950b-48a3db42f38a.png align="center")

To view details of specific resources we can use `terraform state show`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694672509829/23629f38-d546-470e-af25-d3094cc59096.png align="center")

## Task 4: Remote State Configuration

📚 **Modify: Enhance your Terraform configuration file to store the state remotely using the chosen remote state management option. Include the necessary backend configuration block in your Terraform configuration file to enable seamless remote state storage and access.**

Remote state management of terraform that helps teams collaborate, store sensitive information securely and maintain a single source for infrastructure.

Setting up Remote State management with S3:

**Prerequisites**:

* An AWS account with the necessary permissions.
    
* An existing S3 bucket and DynamoDB table were created in your AWS account. You can create these manually through the AWS Management Console or via Terraform.
    

**Terraform Backend Configuration**:

* In your Terraform configuration file (e.g., [`terraform.tf`](http://main.tf)), define the backend configuration.
    
    ```yaml
    terraform {
      required_providers {
        aws = {
          source  = "hashicorp/aws"
          version = "~> 5.0"
        }
      }
    
    
    backend "s3" {
      bucket = "new-u-terraweek-demo-state-bucket"
      key = "terraform.tfstate"
      region = "ap-south-1"
      dynamodb_table = "new-u-terraweek-demo-state-table"
    }
    }
    ```
    

**Initialize the Backend**:

Run `terraform init` to initialize the backend. Terraform will prompt you to confirm the configuration changes. Confirm the changes to use the new backend configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694679883178/e866fd13-b035-47f1-bb71-e2847bdc47bd.png align="center")

**State Locking**:

DynamoDB is used for state locking to prevent concurrent state operations. Ensure that the specified DynamoDB table exists and has the necessary permissions.

Now we will try to write 2 terraform file - resource and providers to create test EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694680240339/d8cebec0-5237-46a4-8a1f-8f579ff0fa74.png align="center")

let's validate and apply it will save the state in the configured S3 bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694680355620/2c47f7fc-553c-4397-bb85-0486dd751a27.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694680407364/4a80e01e-2df2-4b93-9938-6a016737c397.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694680441136/9d6ecd8e-59b7-423d-914d-e5ed0b5383e8.png align="center")

We have saved the state file in S3 bucket and not locally.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694680507563/8d0bd077-305a-4e6f-beb7-b212815b0d63.png align="center")

To access the remote state at any point we can use `terraform state` the command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694680954047/abb1ad5e-84ca-4633-aedb-03001f3162c4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694681182400/6b6e12df-3fb9-4533-a94a-325a242b2950.png align="center")

This setup stores the infrastructure state centrally, for easier to manage and collaboration.

## Task 4: Remote State Configuration

📚 **Modify: Enhance your Terraform configuration file to store the state remotely using the chosen remote state management option. Include the necessary backend configuration block in your Terraform configuration file to enable seamless remote state storage and access.**

```yaml
backend "s3" {
  bucket = "new-u-terraweek-demo-state-bucket"
  key = "terraform.tfstate"
  region = "ap-south-1"
  dynamodb_table = "new-u-terraweek-demo-state-table"
}
}
```

I hope you find this article helpful!

***Happy Learning!***