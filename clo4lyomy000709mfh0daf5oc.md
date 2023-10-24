---
title: "Day 68 - Scaling with Terraform 🚀"
datePublished: Tue Oct 24 2023 17:36:16 GMT+0000 (Coordinated Universal Time)
cuid: clo4lyomy000709mfh0daf5oc
slug: day-68-scaling-with-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698168927591/f248434b-2e8a-4a0a-bf9d-a67d32c7130c.png
tags: aws, devops, terraform, autoscaling, trainwithshubham

---

## [Understanding Scaling](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day68/README.md#understanding-scaling)

Scaling is the process of adding or removing resources to match the changing demands of your application. As your application grows, you will need to add more resources to handle the increased load. And as the load decreases, you can remove the extra resources to save costs.

Terraform makes it easy to scale your infrastructure by providing a declarative way to define your resources. You can define the number of resources you need and Terraform will automatically create or destroy the resources as needed.

## [Task 1: Create an Auto Scaling Group](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day68/README.md#task-1-create-an-auto-scaling-group)

Auto Scaling Groups are used to automatically add or remove EC2 instances based on the current demand. Follow these steps to create an Auto Scaling Group:

* In your [main.tf](http://main.tf) file, add the following code to create an Auto Scaling Group:
    

```plaintext
resource "aws_launch_configuration" "web_server_as" {
  image_id        = "ami-005f9685cb30f234b"
  instance_type  = "t2.micro"
  security_groups = [aws_security_group.web_server.name]

  user_data = <<-EOF
              #!/bin/bash
              echo "<html><body><h1>You're doing really Great</h1></body></html>" > index.html
              nohup python -m SimpleHTTPServer 80 &
              EOF
}

resource "aws_autoscaling_group" "web_server_asg" {
  name                 = "web-server-asg"
  launch_configuration = aws_launch_configuration.web_server_lc.name
  min_size             = 1
  max_size             = 3
  desired_capacity     = 2
  health_check_type    = "EC2"
  load_balancers       = [aws_elb.web_server_lb.name]
  vpc_zone_identifier  = [aws_subnet.public_subnet_1a.id, aws_subnet.public_subnet_1b.id]
}
```

This code provisions a group of EC2 instances with the specified characteristics, launches a simple web server serving an HTML page on port 80, and sets up auto scaling with a minimum of 1 instance, a maximum of 3 instances, and a desired capacity of 2 instances. The instances are placed in the specified subnets.

The autoscaling group defines the parameters for the group, including the launch configuration to use, minimum and maximum number of instances, and desired capacity.

**aws\_launch\_configuration**:- This resource creates a launch configuration for EC2 instances that we are going to deploy as part of our autoscaling group.

The following arguments are required:

* image\_id - The EC2 image ID to launch.
    
* instance\_type - The size of instance to launch.
    
* security\_groups - A list of associated security group IDS.
    

**aws\_autoscaling\_group**:- Provides an Auto Scaling Group resource.

* max\_size - Maximum size of the Auto Scaling Group.
    
* min\_size - Minimum size of the Auto Scaling Group.
    
* desired\_capacity - Number of Amazon EC2 instances that should be running in the group.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698164558570/61b659a5-aaf2-4ec9-9e64-63fb8d466efe.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698164571709/ce91965c-4639-483e-b7b6-54b932d49dd5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698164585803/3645534e-85a6-4646-8d82-2f4794ffd607.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698164597183/3b0fb8a4-3c91-4f12-a808-f430b975fef3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698164628779/75cd9074-93f4-4529-96e4-701c9878b3cc.png align="center")

Run terraform plan

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698167400632/5a147a52-8872-43ef-8e10-7f03e03c954a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698167413798/08a1d869-d8df-42e3-9d7a-0e831c9bb16e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698167427707/3979ae25-9317-456a-a4b5-1bbe4c677e17.png align="center")

Run terraform apply to create the Auto Scaling Group.

`terraform apply`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168246763/be865bc6-9437-4100-b5bb-44a4ebb706cb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168273267/b1ae6434-515b-4053-ae57-a31eab7d6bfd.png align="center")

Auto scaling group is created. Auto scaling group with group details.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168301878/49e1913f-4cfa-440d-ac92-644aba1b8b9d.png align="center")

## Task 2: Test Scaling

Go to the AWS Management Console and select the Auto Scaling Groups service.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168580292/56905b62-645d-402c-9ba5-9ca5d0a7c178.png align="center")

Select the Auto Scaling Group you just created and click on the "Edit" button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168610650/c338ed63-2f17-46ac-89cc-fb4e8875abac.png align="center")

Increase the "Desired Capacity" to 3 and click on the "Save" button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168633461/d86f4d92-92f8-486c-acf0-f10cdb77a979.png align="center")

Go to the EC2 Instances service and verify that the new instances have been launched.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168659170/bed0289e-2912-440c-a6ac-a8f351b12a92.png align="center")

Decrease the "Desired Capacity" to 1 and wait a few minutes for the extra instances to be terminated.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168683027/3c4a9208-68b5-4db2-8ab3-042e95d01505.png align="center")

Go to the EC2 Instances service and verify that the extra instances have been terminated.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168711185/195aac2d-cc24-462b-b65b-9fbbd0ddf871.png align="center")

***Happy Learning!***