---
title: "Day 56: Understanding Ad-hoc commands in Ansible"
datePublished: Tue Oct 10 2023 20:07:14 GMT+0000 (Coordinated Universal Time)
cuid: clnkr6w73000709mjhauwgk4g
slug: day-56-understanding-ad-hoc-commands-in-ansible
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696968391147/1542df91-7d6d-4162-ae2b-dc2e71866d00.png
tags: ansible, devops, trainwithshubham, 90daysofdevops-chanllenge, ad-hoc

---

Ansible ad hoc commands are one-liners designed to achieve a very specific task they are like quick snippets and your compact Swiss army knife when you want to do a quick task across multiple machines.

To put simply, Ansible ad hoc commands are one-liner Linux shell commands and playbooks are like a shell script, a collective of many commands with logic.

Ansible ad hoc commands come in handy when you want to perform a quick task.

# [Task-01](https://github.com/LondheShubham153/90DaysOfDevOps/tree/master/2023/day56#task-01)

write an ansible ad hoc ping command to ping 3 servers from inventory file.

```yaml
ansible -i /path/to/inventory/file server1:server2:server3 -m ping
```

This command uses the **ansible** command with the following options:

* **\-i /path/to/inventory/file**: specifies the path to the inventory file containing the servers we want to ping. /etc/ansible/hosts is by default path of inventory file. there is no need to write path in ansible ad hoc command. If your inventory file is at different location then you need to write the path of inventory file in ad hoc command.
    
* **server1:server2:server3**: specifies the list of servers to ping, separated by colons.
    
* **\-m ping**: specifies that we want to use the **ping** module to ping the servers.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696962423114/9bd9fa55-f997-4294-bde7-540d79e2be55.png align="left")
    
    1. **Write an ansible ad hoc command to check uptime**
        
        ```yaml
        ansible -i /path/to/inventory/file all -m command -a uptime
        ```
        
        This command uses the **ansible** command with the following options:
        
        * **\-m command**: specifies that we want to use the command module to execute the uptime command on the remote servers.
            
        * **\-a uptime**: specifies the arguments to pass to the command module, which in this case is simply the uptime command.
            
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696962610113/dd6d66b7-511f-4e42-805e-36467bf3a935.png align="center")
        
    2. **ansible ad hoc command to check the free memory or memory usage of hosts**
        
        ```yaml
        ansible -i /path/to/inventory/file all -a "free -m"
        ```
        
        **\-a "free -m"**: the **\-a** option specifies the arguments to pass to the command to be executed on the remote hosts. In this case, the **free-m** command is executed to show the memory usage on each host.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696962736569/3bce776b-0402-4039-a770-d00c8e087978.png align="center")
        
    3. **To check the disk space on all hosts in an inventory file**
        
        ```yaml
        ansible -i inventory_file all -m shell -a 'df -h'
        ```
        
        This command uses the **df** command to show the disk space usage on each host in the inventory file.
        
        The **\-m shell** option is used to execute the command on the remote hosts using the shell.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696962834894/0e9dabbb-fb4e-4c18-95de-f22dda2b4399.png align="center")
        
    4. **To run a shell command with sudo on all hosts in an inventory file**
        
        ```yaml
        ansible -i inventory_file all -b -m shell -a 'sudo-command'
        ```
        
        This command uses the **\-b** option to become the sudo user before executing the command with the **shell** module. Replace the **command** with the command you want to run as sudo.
        
        1. Use the sudo command 'sudo apt-get install [docker.io](http://docker.io) -y', so by using this ad hoc command you can install Jenkins, nginx, apache, nodejs, etc. on your 3 or more servers.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696962981634/aa6402e9-6e8c-4e1e-b722-6994d5197e6a.png align="center")
            
        2. Use the sudo command 'sudo git --version' which shows all 3 servers git version.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696963153720/953b4b0d-1de9-40eb-bea6-3ed8e3ad2f07.png align="center")
            
        3. Use the sudo command 'sudo python --version' which shows all 3 server python versions.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696963244737/2237a84e-1f8c-44d8-ab28-1825370b786c.png align="center")
            
        4. Use the sudo command 'sudo docker --version' which shows all 3 server python versions.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696966140129/4ebd1c02-3950-4591-b5fb-45cdd60f7123.png align="center")
            

1. **To check the status of a specific service on all hosts in an inventory file**
    
    ```yaml
    ansible -i inventory_file all -m service -a 'name=docker state=started'
    ```
    
    This command uses the **service** module to check the status of the **apache2** service on all hosts in the inventory file. The **\-a 'name=docker state=started'** option specifies the name of the service to check and the desired state, which is started in this case.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696967010206/0deef692-82c7-41dd-bfa4-d4c154cb45d6.png align="center")
    
2. You can check the status of a specific service on single hosts or server1
    
    ```yaml
    ansible -i inventory_file server1 -m service -a 'name=apache2 state=started'
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696967102293/67b0bcd0-8141-4db1-894e-c3795f5460bc.png align="center")
    
3. **To copy a file to all hosts in an inventory file**
    
    ```yaml
    ansible -i inventory_file all -m copy -a 'src=/local/path/to/file dest=/remote/path/to/file mode=0644'
    ```
    
    This command uses the **copy** module to copy a file from the local machine to all hosts in the inventory file. The **\-a 'src=/local/path/to/file dest=/remote/path/to/file mode=0644'** option specifies the source and destination paths for the file, as well as the desired file permissions.
    
    first create a simple text file at any location, here create a text file at /home/ubuntu location with the name demo.txt
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696967295190/a6853222-bb3d-4bfb-b87d-50cf35ac3be0.png align="center")
    
    Check file is successfully copied to all the servers using the 'sudo ls command'
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696967398772/eab8deca-cd36-42a6-b5ee-871c9dcbf39c.png align="center")
    
4. **Create a file with 755 permissions using ansible ad hoc commands**
    
    ```yaml
    ansible all -m file -a "path=/path/to/file state=touch mode=0755"
    ```
    
    * **\-a "path=/path/to/file state=touch mode=0755"**: This is the argument to the **\-m** option. It tells Ansible to create a file at the path **/path-to-file** with the **touch** state (i.e., to create the file if it doesn't exist). The **mode** argument sets the file permissions to **0755**, which means that the owner has read, write, and execute permissions, and everyone else has read and execute permissions.
        
    * **\-b**: This tells Ansible to run the command as the superuser (i.e., with sudo).
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696967904435/aa5707c6-fb4b-438d-9387-0e815d488a30.png align="center")

Check file is created with given permissions using the sudo ls -l command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696967986465/3d4b0266-d3c9-453c-b89f-a3b2cf642ed8.png align="center")

***Happy Learning!***