---
title: "Day 66 - Terraform Hands-on Project - Build Your Own AWS Infrastructure with Ease using Infrastructure as Code (IaC) Techniques(Interview Questions)"
datePublished: Fri Oct 20 2023 18:18:30 GMT+0000 (Coordinated Universal Time)
cuid: clnyxpkl000010ami9ghrg8nf
slug: day-66-terraform-hands-on-project-build-your-own-aws-infrastructure-with-ease-using-infrastructure-as-code-iac-techniquesinterview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697825873472/78ad3ec1-bc5f-49bb-aeec-477900785755.png
tags: devops, terraform, iac, 90daysofdevops, trainwithshubham

---

## [Task:](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day66/README.md#task)

**1.Create a VPC (Virtual Private Cloud) with CIDR block 10.0.0.0/16**

```plaintext
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"

tags = {
    Name = "main"
  }
} 
```

This will create a new VPC in your AWS account with the specified CIDR block and a name tag of "main".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697821776832/b4a552d3-203b-4683-a619-2fbf3b6b7218.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697821945071/0c873c7f-49ba-4305-8a7c-9b67ab54d6a9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697821973309/a16b02c8-e249-4362-a79a-644fbe57e792.png align="center")

Go to the VPC console and check new VPC with the name 'main' is successfully created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697822066236/64d9007c-8b74-43c4-ad6d-ddac23461ce8.png align="center")

**2\. Create a public subnet with CIDR block 10.0.1.0/24 in the above VPC.**

To create a public subnet with CIDR block 10.0.1.0/24 in the VPC that you created in the previous step, you can use the following Terraform code:

```plaintext
resource "aws_subnet" "public_subnet" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.1.0/24"

  tags = {
    Name = "Public Subnet"
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697822224106/b75834f4-26a1-4c3c-bc11-28f832514005.png align="center")

Go to VPC console then go to Subnets.

Check that "Public Subnet" is created successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697822269070/b783e462-8203-4fd3-bf65-8eb00ff3e9ae.png align="center")

**3\. Create a private subnet with CIDR block 10.0.2.0/24 in the above VPC.**

This Terraform code creates a private subnet with CIDR block 10.0.2.0/24 in the VPC with ID **aws\_vpc.main.id**, and tags it with the name "Private Subnet".

```plaintext
resource "aws_subnet" "private_subnet" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.2.0/24"


  tags = {
    Name = "Private Subnet"
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697822358474/3551dbba-5109-4ea7-b040-b7f7448f77eb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697822826459/18b9c9e9-3852-4b7c-9751-2ed84817e26a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823063220/3cfeee7f-202b-4eac-8da5-f7dcb22072aa.png align="center")

Go to VPC console then go to Subnets.

Check that "Public Subnet" is created successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697822940862/42f41459-aff5-49d1-98d2-d1364f1f9095.png align="center")

**4\. Create an Internet Gateway (IGW) and attach it to the VPC.**

```plaintext
resource "aws_internet_gateway" "gw" {
  vpc_id = aws_vpc.main.id
  
  tags = {
    Name = "igw"
  }
}
```

This Terraform code creates an internet gateway in the VPC with ID aws\_vpc.main.id, and tags it with the name "igw".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823122831/2e6b2917-110a-4778-a022-49daaa8c8677.png align="center")

**terraform apply** -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823239292/8aa75ddb-f363-4c5e-94c4-a7fc035a8af4.png align="center")

Go to VPC then go to Internet gateways

Check new internet gateway is created with the name 'igw'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823313495/dda2cc00-3959-4bb5-9265-41537cb98702.png align="center")

**5\. Create a route table for the public subnet and associate it with the public subnet. This route table should have a route to the Internet Gateway.**

```plaintext
resource "aws_route_table" "public" {
  vpc_id = aws_vpc.main.id

   route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.gw.id
  }

   tags = {
    Name = "route-table"
  }
}

resource "aws_route_table_association" "public" {
  subnet_id      = aws_subnet.public_subnet.id
  route_table_id = aws_route_table.public.id
}
```

