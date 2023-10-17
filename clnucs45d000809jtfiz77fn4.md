---
title: "Day 63 - Terraform Variables"
datePublished: Tue Oct 17 2023 13:21:32 GMT+0000 (Coordinated Universal Time)
cuid: clnucs45d000809jtfiz77fn4
slug: day-63-terraform-variables
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697548846989/91a5bb1b-5fd8-4463-a93f-7b8bce3720a4.png
tags: variables, devops, terraform, trainwithshubham, 90daysofdevops-chanllenge

---

We can create a [variable.tf](http://variables.tf) file which will hold all the variables.

```plaintext
variable "filename" {
default = "/home/ubuntu/terrform-tutorials/terraform-variables/demo-var.txt"
}
```

```plaintext
variable "content" {
default = "This is coming from a variable which was updated"
}
```

These variables can be accessed by the var object in [main. tf](http://main.tf)

## Task-01

**Create a local file using Terraform.**

Create a [variable. tf](http://variable.tf) file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697540433145/8e332585-7436-4c7f-8a6a-038f429f65db.png align="center")

The **filename** variable has a default value of **/home/ubuntu/terraform/terraform-variable/var-demo.txt**, which is the path and filename where the local file will be created.

The **content** variable has a default value of **"This is terraform variable demo file"**, which is the text that will be written to the local file.

Create a [main.tf](http://main.tf) file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697540558005/7be49adb-665a-4bfa-9339-aecd308cb8a8.png align="center")

Terraform code block creates a local\_file resource named "DevOps" that writes a file to disk with the filename and content specified by the filename and content variables.

Initializes a new or existing terraform working directory

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697540611324/16efe984-7407-4e45-8cc8-da1c2cc892fb.png align="center")

terraform will take to reach the desired state specified in the configuration file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697540668366/8bbfb1ba-5487-4316-800c-f69ee5af804e.png align="center")

Run **Terraform apply**, Terraform will create a file called **var-demo.txt** in the local directory with the content specified in the **content** variable.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697540746650/39f6959a-cd98-4c7b-95df-d197f8803649.png align="center")

Check file is created in a specified folder using ls command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697540822528/e629b575-f451-433e-bc08-ec14cfb64fc2.png align="center")

### Data Types in Terraform

**Map**

```plaintext
variable "file_contents" {
type = map
default = {
"statement1" = "this is cool"
"statement2" = "this is cooler"
}
}
```

## [Task-02](https://github.com/LondheShubham153/90DaysOfDevOps/tree/master/2023/day63#task-02)

Use terraform to demonstrate usage of List, Set and Object datatypes

In the example, a map variable named **content\_map** is defined with a default value of two key-value pairs. The keys are strings and the values are also strings.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697541028097/83ecaa18-07cb-4417-a9ae-3a8ab541bffd.png align="center")

This variable can be used in your Terraform configuration to reference the values associated with each key defined in the map. For example, you might use it to configure a resource that requires content,

```plaintext
resource "local_file" "devops" {
    filename = "/home/ubuntu/terraform/terraform-variable/type-map/demo.txt"
    content = var.content_map["content1"]
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697541561487/1983292f-bdad-4986-ac22-79e7a122085e.png align="center")

In this example, we use the **content\_map** variable to set the **content** parameter of local\_file resource. We reference the value associated with the key **"content1"** using the dot notation and **var.content\_map\["content1"\]** syntax.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697541902769/5f528613-de8e-471b-86ca-85cf3fd79c75.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697541942079/8c48ddb3-e304-491d-b7cc-5d7608fa0352.png align="center")

terraform plan

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697542042856/82bd14c4-653a-4f46-a5f9-aa351b080758.png align="center")

terraform apply

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697542092928/763439ed-b53f-4206-90b0-67089373b503.png align="center")

Check demo.txt file content

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697542169172/d5750211-07b6-4747-b71d-ab1e560b84b0.png align="center")

**List:**

A list is an ordered collection of values of the same type. To define a list variable, use the **list** type and specify the type of elements in the list. Here's an example:

```plaintext
variable "file_list"{
type = list
default = ["/home/ubuntu/terraform/terraform-variable/type-map/file1.txt","/home/ubuntu/terraform/terraform-variable/type-map/file2.txt"]
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697542275849/cdd02609-c0c0-4eb0-818f-7ab9addc1933.png align="center")

In this example, we define a variable named "file\_list" as a list of strings with a default value that contains a file path.

This variable can be used in your Terraform configuration to reference the file paths defined in the list.

```plaintext
resource "local_file" "devops" {
    filename = var.file_list[0]
    content = var.content_map["content1"]
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697542750746/aaa7d3ea-534e-4501-b832-cf903fbd7600.png align="center")

In this example, we use the file\_list variable to set the filename parameter of an local\_file resource. We reference the first element of the list using the square bracket notation and var.file\_list\[0\] syntax.

Terraform plan

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697543058735/eb176933-24ac-4c9b-b1b7-f38894940815.png align="center")

**Terraform apply**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697543121776/3b78b3af-a748-4390-b8eb-0cb767187a47.png align="center")

**Object:**

 An object is a structural type that can contain different types of values, unlike map, list. It is a collection of named attributes that each have their own type.

In the example, an object variable named **aws\_ec2\_object** is defined with a default value of a set of properties for an EC2 instance.

This variable can be used in your Terraform configuration to reference the individual properties of the EC2 instance defined in the object.

```plaintext
variable "aws_ec2_object" {
    type = object({
        name = string
        instances = number
        keys = list(string)
        ami = string
})


default = {
    name = "test-ec2-instance"
    instances = 4
    keys = ["key1.pem","key2.pem"]
    ami = "ubuntu-bfde24"
}
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697547983239/5c3bf317-95e5-4df6-8430-dbf6625fa700.png align="center")

[main. tf](http://main.tf)

This output can be used to display the value of the **ami** property in the Terraform output after applying the configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697548091036/bde28220-da32-44f3-bb52-b7d2ee9385b8.png align="center")

**terraform plan**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697548136764/32a6286e-e9fe-4b26-87aa-ae42d5dfe553.png align="center")

**terraform apply**

you can see the output of aws-ec2-instance value.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697548256106/e9339b3e-8420-4dfd-8803-312bbe567f75.png align="center")

**Set:**

A set is an unordered collection of unique values of the same type. To define a set variable, use the **set** type and specify the type of elements in the set. Here's an example:

```plaintext
variable "security_groups" {
  type    = set
  default = ["sg-12345678", "sg-87654321"]
}
```

In this example, we define a variable named "security\_groups" as a set of strings with a default value.

### **Use terraform refresh**

To refresh the state of your configuration file, reload the variables

**terraform refresh** is a Terraform command that retrieves the current state of the resources defined in your configuration and updates the Terraform state file to match that state.

By running **Terraform refresh**, you can update the state file to reflect the current state of your resources, so that Terraform has an accurate view of what needs to be changed. This command does not make any changes to your resources but simply updates the state file to match the current state of your resources.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697548556153/9f5e94ee-bf44-47fd-83a2-3fe541abc336.png align="center")

***Happy Learning!***