---
title: "Day 57: Ansible Hands-on with video"
datePublished: Mon Oct 09 2023 17:18:39 GMT+0000 (Coordinated Universal Time)
cuid: clnj5q8zn000109la1i5t70dd
slug: day-57-ansible-hands-on-with-video
tags: ansible, devops, 90daysofdevops, configuration-management, trainwithshubham

---

## **Installation of Ansible on AWS EC2 (Master Node)**

```yaml
sudo apt-add-repository ppa:ansible/ansible 
sudo apt update -y
sudo apt install ansible -y
```

To install Ansible on an AWS EC2 instance and set it up as a master node, you can follow these steps:

1. **Create Ec2 Instance**
    
2. **Launch the instance.**
    
3. **Connect to Your EC2 Instance**
    

**Add Ansible PPA repository by using the below command**

```yaml
sudo apt-add-repository ppa:ansible/ansible
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694785681328/483cf034-15f7-4270-9b29-e5ce68950f69.png?auto=compress,format&format=webp&auto=compress,format&format=webp align="left")

```yaml
sudo apt update -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694785688965/4dd4d95f-e18e-45a3-ad90-197af3b6c04c.png?auto=compress,format&format=webp&auto=compress,format&format=webp align="left")

Install Ansible

```yaml
sudo apt install ansible -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671534188/c24d2922-91bb-46f2-9e6a-f1435d69dba5.png align="left")

**Verify Ansible Installation**

You can verify the installation by checking the Ansible version:

```yaml
ansible --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696674171939/4b8b64c9-2d86-4255-8465-a4e5deef708c.png align="left")

## Launch 2 new EC2 instances with same private key as ansible-master EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696870740786/c439b6b9-7a0f-4c83-a1ae-80f34c2ea6be.png align="center")

Copy the private key to master server where Ansible is setup.

In master server where ansible is setup, create a new file at location /home/ubuntu/.ssh and paste private key to that file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696870851539/aff20b61-4618-44f8-a22f-4747c3a1732a.png align="center")

You can SSH into 2 new server instances from master instance by using private key.

1. SSH into ansible-server1 instance
    
2. SSH into ansible-server2 instance
    

```yaml
sudo ssh -i /key-path ubuntu@public-ip-address
```

Create an inventory file for Ansible that lists the IP addresses of the two new EC2 instances.

Create a new folder named ansible, inside folder create hosts file which is inventory file for ansible. add the IP addresses of the servers inside hosts file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696870949980/7d4e5c83-9a7b-4714-a450-a9cf3825dde2.png align="left")

you can verify the inventory of hosts using the ansible-inventory command.

```yaml
ansible-inventory --list -y -i <inventory-file-path>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696871127460/842cdac0-df84-463f-9b68-56fa56c99739.png align="center")

Try a ping command using ansible to the Nodes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680965150589/dd00cf00-38f2-4a4a-b346-549378d14604.png?auto=compress,format&format=webp align="left")

This error message indicates that Ansible was unable to connect to the remote host using SSH because the authentication method specified (likely public key authentication) failed. also Check the permissions on the remote host's private key file

Give permissions to the key file using chmod command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696871631089/c53e9d47-dce5-42ee-9873-d8aa7d4b4ca8.png align="left")

Specify the private key file to use for authentication using the **\--private-key** option when running the Ansible command.

```yaml
ansible -i <inventory_file> all -m ping --private-key=<path_to_private_key>
```

**&lt;inventory\_file&gt;** is the path to the inventory file.

**&lt;hosts&gt;** is the name or pattern of the host(s) that you want to ping.

**&lt;path\_to\_private\_key&gt;** is the path to the private key file to use for authentication.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680968938700/0780ab9a-4732-4ea2-ba97-e2770ac9e285.png?auto=compress,format&format=webp align="left")

\-a "free -m": the -a option specifies the arguments to pass to the command to be executed on the remote hosts. In this case, the free-m command is executed to show the memory usage on each host.

***Happy Learning!***