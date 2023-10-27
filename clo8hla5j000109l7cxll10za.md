---
title: "Day 71 - Let's prepare for some interview questions of Terraform 🔥"
datePublished: Fri Oct 27 2023 10:44:57 GMT+0000 (Coordinated Universal Time)
cuid: clo8hla5j000109l7cxll10za
slug: day-71-lets-prepare-for-some-interview-questions-of-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698403419750/bbfdc447-db87-46b5-b067-aa1321f9591b.png
tags: aws, devops, terraform, 90daysofdevops, trainwithshubham

---

**What is Terraform and how is it different from other IaaC tools?**

* Terraform is an Infrastructure as Code (IaC) tool developed by HashiCorp. It allows you to define and provision infrastructure resources using declarative configuration files.
    
* Unlike some other IaC tools, Terraform is cloud-agnostic and supports multiple cloud providers, on-premises, and third-party integrations.
    
* Terraform's configuration files describe the desired state of infrastructure, and Terraform handles the provisioning and management of resources to achieve that state.
    
* Terraform has a strong focus on infrastructure drift detection and the ability to update and evolve existing infrastructure without causing downtime.
    
* Terraform uses a "plan and apply" approach, which means it generates an execution plan before making changes, making it safer for production environments.
    

**How do you call a** [`main.tf`](http://main.tf) **module?**

* In Terraform, the [`main.tf`](http://main.tf) file is typically the entry point for a module or the main configuration file in the root module.
    
* You don't need to explicitly "call" the [`main.tf`](http://main.tf) file. When you run `terraform apply` or `terraform init`, Terraform automatically processes the configuration in the [`main.tf`](http://main.tf) file in the current directory (root module).
    
* If you have multiple modules, you can reference them from the root module using the `module` block.
    

**What exactly is Sentinel? Can you provide a few examples where we can use Sentinel policies?**

* Sentinel is a policy as a code framework developed by HashiCorp. It is used for policy enforcement, compliance, and governance across infrastructure as code.
    
* Sentinel policies can be used to define rules and constraints on Terraform configurations. For example:
    
    * Enforcing naming conventions for resources.
        
    * Specifying that certain tags must be applied to resources.
        
    * Restricting the use of specific regions or instance types.
        
    * Ensuring compliance with security standards.
        
    * Implementing budget limits.
        
    * Enforcing specific access control rules.
        

**You have a Terraform configuration file that defines an infrastructure deployment. However, there are multiple instances of the same resource that need to be created. How would you modify the configuration file to achieve this?**

* To create multiple instances of the same resource in Terraform, you can use the `count` argument within the resource block. For example:
    
    ```plaintext
    resource "aws_instance" "example" {
      count         = 3
      ami           = "ami-12345678"
      instance_type = "t2.micro"
    }
    ```
    
    **You want to know from which paths Terraform is loading providers referenced in your Terraform configuration (\*.tf files). You need to enable debug messages to find this out. Which of the following would achieve this?**
    
    * A. Set the environment variable TF\_LOG=TRACE
        

**The below command will destroy everything that is being created in the infrastructure. Tell us how would you save any particular resource while destroying the complete infrastructure.**

* To selectively destroy only specific resources while running `terraform destroy`, you can use the `-target` flag. For example, to destroy a specific resource, you can run:
    
    ```plaintext
    terraform destroy -target=aws_instance.example[0]
    ```
    
* This command will destroy only the specific instance referenced by its index (in this case, the first instance).
    

**Which module is used to store .tfstate file in S3?**

* To store the Terraform state file in an S3 bucket, you can use the `terraform` backend configuration with the `s3` backend type. For example:
    

```plaintext
terraform {
  backend "s3" {
    bucket         = "my-terraform-state-bucket"
    key            = "terraform.tfstate"
    region         = "us-west-2"
    encrypt        = true
  }
}
```

**How do you manage sensitive data in Terraform, such as API keys or passwords?**

* Sensitive data in Terraform can be managed using Terraform's built-in mechanisms:
    
    * Use environment variables to set sensitive values, which are not stored in your configuration files.
        
    * Use the `sensitive` argument to mark sensitive variables or outputs, so their values are not displayed in plain text.
        
    * Store sensitive data in a secure external system like HashiCorp Vault.
        
    * Use secure file-based methods like `SOP` for managing secrets in version-controlled files.
        
    
    **You are working on a Terraform project that needs to provision an S3 bucket, and a user with read and write access to the bucket. What resources would you use to accomplish this, and how would you configure them?**
    
    * To provision an S3 bucket and an IAM user with read and write access, you can use the following Terraform resources:
        
        * `aws_s3_bucket` for creating the S3 bucket.
            
        * `aws_iam_user` for creating the IAM user.
            
        * `aws_iam_policy` to define a policy that allows read and write access to the S3 bucket.
            
        * `aws_iam_user_policy_attachment` to attach the policy to the IAM user.
            
    
    Here's an example configuration:
    
    ```plaintext
    resource "aws_s3_bucket" "example" {
      bucket = "my-example-bucket"
    }
    
    resource "aws_iam_user" "example" {
      name = "my-user"
    }
    
    resource "aws_iam_policy" "example" {
      name        = "s3-access-policy"
      description = "Allows read and write access to S3 bucket"
    
      policy = jsonencode({
        Version = "2012-10-17",
        Statement = [
          {
            Action   = "s3:*",
            Effect   = "Allow",
            Resource = [aws_s3_bucket.example.arn, "${aws_s3_bucket.example.arn}/*"]
          }
        ]
      })
    }
    
    resource "aws_iam_user_policy_attachment" "example" {
      user       = aws_iam_user.example.name
      policy_arn = aws_iam_policy.example.arn
    }
    ```
    
    **Who maintains Terraform providers?**
    
    * Terraform providers are typically maintained by the respective cloud providers, organizations, or open-source contributors. For example, AWS maintains the AWS provider, and HashiCorp maintains many official providers. Additionally, the Terraform community often contributes to and maintains various third-party providers.
        
    
    **How can we export data from one module to another?**
    
    * In Terraform, you can export data from one module to another using output variables. To export data, follow these steps:
        
        1. In the source module, define an output variable for the data you want to export.
            
        2. In the calling module, use the `module` block to reference the source module and access the output variable's value.
            
    
    Example: Source Module (source\_module/main.tf):
    
    ```plaintext
    output "exported_data" {
      value = "This is the data to export"
    }
    ```
    
    Calling Module ([main.tf](http://main.tf)):
    
    ```plaintext
    module "source" {
      source = "./source_module"
    }
    
    resource "example_resource" "example" {
      data_from_source = module.source.exported_data
    }
    ```
    
    In this example, `data_from_source` in the resource block will contain the value of the `exported_data` variable from the `source_module`.
    

***Happy Learning!***