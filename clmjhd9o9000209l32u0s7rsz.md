---
title: "TerraWeek Day 5"
datePublished: Thu Sep 14 2023 18:04:47 GMT+0000 (Coordinated Universal Time)
cuid: clmjhd9o9000209l32u0s7rsz
slug: terraweek-day-5
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694687015977/b32f0340-51ad-45f3-9eb1-4556f2c9b55e.png
tags: modules, devops, terraform, trainwithshubham, terraweekchallenge

---

## Task 1:

**What are modules in Terraform and why do we need modules in Terraform?**

Terraform, modules are a fundamental concept used to organize and encapsulate infrastructure code into reusable and shareable components. Modules help make Terraform configurations more modular, maintainable, and scalable.

Modules in Terraform improve the organization, maintainability, and collaboration of your infrastructure code. They enable you to build reusable and scalable infrastructure components, reducing the complexity of managing cloud resources and promoting best practices in infrastructure as code (IaC) development.

**What are the benefits of using modules in Terraform?**

1. **Abstraction and Encapsulation**: Modules allow you to encapsulate a set of related resources and configurations into a single, reusable unit.
    
2. **Reusability**: Modules can be reused across multiple Terraform projects and configurations.
    
3. **Separation of Concerns**: Modules promote separation of concerns by breaking down complex infrastructure into smaller, manageable pieces.
    
4. **Versioning**: Modules can be versioned and published, allowing teams to use specific versions of modules in their configurations.
    
5. **Collaboration**: Modules facilitate collaboration among team members. Different team members can work on separate modules, and these modules can be integrated into a larger infrastructure configuration.
    
6. **DRY (Don't Repeat Yourself) Principle**: Modules encourage the DRY principle by eliminating the need to duplicate infrastructure code.
    

## Task 2:

**Create/Define a module in Terraform to encapsulate reusable infrastructure configuration in a modular and scalable manner. For example EC2 instance in AWS, Resource Group in Azure, and Cloud Storage bucket in GCP.**

In this example, we will be creating 2 Ec2 instances 1 S3 bucket, and 1 DynamoDB. for that, we will create a **<mark>provider.tf resources.tf ec2.tf s3.tf dynamodb.tf terraform. tf</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694711772815/e3cb4a1d-c71a-493e-965a-8572b96bb1b2.png align="left")

```yaml
#provider.tf
provider "aws" {
  region = "ap-south-1"  # Replace with your desired AWS region
}
```

```yaml
#ec2.tf
resource "aws_instance" "ec2_instance" {
        ami = var.ami_id   
        instance_type = var.instance_type  

  tags = {
    Name = var.instance_name  
  }
}
```

```yaml
#provider.tf
terraform {
         required_providers {
         aws = {
                 source = "hashicorp/aws"
                 version = "~> 5.0"
                 }
         }
 }
```

```yaml
resource "aws_s3_bucket" "demo-s3-buck1" {
        bucket = var.bucket_name
}
```

```yaml
resource "aws_dynamodb_table" "dyno-demo-table" {
        name = var.table_name
        billing_mode = "PAY_PER_REQUEST"
        hash_key = "emailID"

        attribute {
                name = "emailID"
                type = "S"
}
}
```

**Variable. tf**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694708753015/2bfbc331-fa28-4e09-a3a7-d388cf3a308a.png align="center")

Check everything is correct by doing `terraform plan` and `terraform apply` to create the instance,S3,dynamodb

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694712395385/456b4042-3526-4092-8834-eaae99a454e2.png align="left")

Now Create a directory for modules and copy all the required templates.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694712454911/c9c2cc05-3acd-451f-bee8-c4dcb0f0a942.png align="left")

we will be creating template for my-app

change the variable.tf

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694712629810/57508da4-5eb2-4ad5-8c2d-3d258a313046.png align="center")

1\. **ami\_id**: This variable is of type string and represents the AMI (Amazon Machine Image) ID that will be used for your EC2 instances. AMIs are used as templates to create EC2 instances, and by defining this variable, you can specify the AMI to use in different environments.

1. **instance\_type**: Also of type string, this variable represents the EC2 instance type. EC2 instances come in various types with different compute and memory capacities. Defining this variable allows you to select the appropriate instance type for your infrastructure.
    
