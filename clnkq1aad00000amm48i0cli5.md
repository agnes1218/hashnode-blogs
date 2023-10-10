---
title: "Day 58: Ansible Playbooks"
datePublished: Tue Oct 10 2023 19:34:53 GMT+0000 (Coordinated Universal Time)
cuid: clnkq1aad00000amm48i0cli5
slug: day-58-ansible-playbooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696966454607/93ab646e-b907-4419-8959-92eaf71f46ed.png
tags: ansible, devops, 90daysofdevops, ansible-playbook, trainwithshubham

---

Ansible playbooks run multiple tasks, assign roles, and define configurations, deployment steps, and variables. If you’re using multiple servers, Ansible playbooks organize the steps between the assembled machines or servers and get them organized and running in the way the users need them to. Consider playbooks as the equivalent of instruction manuals.

# [Task-01](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day58/README.md#task-01)

Write an Ansible playbook to create a file on a different server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696963930988/67897b74-42a0-4484-8e07-e65fb9f6dc8e.png align="center")

In this playbook, we define a single task that uses the **file** module to create the file. The **path** parameter specifies the full path to the file we want to create, and **state** parameter set to **touch** which will create the file if it doesn't exist and do nothing if it does exist.

You can run this playbook using the **ansible-playbook** command

```yaml
ansible-playbook file-name.yml -i <inventory-file-path> --private-key=<private-key-path>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696964222093/b92755a1-1c38-4616-b540-9d4d9d410f52.png align="left")

Verify that the file has been created on different servers

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696964483152/c9d80452-9c8d-4a7b-a21a-941ece86a3db.png align="center")

1. ### **Write an ansible playbook to create a new user.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696964756801/9409a9fc-bf55-48e4-9d28-d33753f7a078.png align="center")

In this playbook, we define a single task that uses the **user** module to create a new user.

Run the playbook using the **ansible-playbook** command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696964891396/f25de32b-e8e5-4fa2-9786-b88dc1b3cb54.png align="center")

To check if the user has been created, look for the user's name in the **/etc/passwd** file."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696965028700/d1d88f13-14a7-4305-9985-99bb3cf48394.png align="center")

### **3\. Write an ansible playbook to install docker on a group of servers**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696965834865/8217582b-60f0-4962-9976-c0fb8b4ad6b6.png align="center")

In this playbook, we define three tasks that install Docker on a group of servers. The hosts parameter specifies the group of servers where Docker will be installed. The become parameter is set to yes, which means that the tasks will use elevated privileges to install Docker.

The first task adds the Docker GPG key to the apt keyring, which is required for package signature verification.

The second task adds the Docker repository to the list of sources used by apt-get. This allows the system to download Docker packages from the Docker repository.

The final task install Docker using the apt module. We specify the package name as docker-ce, which installs the Community Edition of Docker.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696965906254/76489d8b-74b1-480e-b13f-92bde3334f68.png align="center")

Verify that Docker has been installed on multiple servers.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696966080971/87c0cd9d-5467-40d5-b507-25114de3d0f7.png align="center")

## Task-02

### **Write a blog about writing Ansible playbooks with the best practices.**

Ansible is a powerful open-source automation tool that allows you to automate IT infrastructure management. Ansible playbooks are the configuration files that describe the desired state of your systems. Writing Ansible playbooks with best practices can make your automation more robust, reliable, and scalable. In this blog, we will discuss some best practices for writing Ansible playbooks.

**Use a clear structure:**

Make sure your playbook is organized and easy to read. Use comments and section headers to explain what each part of the playbook does. Avoid nesting too many tasks or plays inside each other, as it can make the playbook difficult to read and maintain.

**Use idempotent tasks**:

Idempotency is one of the key principles of Ansible. It means that a task should be designed in such a way that it can be executed repeatedly without changing the state of the system. This makes your playbook more robust and prevents unexpected changes to the system. You can achieve idempotency by using modules that are designed to be idempotent, such as **apt**, **yum**, and **copy**.

Example:

```yaml
- name: Install Apache web server
  apt:
    name: apache2
    state: latest
```

In this example, the **apt** module will only install the Apache web server if it is not already installed or if there is a newer version available.

**Use variables:**

Variables can make your playbook more flexible and reusable. They allow you to store values that can be used across multiple tasks and playbooks. You can define variables in the playbook itself or in separate files, such as **group\_vars** or **host\_vars**.

Example:

```yaml
- name: Install Nginx web server
  apt:
    name: nginx
    state: latest

- name: Configure Nginx web server
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/nginx.conf
  vars:
    nginx_port: 80
```

### Use YAML Syntax Correctly:

YAML is the markup language used in Ansible playbooks. Proper YAML syntax is critical for playbook readability and execution. Always use spaces for indentation (not tabs), and be consistent with your formatting.

**Use roles:**

Roles are a way to organize your tasks, variables, and files into reusable components. They can be used across multiple playbooks and provide a way to share functionality between different teams. Roles can also make your playbook more modular and easier to maintain.

Example:

```yaml
- name: Install web serve
  hosts: all
  roles:
    - webserver
```

In this example, we are using a role called **webserver** to install the web server on the all group of hosts.

**Use tags:**

Tags allow you to selectively run specific tasks or groups of tasks within a playbook. This can be useful when testing or debugging your playbook or when you need to run a subset of tasks. Tags can be added to individual tasks or to entire plays.

Example:

```yaml
- name: Install web serve
  hosts: all
  become: yes
  tags:
    - webserver


  tasks:
    - name: Install Apache web server
      apt:
        name: apache2
        state: latest
      tags:
        - apache


    - name: Install Nginx web server
      apt:
        name: nginx
        state: latest
      tags:
        - nginx
```

In this example, we are using tags to selectively run the Apache or Nginx installation tasks.

**Use conditionals:**

Conditionals allow you to execute a task only if a specific condition is met. This can be useful when you need to run a task only on a subset of hosts or when you need to run a task only if a specific variable is defined.

Example:

```yaml
---
- name: Example playbook with a conditional
  hosts: all
  vars:
    myvar: "foo"
  tasks:
    - name: Task 1
      debug:
        msg: "This task will always run"

    - name: Task 2
      debug:
        msg: "This task will run if myvar equals 'foo'"
      when: myvar == "foo"
```

### Parameterize Your Playbooks:

Avoid hardcoding values within your playbooks. Instead, use variables and parameterize your tasks. This makes your playbooks more flexible and reusable. Consider using Ansible Vault for sensitive data like passwords or API keys.

Writing Ansible playbooks with best practices in mind can significantly improve the efficiency and reliability of your automation tasks. By following these guidelines, you'll create playbooks that are easy to read, maintain, and share with your team, ultimately saving time and reducing the risk of errors in your infrastructure automation.

***Happy Learning!***