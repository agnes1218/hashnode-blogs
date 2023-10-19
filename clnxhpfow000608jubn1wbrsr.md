---
title: "Day 65 - Working with Terraform Resources 🚀"
datePublished: Thu Oct 19 2023 18:02:43 GMT+0000 (Coordinated Universal Time)
cuid: clnxhpfow000608jubn1wbrsr
slug: day-65-working-with-terraform-resources
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697738533776/e97ae5de-f8c7-44a2-b27a-7b58a9b054cd.png
tags: aws, devops, terraform, 90daysofdevops, trainwithshubham

---

## [Understanding Terraform Resources](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day65/README.md#understanding-terraform-resources)

A resource in Terraform represents a component of your infrastructure, such as a physical server, a virtual machine, a DNS record, or an S3 bucket. Resources have attributes that define their properties and behaviours, such as the size and location of a virtual machine or the domain name of a DNS record.

When you define a resource in Terraform, you specify the type of resource, a unique name for the resource, and the attributes that define the resource. Terraform uses the resource block to define resources in your Terraform configuration.

## Task 1: Create a security group

To allow traffic to the EC2 instance, you need to create a security group. Follow these steps:

In your [main.tf](http://main.tf) file, add the following code to create a security group:

```plaintext
resource "aws_security_group" "web_server" {
  name_prefix = "web-server-sg"

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697735645135/6797a188-4375-4455-8827-ddf982830906.png align="center")

In this configuration, we first configure the AWS provider with the desired region.

Configure a security group using the **aws\_security\_group** resource block that allows incoming traffic on port 80 from any IP address. This ensures that we can access the website from the public internet.

**Run terraform init to initialize the Terraform project.**

**terraform init**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697735719686/6c5935d1-a9ab-428b-98bc-ce5d2c9f884d.png align="center")

**Run Terraform apply to create the security group.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697737294590/4b340193-9474-46c9-ac47-6431299de265.png align="center")

**Check Security group is created**

Go to EC2 service

Inside 'Network & Security', select 'Security Groups'

You can see web-server-sg security group is created using Terraform.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697737494790/581d7d65-a6a4-4ea1-922c-8987fef69fcb.png align="center")

## Task 2: Create an EC2 instance

Now you can create an EC2 instance with Terraform. Follow these steps:

In your [main.tf](http://main.tf) file, add the following code to create an EC2 instance:

```plaintext
resource "aws_instance" "web_server" {
  ami           = "ami-0557a15b87f6559cf"
  instance_type = "t2.micro"
  key_name      = "my-key-pair"
  security_groups = [
    aws_security_group.web_server.name
  ]

  user_data = <<-EOF
              #!/bin/bash
              echo "<html><body><h1>Welcome to my website!</h1></body></html>" > index.html
              nohup python3 -m http.server80 &
  EOF
}

///if you use python2 version then use-
 
   nohup python -m SimpleHTTPServer 80 &
```

Note: Replace the ami and key\_name values with your own.

We use the **user\_data** parameter to execute a Bash script that sets up a basic web server using Python's SimpleHTTPServer.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697737676080/7a4990d3-8656-4754-9072-0099adb403db.png align="center")

When we launch an EC2 instance using Terraform with this **user\_data** script, it will set up a web server serving the content of **index.html** on port 80. You can then access the website by navigating to the public IP address of your instance in a web browser.

**Run terraform apply to create the EC2 instance.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697737709260/fe79b041-f983-415e-87dd-b8c4ce01c1e2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697737910450/40b0418d-6b5f-4db0-a7ad-c24380fcb786.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697737922201/954b1c95-b40c-4952-9d0a-e860bcf6eea3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697738011216/c8531fe2-70b5-48eb-9a84-376eb4c6a27a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697738027875/0e53739b-53c6-4764-ae50-7a8c6bca3035.png align="center")

Browser the public Ip address of the instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697738342805/8505085e-7b8b-4881-bc27-d837be1d9cd2.png align="center")

***Happy Learning!***