First create a route table for public subnet.

**aws\_route\_table** block creates a new route table in the VPC specified by vpc\_id attribute. It also defines a route that sends all traffic with destination CIDR 0.0.0.0/0 to the internet gateway specified by gateway\_id attribute. The tags attribute sets a name for the route table for easy identification.

Then associate the route table with the public subnet.

**aws\_route\_table\_association** block associates the newly created route table with a public subnet specified by the subnet\_id attribute. The route\_table\_id attribute refers to the ID of the route table created in the previous block.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823605556/f3b3bcaa-724c-4bb4-b3d4-26a7218ce016.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823666063/c6884996-54d9-4b0d-971d-1faf28179841.png align="center")

In Route tables, new route table is successfully created.

Route table routes with internet gateway.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823692123/09740494-508a-4942-871a-5fd58d103be7.png align="center")

**6\. Launch an EC2 instance in the public subnet with the following details:**

* **AMI**
    
* **Instance type: t2.micro**
    

**aws\_instance block** creates a new EC2 instance in the public subnet specified by subnet\_id attribute. It uses the Amazon Machine Image (AMI) ID ami-0f8ca728008ff5af4, which is a Ubuntu 18.04 LTS image. The key\_name attribute specifies the name of the key pair used to SSH into the instance. The vpc\_security\_group\_ids attribute specifies a list of security groups to attach to the instance, in this case, it refers to the ID of the security group created in the next block.

```plaintext
resource "aws_instance" "web_server" {
  ami           = "ami-0f8ca728008ff5af4"
  instance_type = "t2.micro"
  key_name      = "terraform-key"
  subnet_id     = aws_subnet.public_subnet.id

  vpc_security_group_ids = [
      aws_security_group.ssh_access.id
  ]
```

**Security group: Allow SSH access from anywhere**

**aws\_security\_group block** creates a new security group that allows inbound traffic on ports 22 (SSH) and 80 (HTTP) from any source (0.0.0.0/0). The name\_prefix attribute sets a name prefix for the security group, and the vpc\_id attribute specifies the ID of the VPC where the security group will be created.

```plaintext
resource "aws_security_group" "ssh_access" {
  name_prefix = "ssh_access"
  vpc_id      =  aws_vpc.main.id


  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697823815056/dca68e68-4297-4e1d-8aec-3a691618174d.png align="center")

**User data: Use a shell script to install Apache and host a simple website**

The **user\_data attribute** specifies the script to run when the instance is launched. This script updates the package manager, installs Apache web server, creates a basic HTML file, and restarts Apache.

```plaintext
 user_data = <<-EOF
        #!/bin/bash
        sudo apt-get update -y
        sudo apt-get install apache2 -y
        sudo systemctl start apache2
        sudo systemctl enable apache2
        echo "<html><body><h1>Welcome to my website!</h1></body></html>" > /var/www/html/index.html
        sudo systemctl restart apache2
  EOF
```

**Create an Elastic IP and associate it with the EC2 instance.**

**aws\_eip** block creates a new Elastic IP address and associates it with the instance created in the first block by specifying the instance ID in the instance attribute. The tags attribute sets a name for the Elastic IP for easy identification.

```plaintext
resource "aws_eip" "eip" {
  instance = aws_instance.web_server.id


  tags = {
    Name = "test-eip"
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697825508664/8d55da68-e6ec-4b86-871b-e658429587d8.png align="center")

Terraform [main.tf](http://main.tf) file for creating EC2 instance in the public subnet.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697825558399/b180434e-570d-4667-bef6-b19083010e21.png align="center")

Run terraform apply to create the EC2 instance in your AWS account

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697825645297/6efe2642-b4c4-4252-8c18-99872a85a2ae.png align="center")

**Open the website URL in a browser to verify that the website is hosted successfully.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697825721543/93f7a67c-34fc-4189-8c2d-b5ccc175591d.png align="center")

***Happy Learning!***