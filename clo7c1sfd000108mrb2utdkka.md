---
title: "Day 70 - Terraform Modules"
datePublished: Thu Oct 26 2023 15:22:04 GMT+0000 (Coordinated Universal Time)
cuid: clo7c1sfd000108mrb2utdkka
slug: day-70-terraform-modules
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698333672671/8f89c209-3e27-4807-aded-dbc2a9349718.png
tags: modules, devops, terraform, 90daysofdevops, trainwithshubham

---

* Modules are containers for multiple resources that are used together. A module consists of a collection of .tf and/or .tf.json files kept together in a directory
    
* A module can call other modules, which lets you include the child module's resources in the configuration concisely.
    
* Modules can also be called multiple times, either within the same configuration or in separate configurations, allowing resource configurations to be packaged and re-used.
    

### [Below is the format on how to use modules:](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day70/README.md#below-is-the-format-on-how-to-use-modules)

```plaintext
# Creating a AWS EC2 Instance
resource "aws_instance" "server-instance" {
  # Define number of instance
  instance_count = var.number_of_instances

  # Instance Configuration
  ami                    = var.ami
  instance_type          = var.instance_type
  subnet_id              = var.subnet_id
  vpc_security_group_ids = var.security_group

  # Instance Tagsid
  tags = {
    Name = "${var.instance_name}"
  }
}
```

AWS EC2 instance resource in Terraform using a configuration block named `aws_instance` with the name "server-instance." Your configuration block appears to be designed for flexibility, as it uses variables to parameterize key attributes. Here's a breakdown of the resource block and its key elements:

1. `instance_count`: This line is attempting to use a variable named `number_of_instances` to specify the number of EC2 instances you want to create. However, it appears to be using the incorrect attribute name. The correct attribute name for controlling the number of instances is `count` (not `instance_count`). You can adjust the `count` using the `count` meta-argument as shown in previous examples.
    
2. **Instance Configuration**: These lines define various instance attributes that are set based on variables, making the resource configuration more dynamic. Variables like `var.ami`, `var.instance_type`, `var.subnet_id`, and [`var.security`](http://var.security)`_group` should be defined and assigned appropriate values in your Terraform configuration.
    
3. **Instance Tags**: The `tags` block allows you to attach key-value tags to the EC2 instances. In this case, it sets the "Name" tag based on the `var.instance_name` variable. You can use tags to add metadata to your instances for easier identification.
    

```plaintext
# Server Module Variables
variable "number_of_instances" {
  description = "Number of Instances to Create"
  type        = number
  default     = 1
}

variable "instance_name" {
  description = "Instance Name"
}

variable "ami" {
  description = "AMI ID"
  default     = "ami-xxxx"
}

variable "instance_type" {
  description = "Instance Type"
}

variable "subnet_id" {
  description = "Subnet ID"
}

variable "security_group" {
  description = "Security Group"
  type        = list(any)
}
```

a set of module variables for a server module that can be used to parameterize the creation of AWS EC2 instances. These variables allow you to customize the behavior and attributes of your EC2 instances when using the module.

Here's a breakdown of the module variables you've defined:

1. `number_of_instances`: This variable controls the number of EC2 instances to create. It's set to a default value of 1, meaning that by default, the module will create a single instance. However, you can customize this value when using the module to create multiple instances if needed.
    
2. `instance_name`: This variable allows you to specify a name for your EC2 instances. It provides a way to tag your instances with a human-readable name that makes them easily identifiable.
    
3. `ami`: This variable is used to specify the Amazon Machine Image (AMI) ID for the EC2 instances. You've provided a default value, but you can customize it when using the module to choose the appropriate AMI for your instances.
    
4. `instance_type`: This variable is used to specify the instance type (e.g., t2.micro) for the EC2 instances. You would provide this when using the module to select the desired instance type.
    
5. `subnet_id`: This variable allows you to specify the Subnet ID where the EC2 instances will be launched. It's important for placing instances in the correct network.
    
6. `security_group`: This variable is a list that allows you to specify one or more Security Group IDs to associate with the EC2 instances. Security groups control inbound and outbound traffic to and from the instances.
    

```plaintext
# Server Module Output
output "server_id" {
  description = "Server ID"
  value       = aws_instance.server-instance.id
}
```

## The code provided is an example of a Terraform configuration file that creates an EC2 instance in AWS using the **aws\_instance** resource and outputs its ID using the **output** section. Here is a brief description of the different sections in this code:

* **output "server\_id"**: This line declares a new output named "server\_id".
    
* **value = aws\_instance.server-instance.id**: This line sets the value of the output to the ID of the EC2 instance created earlier with the aws\_instance resource. The format aws\_instance.server-instance.id refers to the attribute id of the resource aws\_instance named "server-instance".
    

## Task-01

Write about different modules of Terraform.

### **Modules in Terraform:**

**1\. Modules**:

* Modules in Terraform are self-contained, reusable components of infrastructure configurations. They can consist of one or more resources and are defined in separate directories.
    
* Modules allow you to abstract and encapsulate specific infrastructure components, such as a web server, a database, a VPC, or any other logical grouping of resources.
    
* Modules can be reused in multiple parts of your Terraform configuration, promoting consistency and reducing code duplication.
    
* Modules accept input variables and produce output values, making them customizable and composable.
    

**2\. Root Module**:

* The root module is the entry point of your Terraform configuration. It's essentially the main configuration file (typically named [`main.tf`](http://main.tf)) that sets up your Terraform project.
    
* The root module often defines providers, declares variables, and calls child modules.
    
* It represents the top-level execution context where you configure your infrastructure, set up provider configurations, and orchestrate the use of various child modules.
    

**3\. Child Modules**:

* Child modules are self-contained configurations defined in separate directories within your project.
    
* They encapsulate specific pieces of infrastructure, such as a database cluster or a load balancer.
    
* Child modules are called from the root module and accept input variables that customize their behavior.
    
* They promote reusability, maintainability, and separation of concerns in your Terraform configuration.
    

### **Difference between Root Module and Child Module:**

The key differences between the root module and child modules are:

1. **Root Module**:
    
    * The root module is the top-level configuration file.
        
    * It is the entry point for your Terraform project.
        
    * The root module orchestrates the use of child modules.
        
    * It typically sets up provider configurations, defines variables, and calls child modules.
        
2. **Child Modules**:
    
    * Child modules are self-contained configurations.
        
    * They are defined in separate directories.
        
    * Child modules encapsulate specific infrastructure components.
        
    * They can be called multiple times from the root module and from other modules, promoting reusability.
        

### **Are Modules and Namespaces the Same?**

No, modules and namespaces are not the same in Terraform.

**Modules**:

* As described above, modules are a way to encapsulate and reuse configurations.
    
* Modules help you structure your code and promote code organization, reusability, and modularity.
    
* Modules are designed to create a logical separation of resources.
    

**Namespaces**:

* In Terraform, a namespace typically refers to a named scope within a particular configuration file or module. It's used to group and organize resources and variables.
    
* Namespaces are a way to avoid naming conflicts by scoping identifiers.
    
* They don't necessarily represent a reusable, self-contained unit of infrastructure.
    

In summary, modules and namespaces serve different purposes in Terraform. Modules are a way to structure and organize your code for reuse, while namespaces help organize resources and variables within a particular scope to avoid naming conflicts.

***Happy Learning!***