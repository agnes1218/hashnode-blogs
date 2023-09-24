---
title: "Day 49 - INTERVIEW QUESTIONS ON AWS"
datePublished: Sun Sep 24 2023 17:52:36 GMT+0000 (Coordinated Universal Time)
cuid: clmxrc4gm000708igempeh9zd
slug: day-49-interview-questions-on-aws
tags: aws, devops, amazon-s3, amazon-ec2, interview-questions

---

## [INTERVIEW QUESTIONS:](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day49/tasks.md#interview-questions)

1. **Name 5 aws services you have used and what are the use cases?**
    

**Amazon S3 (Simple Storage Service):**

* **Use Case:** Amazon S3 is a highly scalable and durable object storage service. It is commonly used for:
    
    * Storing and managing data like (images, videos, documents) for websites and applications.
        

**Amazon EC2 (Elastic Compute Cloud):**

* **Use Case:** Amazon EC2 provides resizable computing capacity in the cloud. It is used for hosting web applications and websites.
    

**Amazon RDS (Relational Database Service):**

* **Use Case:** Amazon RDS manages relational databases in the cloud.
    
    Hosting databases (e.g., MySQL, PostgreSQL, SQL Server).
    

**Amazon Lambda:**

* **Use Case:** AWS Lambda is a serverless computing service that runs code in response to events.
    
    Building serverless applications.
    

**Amazon SNS (Simple Notification Service):**

* **Use Case:** Amazon SNS is a publish-subscribe messaging service. It is used for:
    
    * Sending notifications and alerts via various channels (email, SMS, HTTP, etc.).
        

1. **What are the tools used to send logs to the cloud environment?**
    
    Log Management and analysis is a common practice in cloud environments.
    
    **Amazon CloudWatch Logs:**
    
    CloudWatch Logs allows you to collect and store log data from AWS resources and custom applications.
    
    **Azure Monitor:**
    
    Azure Monitor provides log analytics capabilities for Azure resources.
    
    **Elasticsearch and the ELK Stack (Elasticsearch, Logstash, Kibana):**
    
    You can set up Elasticsearch and the ELK Stack to ingest, store, and analyze logs from various sources.
    
2. **What are IAM Roles? How do you create /manage them?**
    
    IAM (Identity and Access Management) roles are a way to grant permissions to AWS services. IAM roles are preferred for security and automation reasons because they eliminate the need for hard-code credentials.
    
    1. **Sign in to the AWS Management Console:**
        
        * Sign in to your AWS account using your IAM user credentials or the root user.
            
    2. **Open the IAM Console:**
        
        * Navigate to the IAM console, which is typically found in the "Security, Identity, & Compliance" section.
            
    3. **Create a New Role:**
        
        * In the IAM dashboard, click on "Roles" in the left navigation pane.
            
    4. **Create Role:**
        
        * Click the "Create role" button.
            
    5. **Select Type of Trusted Entity:**
        
        * Choose the type of trusted entity that will assume the role.
            
    6. **Attach Permissions Policies:**
        
        * In the "Permissions" step, attach one or more permissions policies to the role
            
    7. **Review and create**
        
        Click the "Create role" button to create the role.
        

**Manage IAM roles through the AWS Management Console, AWS CLI.**

You can edit the permissions policies and trust relationships associated with a role. When a role is no longer needed, you can delete it.

1. **How to upgrade or downgrade a system with zero downtime?**
    
    To upgrade or downgrade a system with zero downtime, you can use techniques such as blue-green deployment, and rolling deployment, These techniques involve creating a duplicate environment, deploying the updated version to the duplicate environment, and gradually shifting traffic from the old environment to the new one.
    
2. **What is infrastructure as code and how do you use it?**
    

Infrastructure as Code (IaC) is an approach to managing and provisioning infrastructure resources, such as servers, networks, databases, and storage, using code and automation. With IaC, you define your infrastructure and its configuration as code, in a human-readable and version-controlled format. This code can then be used to create, modify, and manage infrastructure resources in a consistent and repeatable manner.

IAC, you need to define your infrastructure as code by creating scripts or configuration files that describe the desired state of your infrastructure. Once the code has been written, you can use a tool like CloudFormation or Terraform to provision and manage the infrastructure.

1. **What is a load balancer? Give scenarios of each kind of balancer based on your experience.**
    

A load balancer is a device or software that distributes incoming network traffic across multiple servers to improve the performance, availability, and scalability of applications or services. It can help to distribute the workload among servers and prevent overloading.

**Types of load balancers:**

**Classic Load Balancer (CLB):** This load balancer routes traffic based on either the IP address of the client or the requested hostname. It supports both HTTP and HTTPS protocols, as well as TCP and SSL protocols. Some scenarios where a Classic load balancer may be used are:1) Serving static websites or applications that do not rely on cookies 2) Distributing traffic across multiple web or application servers in a simple setup 3) Handling TCP or SSL traffic for non-HTTP/HTTPS applications

