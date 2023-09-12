---
title: "TerraWeek Day 2"
datePublished: Tue Sep 12 2023 17:33:24 GMT+0000 (Coordinated Universal Time)
cuid: clmgld7ia000709jlbp7b8w3y
slug: terraweek-day-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694539901603/afba4a15-028e-414b-955c-7f18099c8181.png
tags: devops, terraform, trainwithshubham, tws, terraweekchallenge

---

## Task 1: Familiarize yourself with the HCL syntax used in Terraform

* **Learn about HCL blocks, parameters, and arguments**
    
    HashiCorp Configuration Language (HCL) is the language used in Terraform for writing configuration files. HCL configuration files consist of various blocks, parameters, and arguments. Let's break down these concepts with examples:
    
    1. **Blocks:**
        
        Blocks are structural elements in HCL that define different types of configurations. They usually have a specific keyword followed by an opening and closing curly brace (`{}`) to enclose their content.
        
        ```yaml
          <block> <parameters> {
              key1 = value1
              key2 = value2
          }
        ```
        
        Blocks can contain **parameters** and **arguments.**
        
        Example:
        
        ```yaml
        resource "aws_instance" "example" {
          ami           = "ami-0c55b159cbfafe1f0"
          instance_type = "t2.micro"
        }
        ```
        
        In this example, `resource` is a block keyword, and it defines a resource block for creating an AWS EC2 instance.
        
    2. **Parameters:**
        
        Parameters are attributes associated with a block, and they define the behavior or configuration of that block.
        
        Parameters are specified within a block and are often set to specific values or expressions.
        
        Example:
        
        ```yaml
        resource "aws_instance" "example" {
          ami           = "ami-0c55b159cbfafe1f0"
          instance_type = "t2.micro"
        }
        ```
        
        In this resource block, `ami` and `instance_type` are parameters. They specify the Amazon Machine Image (AMI) and the instance type for the EC2 instance.
        
    3. **Arguments:**
        
        Arguments are the values assigned to parameters. They are used to provide specific values for the parameters defined within a block. Arguments follow the parameter name and are set with the **equal sign (**`=`**)**.
        
        Example:
        
        ```yaml
        resource "aws_instance" "example" {
          ami           = "ami-0c55b159cbfafe1f0"
          instance_type = "t2.micro"
        }
        ```
        
        In this resource block, `"ami-0c55b159cbfafe1f0"` **and** `"t2.micro"` are arguments assigned to the `ami` and `instance_type` parameters, respectively.
        
    
    In summary, HCL configuration files consist of blocks, which define the structure of your infrastructure, parameters, which specify the configuration options for those blocks, and arguments, which provide values for those parameters. Terraform uses these configurations to create, update, or delete resources in your infrastructure based on your desired state.
    
* **Explore the different types of resources and data sources available in Terraform**
    
    Terraform is an Infrastructure as Code (IaC) tool that allows you to define, Provision, and manage infrastructure resources in a declarative manner.
    
    **1\. Resources:**
    
    Resources in Terraform are used to create, modify, and manage infrastructure components. They represent real-world resources that Terraform provisions and manages, such as virtual machines, databases, networks, and more. When you define a resource block in your Terraform configuration, Terraform will manage the lifecycle of that resource, including creating, updating, or destroying it.
    
    Here's an example of defining an AWS EC2 instance resource:
    
    ```yaml
    resource "aws_instance" "example" {
      ami           = "ami-0c55b159cbfafe1f0"
      instance_type = "t2.micro"
    }
    ```
    
    In this example, we're defining an EC2 instance using the `aws_instance` resource type. Terraform will create and manage this instance based on the specified Amazon Machine Image (AMI) and instance type.
    
    Common types of resources include `aws_instance` (EC2 instances), `aws_s3_bucket` (S3 buckets), `aws_rds_instance` (RDS databases), and many others, depending on the cloud provider and services you are using.
    
    **2\. Data Sources:**
    
    Data sources in Terraform are used to fetch information about existing resources from your infrastructure without creating or modifying them. They are read-only and provide valuable data that you can use in your configuration. Data sources are often used for referencing existing resources, querying their attributes, and using that information elsewhere in your configuration.
    
    Here's an example of using a data source to retrieve information about an AWS VPC (Virtual Private Cloud):
    
    ```yaml
    data "aws_vpc" "example" {
      id = "vpc-0123456789abcdef0"
    }
    ```
    
    In this example, we're using the `aws_vpc` data source to retrieve details about the specified VPC with the ID `vpc-0123456789abcdef0`. This information can be used, for example, to reference the VPC in other resource configurations or to extract specific attributes like its CIDR block.
    
    Common types of data sources include `aws_vpc` (VPC information), `aws_subnet` (subnet details), `aws_security_group` (security group attributes), and many others.
    
    Data sources help you query and reference existing resources in your Terraform configurations, enabling you to create dynamic and interrelated infrastructure configurations.
    
    Using a combination of resources and data sources allows you to define, provision, and manage your infrastructure while also querying and referencing existing resources, creating a comprehensive approach to managing your infrastructure as code.
    
    ## Task 2: Understand variables, data types, and expressions in HCL
    
    ## **Create a** [**variable.tf**](http://variable.tf) **file and define a variable:**
    

To create a [**variable.tf**](http://variable.tf) file and define a variable in Terraform, follow these steps:

1. Create a new directory for your Terraform project and navigate to the project Directory.
    
2. Inside the project directory, create a file named variables. tf using a text editor or an integrated development environment (IDE).
    
3. In the [**variables.tf**](http://variables.tf) file, you can define variables using the variable block. Here's an example of defining a simple variable named instance type with a description and a default value  
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694447556829/fb4c339d-b280-4c14-a58c-8cd0090ac112.png?auto=compress,format&format=webp align="left")
    
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694539390838/85a34f95-04bc-4deb-9690-59de979d8900.png align="left")
        
    * **Use the variable in a** [**main. tf**](http://main.tf/) **file to create an "AWS Ec2" resource.**
        
    * Create and open your [**main.tf**](http://main.tf) file in the same Terraform project directory.
        
    * Define a **local\_file** resource that uses the **instance\_type** variable to specify a file name or path based on the chosen instance type. Here's an example.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694539441066/7493deda-2252-4b43-a560-9e7f8e3181c0.png align="left")
        
        ### **Task 3: Practice writing Terraform configurations using HCL syntax.**
        
        1. **Adding Required Providers:** To use specific providers (e.g., AWS, Docker), add a `required_providers` block to your configuration:
            
        2. Create and open your [`provider.tf`](http://provider.tf) file in the same Terraform project directory. Here's an example.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694451453822/76ea5517-3948-4f81-84bf-8e5c299f58e2.png?auto=compress,format&format=webp align="left")
            
        
        1. **Testing Your Configuration:**
            
            * Initialize your Terraform project: `terraform init`
                
            * Apply your configuration: `terraform apply`
                
        2. **Making Adjustments:**
            
            * Make any necessary adjustments to your configuration based on Terraform's feedback.
                
            * Use `terraform plan` to see the changes Terraform will apply.
                
        

***Happy Learning!***