2. **instance\_name**: This variable is of type string and can be used to specify a name for your EC2 instances. Naming instances can help you identify them easily in your AWS environment.
    
3. **bucket\_name**: This string variable can be used to specify the name of an S3 bucket. S3 buckets are used for storing objects and files in AWS. By defining this variable, you can customize the name of the S3 bucket in your Terraform configuration.
    
4. **table\_name**: This variable of type string can be used to specify the name of an AWS DynamoDB table. DynamoDB is a managed NoSQL database service in AWS, and by using this variable, you can set the table name for your DynamoDB resources.
    
5. **env\_name**: This variable is of type string and can be used to specify an environment name. Environment names can be used to differentiate resources between different environments, such as "development," "staging," and "production."
    

When you use these variables in your configuration files, you can pass values for them to tailor your infrastructure to specific requirements in different environments. This makes your Terraform code more adaptable and reusable.

**The** `module` **block allows you to reference and use a module in your main Terraform configuration.**

Here's the syntax of a `module` block:

```yaml
module "module_name" {
  source = "module_source"

  # Input variable assignments (if any)
  variable_name = value
  # ...
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694713302059/a8254723-6d94-45b4-b2df-63850d97206c.png align="left")

Main. tf

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694710742063/1a1404f4-574d-468a-b85c-9d1d7865ae41.png align="center")

Terraform configuration, each representing a different environment: "dev," "QA" (staging), and "prd" (production). These module blocks are using a module named "my-app" from a local source (`./modules/my-app`) to create infrastructure in each environment.

* The `env_name` variable is set to "dev" to indicate the development environment.
    
* You're using a "t2.micro" instance type with a specific AMI ID, instance name, S3 bucket name, and DynamoDB table name.
    
* The `env_name` variable is set to "QA" to indicate the staging environment.
    
* You're using a "t2.small" instance type with a specific AMI ID, instance name, S3 bucket name, and DynamoDB table name.
    
* The `env_name` variable is set to "prd" to indicate the production environment.
    
* You're using a "t2.micro" instance type with a specific AMI ID, instance name, S3 bucket name, and DynamoDB table name.
    

`terraform init`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694710918919/78cc6e13-2544-4baa-b576-de33aa635775.png align="center")

`terraform plan`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694710842522/7008c433-7a0f-4949-81ca-296fb8ee21c9.png align="center")

`terraform apply`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694711461236/2d71818e-c654-4612-b50a-dcc7f52082f9.png align="center")

All instances are created with module templates.

**ec2 instance**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694713178640/775d3812-ac3c-489a-af5c-e0cb9135ce22.png align="center")

**s3 bucket**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694713057804/633d3979-d67a-4655-a7f5-00d137b86288.png align="center")

**DynamoDB table**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694713128968/881e7230-8841-4ee0-8713-4dac08154b94.png align="center")

### **Task 3: Dig into modular composition and module versioning**

modular composition and module versioning are important aspects of managing infrastructure as code (IaC) effectively. These practices help you create reusable and maintainable infrastructure configurations while ensuring consistency across different projects and environments.

### **Modular Composition:**

Modular composition refers to the practice of combining multiple Terraform modules to build complex infrastructure configurations. This approach allows you to reuse existing modules for common infrastructure components and assemble them into larger configurations.

### **Module Versioning:**

Module versioning is the practice of assigning versions to Terraform modules to ensure reproducibility and compatibility. This is especially important when you have multiple projects or teams using the same modules.

## Task 4:

**What are the ways to lock Terraform module versions? Explain with code snippets.**

Locking Terraform module versions is important to ensure that your infrastructure remains stable and doesn't break due to unexpected changes in module versions.

When referencing a module in your Terraform configuration, we can specify a version constraint using the version argument. This allows us to ensure that only compatible module versions are used.

You can create a .tf file dedicated to module versions and constraints. For example, you can create a file named [`module-versions.tf`](http://module-versions.tf) and define module versions and constraints there.

```yaml
#module-version.tf
module "CKP-app" {
  source  = "hashicorp/example/aws"
  version = ">= 1.0, < 2.0"  
# Version constraint, any version in the 1.x range
}
```

In this example, Terraform will only use module versions that are greater than or equal to 1.0.0 but less than 2.0.0.

***Happy Learning :)***