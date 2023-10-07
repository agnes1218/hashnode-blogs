---
title: "Day 54: Understanding Infrastructure as Code and Configuration Management"
datePublished: Sat Oct 07 2023 08:05:54 GMT+0000 (Coordinated Universal Time)
cuid: clnfr3ovh000p09mj3oyqafym
slug: day-54-understanding-infrastructure-as-code-and-configuration-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696665916755/7320ce94-98ee-44a2-95a0-67fe9ad238a5.png
tags: devops, iac, 90daysofdevops, configuration-management, trainwithshubham

---

### What's the difference?

When it comes to the cloud, Infrastructure as Code (IaC) and Configuration Management (CM) are inseparable. With IaC, a descriptive model is used for infrastructure management. To name a few examples of infrastructure: networks, virtual computers, and load balancers. Using an IaC model always results in the same setting.

Throughout the lifecycle of a product, Configuration Management (CM) ensures that the performance, functional and physical inputs, requirements, design, and operations of that product remain consistent.

# [Task-01](https://github.com/LondheShubham153/90DaysOfDevOps/tree/master/2023/day54#task-01)

Read more about IaC and Config. Management Tools

[**1.Read**](http://1.Read) **more about IaC and Config. Management Tools**

IaC manages infrastructure using a descriptive model. Infrastructure includes networks, virtual machines, load balancers, to name a few. An IaC model produces the same environment every time it is applied.

Configuration Management (CM) maintains the consistency of an application’s performance, as well as its functional and physical inputs along with requirements, overall design, and operations throughout the lifespan of the product.

The choice of tool depends on your specific needs, existing infrastructure, and your team's expertise. Some organizations even use a combination of IaC and configuration management tools to achieve comprehensive automation and management of their infrastructure and applications.

1. **Give differences on both with suitable examples**
    

The main difference between Infrastructure as Code (IaC) and Configuration Management (CM) is that IaC focuses on managing and provisioning infrastructure through code, while CM focuses on automating the configuration and management of software applications, operating systems, and servers.

**Infrastructure as Code (IaC)** is a practice of managing and provisioning IT infrastructure through code. IaC allows teams to manage infrastructure in a repeatable, scalable, and automated manner. With IaC, infrastructure components such as virtual machines, networks, and storage can be defined as code, which can be version controlled, tested, and deployed like any other codebase.

**Configuration Management (CM)**, on the other hand, is the practice of automating the configuration and management of software applications, operating systems, and servers. CM tools help teams automate the installation and configuration of software packages, enforce security policies, and manage system settings.

While IaC focuses on the infrastructure layer, CM focuses on the application layer. However, both concepts work together to help teams automate and manage their IT infrastructure more efficiently.

1. **What are the most common IaC and Config Management Tools?**
    

**Some common Infrastructure as code tools include:**

1. **Terraform**: Terraform is a popular IaC tool by HashiCorp. It uses a declarative configuration language to define infrastructure as code and supports various cloud providers and services.
    
2. **AWS CloudFormation**: AWS CloudFormation is Amazon Web Services' native IaC tool. It allows you to define and provision AWS infrastructure using JSON or YAML templates.
    
3. **Azure Resource Manager (ARM) Templates**: Microsoft Azure's ARM Templates are used for defining and deploying Azure infrastructure as code.
    
4. **Google Cloud Deployment Manager**: Google Cloud Deployment Manager is Google Cloud's IaC tool, which enables the creation and management of Google Cloud resources using templates.
    
5. **Ansible**: Although Ansible is often associated with configuration management, it also has IaC capabilities. Ansible uses YAML-based playbooks to define infrastructure and automate provisioning tasks.
    

**Some common Configuration Management tools include:**

**Chef** - A configuration management tool that automates the deployment, configuration, and management of software.

**Puppet** - A configuration management tool that helps automate the management of infrastructure, applications, and compliance.

**SaltStack** - A tool that automates the configuration and management of software applications, operating systems, and servers.

IaC and CM are complementary concepts that help teams automate and manage their IT infrastructure more efficiently. While IaC focuses on the infrastructure layer, CM focuses on the application layer. Some common IaC tools include Terraform, CloudFormation, Ansible, and Pulumi, while common CM tools include Chef, Puppet, SaltStack, and Ansible.

Thank you for reading!

***Happy Learning!***