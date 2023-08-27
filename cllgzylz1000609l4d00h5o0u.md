---
title: "Day 24 Task: Complete Jenkins CI/CD Project"
datePublished: Fri Aug 18 2023 19:42:15 GMT+0000 (Coordinated Universal Time)
cuid: cllgzylz1000609l4d00h5o0u
slug: day-24-task-complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692387694118/b8c9db40-48ee-4941-a01c-c7bf63d28858.webp
tags: nodejs, devops, jenkins, ci-cd, trainwithshubham

---

# Task-01

* **Fork** [**this**](https://github.com/LondheShubham153/node-todo-cicd.git) **repository:**
    
    This is a node-todo-cicd repo.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692378762133/05766771-af02-4da3-9a07-5e847c02d545.png align="center")
    
    * Setup the Jenkins and Make sure Jenkins are all the plugins are installed on the system.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692379336257/abb518b7-5209-4343-a4c7-14eb6a153bae.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692379660640/19f0edda-1272-48af-8849-e80c0706d492.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692379761125/7e247d6a-eb35-49ff-a2e5-fb5e82fe4239.png align="center")
        
    * **Create a connection to your Jenkins job and your GitHub Repository via GitHub Integration.**
        
    
    **Configuring GitHub**
    
    1. Go to your GitHub account settings.
        
    2. Go to **SSH and GPG keys**, Add public key that we created using ssh-keygen, and select key-type Authentication key.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692380420789/5c099f32-aa78-4b46-86a2-40032395f079.png align="center")
        
        **For GitHub-Webhook:**
        
        1. Go to your GitHub repository and click on **Settings**.
            
        2. [Click](http://2.Click) on **Webhooks** and then click on **Add Webhook**.
            
        
        3\. In the ‘Payload URL’ field, paste your Jenkins environment URL. At the end of this URL add /GitHub-webhook/. In the ‘Content type’ select: ‘application/json’ and leave the ‘Secret’ field empty.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692380646133/b5ca22c9-fb42-41c2-ae60-1a645fbb3577.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692380805190/a1f18eb6-e23c-455d-a039-8f8aad22aafa.png align="center")
        
        Now CI/CD is all setup, we can start with our project.
        
        1. Go to Jenkins are click on new-item to create a project.
            
        2. Select a freestyle project and name the project.
            
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692380966475/0ba11d63-55c6-411e-a428-1d35814e4e6f.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692381085131/5b152d9d-10cb-483b-adf3-269eacbf3ec8.png align="center")
        
        In Configure, GitHub project URL write your project GitHub URL
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692381420488/035e29d3-f8ef-4cb3-8525-bf161e4df49c.png align="center")
        
        Click on the ‘Build Triggers’ tab and then on the ‘GitHub hook trigger for GITScm polling’.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692381510472/6623cc55-2bde-45f4-9f44-2e7d2d98da97.png align="center")
        
        # Task-02
        
        * In the Execute shell run the application using Docker compose.
            
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692381616882/a60d565a-5197-419f-a314-d454233a9aa7.png align="center")
        
        * You will have to make a Docker Compose file for this Project.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692382768119/38eff37e-fc48-448c-a6fe-9fb13f7ffe37.png align="center")
            
            The build is triggered, After the build you can check the console output.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692382926054/d38cd209-5122-4dda-aa64-3765883f2668.png align="center")
            

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692387348345/aed2d29a-4767-4c5d-95f2-ec6b02947994.png align="center")

*Happy Learning!*