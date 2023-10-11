---
title: "Day 59: Ansible Project 🔥"
datePublished: Wed Oct 11 2023 10:22:04 GMT+0000 (Coordinated Universal Time)
cuid: clnllq7xs000409mj7kg99rce
slug: day-59-ansible-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697019687191/e45e42dd-99b5-45ad-989a-f96315668777.png
tags: ansible, devops, 90daysofdevops, happy-learning, trainwithshubham

---

# [Task-01](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day59/README.md#task-01)

create 3 EC2 instances . make sure all three are created with the same key pair

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697013896855/5cc4818e-2964-46b0-a963-ac500d661238.png align="center")

**Install Ansible on a host server**

Connect to your EC2 instance using SSH.

Add the Ansible PPA repository using the following command:

```yaml
sudo apt-add-repository ppa:ansible/ansible
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671198368/43bb436a-8f8c-4cd6-a261-01b7c49d4805.png align="left")

Update the package using the following commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671337137/93c2592f-d921-4454-8e56-8129f65e2140.png align="left")

Install Ansible using the following command:

```yaml
sudo apt install ansible
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696671534188/c24d2922-91bb-46f2-9e6a-f1435d69dba5.png align="left")

Once the installation is complete, you can check the version of Ansible using the following command:

```yaml
ansible --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697014158914/37e474ed-5863-41b9-bc1c-98b90e79ff10.png align="center")

**Copy the private key from the local to the Host server (ansible\_host) at (/home/ubuntu/.ssh)**

Copy the private key from your local.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697014266211/4ea1b3f9-835c-4a05-8940-16deb3901ea2.png align="center")

Give permissions to the private key file using chmod command.

`sudo chmod 600 ansible_key`

**Access the inventory file using sudo nano /etc/ansible/hosts**

Create inventory file at location /etc/ansible/hosts which is by default location of file. Ansible hosts file is a configuration file that contains a list of hosts or servers. Add the IP addresses of the servers and also add private key file locations to use for authentication.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697014478166/0232f698-07ea-40be-a1ae-aa7e6e80b725.png align="center")

**Create a playbook to install Nginx**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697015194228/4d74f197-a50b-4a11-9113-4d77a5be2419.png align="center")

In this playbook, we first specify the name of the playbook (**Install nginx**) and the hosts we want to target (**servers**). We also set **become: yes** to run the tasks with root privileges.

The first task updates the apt cache on the managed nodes using the **apt** module. The second task installs the latest version of Nginx using the same module. The third task uses the **service** module to start the Nginx service by specifying the service name (**nginx**) and setting the **state** parameter to **start**.

Run playbook using the ansible-playbook command

```yaml
ansible-playbook file-name.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697018329612/f39da53a-4cf6-4351-aecf-72e3ab618b6b.png align="center")

Check the status of Nginx on the two EC2 instances,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697018694172/4dd759a6-df28-441c-a551-bc4c78293790.png align="center")

**Deploy a sample webpage using the ansible-playbook**

Create a new file index.html in the playbook directory, and add some sample content

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697019263569/7f2eb539-ff14-44a4-9a90-de47cd3317ab.png align="center")

Update a ansible playbook file, install\_nginx.yml, in the playbook directory:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697019298205/31400987-188a-4ffa-9ed8-c6e8256d98d4.png align="center")

This playbook will copy the **index.html** file to the default Nginx web server document root directory at **/var/www/html/.**

Run the playbook

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697019232494/fb36a99d-b6d2-45d6-9548-aa151f65f2eb.png align="center")

Once the playbook finishes executing, open a web browser and enter the public IP address of one of the EC2 instances running Nginx

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697019371703/20b35fb0-4029-45c0-839d-1236a2507eb0.png align="center")

I hope you find this article helpful!

***Happy Learning!***