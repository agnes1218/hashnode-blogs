---
title: "Day 55: Understanding Configuration Management with Ansible"
datePublished: Sat Oct 07 2023 10:49:30 GMT+0000 (Coordinated Universal Time)
cuid: clnfwy2z1000p08jn3e3e1gni
slug: day-55-understanding-configuration-management-with-ansible
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696675730983/5b944544-baae-4152-9720-0dd74120ca06.png
tags: ansible, devops, 90daysofdevops, configuration-management, trainwithshubham

---

## [What's this Ansible?](https://github.com/LondheShubham153/90DaysOfDevOps/tree/master/2023/day55#whats-this-ansible)

Ansible is an open-source automation tool, or platform, used for IT tasks such as configuration management, application deployment, intra-service orchestration, and provisioning

# [Task-01](https://github.com/LondheShubham153/90DaysOfDevOps/tree/master/2023/day55#task-01)

Installation of Ansible on AWS EC2 (Master Node) `sudo apt-add-repository ppa:ansible/ansible` `sudo apt update` `sudo apt install ansible`

Create an EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671036097/12557661-78d7-472f-b6bf-bff22d6f6b8e.png align="center")

Add the Ansible PPA repository using the following command:

```yaml
sudo apt-add-repository ppa:ansible/ansible
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671198368/43bb436a-8f8c-4cd6-a261-01b7c49d4805.png align="center")

Update the package using the following commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671337137/93c2592f-d921-4454-8e56-8129f65e2140.png align="center")

Install Ansible using the following command:

```yaml
sudo apt install ansible
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671534188/c24d2922-91bb-46f2-9e6a-f1435d69dba5.png align="center")

Once the installation is complete, you can check the version of Ansible using the following command:

```yaml
ansible --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696674171939/4b8b64c9-2d86-4255-8465-a4e5deef708c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696674185471/3a0416f0-2340-4a39-aea9-3e54a2290829.png align="center")

### Task-02

**Read more about Hosts file sudo nano /etc/ansible/hosts and ansible-inventory --list -y**

The Ansible hosts file is a configuration file that contains a list of hosts or servers that Ansible can manage. The host's file is located at **/etc/ansible/hosts** on the Ansible control node, and it is used to define the inventory of hosts that Ansible can manage.

To edit the host file, you can use any text editor of your choice.

Once the file is open, you can add the IP addresses or hostnames of the servers you want to manage. The format for adding hosts is as follows:

```yaml
[group_name] 
host1 
host2 
host3 
```

In this example, **group\_name** is a user-defined name for the group of hosts, and **host1**, **host2**, and **host3** are the IP addresses or hostnames of the servers. You can define multiple groups of hosts in the hosts file, each with its own list of hosts.

After you have added the hosts to the file, you can verify the inventory of hosts that Ansible can manage using the **ansible-inventory** command with the **\--list** and **\-y** options:

```yaml
ansible-inventory --list -y 
```

This command will display a YAML-formatted list of hosts and their attributes, including the hostnames, IP addresses, and any other defined variables or group memberships.

### Task-03

**Setup 2 more EC2 instances with the same Private keys as the previous instance (Node)**

Launch 2 new EC2 instances with the same private keys as ansible-server instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696674675891/366c5253-a4f7-467f-8f2d-3e9fa41fe75b.png align="center")

**Copy the private key to the master server where Ansible is set up.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696674915541/a9b357c3-b8cb-4d7a-97a8-e8bef86c5122.png align="center")

Give permissions to the key file using chmod command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696674977750/00bf5846-45d4-4913-8dc6-bfb154c72cfd.png align="center")

Create an inventory file for Ansible that lists the IP addresses of the two new EC2 instances, and specifies the private key file to use for authentication.

Create inventory file at location **/etc/ansible/hosts** which is by default location of the file. Ansible hosts file is a configuration file that contains a list of hosts or servers.

Once the file is open, you can add the IP addresses of the servers and also add a private key file location to use for authentication.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696675466519/9df2e7b3-e82c-45e1-8485-5914a5c826fb.png align="center")

After you have added the hosts to the file, you can verify the inventory of hosts that Ansible can manage using the ansible-inventory command.

```yaml
ansible-inventory --list -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696675496675/3e407de3-0ffc-4610-9578-11d447716c94.png align="center")

**Try a ping command using ansible to the Nodes.**

To test that Ansible is able to connect to your nodes, you can use the following command:

```yaml
ansible all -m ping
```

The ping module will test if you have valid credentials for connecting to the nodes defined in your inventory file. A pong reply means Ansible is ready to run commands on that node.

You can also use servers instead of all which is a group name.

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQEk4cr2J0-0IQ/article-inline_image-shrink_1500_2232/0/1678351277433?e=1701907200&v=beta&t=HsnCekoNwzDZFHlUNgNGSIKO3NWIpgCSGBGC-EH1QxU align="left")

I hope you find this article helpful!

***Happy Learning!***