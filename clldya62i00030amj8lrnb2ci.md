---
title: "Day-22: Getting Started with Jenkins 😃"
datePublished: Wed Aug 16 2023 16:31:56 GMT+0000 (Coordinated Universal Time)
cuid: clldya62i00030amj8lrnb2ci
slug: day-22-getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692203475053/e7b1f48e-af17-4f43-a894-f6d2303e50a9.jpeg
tags: devops, jenkins, cicd, 90daysofdevops, trainwithshubham

---

## What is Jenkins?

* Jenkins is an open-source continuous integration-continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.
    
* Jenkins is a tool that is used for automation, and it is an open-source server that allows all the developers to build, test and deploy software. It works or runs on Java as it is written in Java. By using Jenkins we can make a continuous integration of projects(jobs) or end-to-endpoint automation.
    
* Jenkins achieves Continuous Integration with the help of plugins. Plugins allow the integration of Various DevOps stages. If you want to integrate a particular tool, you need to install the plugins for that tool. For example Git, Maven 2 project, Amazon EC2, HTML publisher, etc.
    

### **Create a freestyle pipeline to print "Hello World!!**

* Install Jenkins on AWS EC2 Ubuntu instance.
    
* For Jenkins used port 8080, browse instance-public-IP/8080 it will open the Jenkins dashboard.
    

Click on the "New Item" button on the left sidebar.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692202646273/845b3b7f-5770-4eda-95a4-d391c895fd8c.png align="center")

Give your project a name, such as "demo-pipeline" and select "Freestyle project" as the project type.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692202718491/7d3900d6-e5f9-4928-b667-59c52c64d5c7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692202819313/ef2c14c8-7cb9-4429-9f20-5abaa1a4c385.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692202898311/ecd73f80-55b8-4c39-bc4e-94fbd86a3e1a.png align="center")

* Click on the "Save" button at the bottom of the page to create the project.
    
* project is created, click on the "Build Now" link to run the project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692202965979/eafb59ad-79ff-4a21-ba3e-1374310fc6f3.png align="center")
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692203004367/c2520dcf-4df8-4f24-8f62-40c0c07ddc61.png align="center")
    
    Check the console output for the "Hello World!" message.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692203042082/aa104347-53d0-461b-8c8b-a78d66d7bdeb.png align="center")
    
    Thank you for reading this blog!
    

*Happy Learning!*