**Application Load Balancer (ALB):** This is a more advanced load balancer that operates at the application layer (Layer 7) and can route traffic based on the content of the request. ALB supports features such as path-based routing, host-based routing, and routing based on HTTP headers or query strings. It can also handle sticky sessions for applications that require session persistence, such as e-commerce websites or SaaS applications.

some scenarios where an application load balancer may be used are 1)Routing traffic to multiple microservices based on path or host 2) Handling traffic for complex web applications with multiple tiers

**Network Load Balancer(NLB):** It is a Layer 4 (transport layer) load balancer that can handle high volumes of traffic with low latency and high throughput. Also used to handle TCP and UDP traffic at the transport layer.

**7)What is CloudFormation and why is it used?**

AWS CloudFormation is a service that allows you to model and provision AWS resources in a declarative way using templates. It is used to automate the deployment and management of infrastructure as code in AWS, making it easier to create, update, and delete stacks of resources with minimal effort. By using CloudFormation, you can create and configure resources in a consistent and repeatable way, reducing the time and effort required to manage your infrastructure.

**8)Difference between AWS CloudFormation and AWS Elastic Beanstalk?**

AWS CloudFormation is a service that automates the deployment and management of infrastructure resources, CloudFormation is focused on infrastructure management and provides more flexibility and control over the resources being deployed. It allows for custom scripts and more granular resource configuration.

AWS Elastic Beanstalk is a platform that simplifies the deployment and management of applications by providing a preconfigured platform. It is focused on application management and provides a preconfigured platform that simplifies the deployment and management of applications. It includes a variety of prebuilt components, such as load balancers and databases, which can be quickly and easily configured.

**9)What are the kinds of security attacks that can occur on the cloud? And how can we minimize them?**

**Several kinds of security attacks can occur on the cloud, including**

1)Distributed Denial of Service (DDoS) attack 2)Malware and viruses 3)Data breaches and theft 4)SQL injection attacks 5)Phishing attacks

**To minimize these security attacks, here are some best practices:**

Use strong authentication and authorization mechanisms, such as multi-factor authentication and role-based access control.

Implement encryption for data at rest and in transit.

Implement regular security audits and vulnerability assessments.

Implement security monitoring and logging to detect and respond to security incidents.

**10)Can we recover the EC2 instance when we have lost the key?**

We can recover an EC2 instance when we have lost the key pair by creating a new key pair, stopping the instance, detaching the root volume, launching a new instance with the new key pair, attaching the root volume to the new instance, starting the new instance, and updating security groups and IP addresses as needed.

There is another way to recover an ec2 instance, if we have lost the key pair, we can create an AMI of the existing instance, and then launch a new instance. We can then select a new key pair by following the instance launch wizard.

**11)What is a gateway?**

A gateway is a network component that serves as a bridge or a transition point between different networks. It is used to facilitate communication and data transfer between networks that may have different communication protocols and addressing schemes. Gateways can be used to connect different cloud environments together.

**12)What is the difference between Amazon Rds, Dynamodb, and Redshift?**

Amazon RDS, DynamoDB, and Redshift are three different database services offered by Amazon Web Services (AWS) with different use cases and functionalities.

**Amazon RDS (Relational Database Service):** is a fully managed relational database service that makes it easy to set up, operate, and scale a relational database in the cloud. It supports popular database engines like MySQL, PostgreSQL, Oracle, and SQL Server. With RDS, you don't have to worry about managing the underlying infrastructure, including patching, backups, and replication. Instead, you can focus on building and optimizing your applications.

**Amazon DynamoDB:** on the other hand, is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. It is designed to handle large amounts of unstructured data, such as documents, images, and social media content. DynamoDB is a serverless database, which means that you don't have to manage any servers or infrastructure.

**Amazon Redshift:** is a fully managed data warehouse service that makes it easy to analyze large amounts of data using SQL and business intelligence tools. It is designed for online analytical processing (OLAP) and supports big data analytics. Redshift is optimized for querying and analyzing large datasets and is based on a columnar storage format. It provides fast query performance and allows you to scale your cluster up or down depending on your needs.

**13)Do you prefer to host a website on S3? What's the reason if your answer is either yes or no?**

**Yes, hosting a website on Amazon S3 can be a good choice for specific scenarios:**

S3 charges based on the amount of storage used and data transferred, which can be significantly cheaper than using a traditional web hosting service.

S3 also lacks some features that are typically included in web hosting services, such as domain name registration, email hosting, and database support.

**Thank you for reading this blog!**

***Happy Learning!***