---
title: "Day 23 Task: Jenkins Freestyle Project for DevOps Engineers."
datePublished: Thu Aug 17 2023 17:30:28 GMT+0000 (Coordinated Universal Time)
cuid: cllffta59000309l0as9lhwr2
slug: day-23-task-jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692293370418/4b70856a-915e-4e3a-98de-6f758d8dbc62.png
tags: continuous-delivery, continuous-integration, devops, jenkins, trainwithshubham

---

## What is CI/CD?

* CI or Continuous Integration is the practice of automating the integration of code changes from multiple developers into a single codebase. It is a software development practice where the developers commit their work frequently to the central code repository (Github or Stash). Then there are automated tools that build the newly committed code and do a code review, etc as required upon integration. The key goals of Continuous Integration are to find and address bugs quicker, make the process of integrating code across a team of developers easier, improve software quality, and reduce the time it takes to release new feature updates.
    
* CD or Continuous Delivery is carried out after Continuous Integration to make sure that we can release new changes to our customers quickly in an error-free way. This includes running integration and regression tests in the staging area (similar to the production environment) so that the final release is not broken in production. It ensures to automate the release process so that we have a release-ready product at all times and we can deploy our application at any point in time.
    

## What Is a Build Job?

A Jenkins build job contains the configuration for automating a specific task or step in the application building process. These tasks include gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in different environments.

Jenkins supports several types of build jobs, such as freestyle projects, pipelines, multi-configuration projects, folders, multibranch pipelines, and organization folders.

## What is Freestyle Projects ?? 🤔

A freestyle project in Jenkins is a type of project that allows you to build, test, and deploy software using a variety of different options and configurations. Here are a few tasks that you could complete when working with a freestyle project in Jenkins:

# Task-01

**Pre-requisite**

* Jenkins is installed
    
* Jenkins is up and running.
    
* Docker plugins are installed in Jenkins
    

1. **Create a new Jenkins freestyle project for your app.**
    
    * Log in to your Jenkins instance.
        
    * Click on "New Item" to create a new project.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692285276247/7aa2ca73-738b-428e-b6fc-f3f2769c7d79.png align="center")

* Enter a name for your project (e.g...)
    
* Select "Freestyle project" and click "OK".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692285375470/b201923a-bb9c-4705-b605-cb173dee4c31.png align="center")
    
    On the project configuration page, you can specify the details of the project, such as the source code management system, build triggers, and build actions. In the GitHub project write your GitHub project repository URL.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692286082392/a62e1bab-8952-4fa9-92f1-9f2342b49e59.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692286588994/bd7af02c-1289-477a-b3eb-9e7da2418c1c.png align="center")
    
    Add a second step to run the "docker run" command to start a container using the image created in Step 3
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287128131/5e8e43f5-c3a4-4550-9a88-834328429171.png align="center")

Save the changes

Manually build the project by clicking on the "Build Now" link on the project's main page. This will start the building project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287293549/13331a1b-21b2-4d08-847b-d7c4526acb75.png align="center")

Once the build is completed, you can view the output commands that are executed in the "Console Output".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287398334/545c40e8-4f90-4072-b1c4-a0e13c38f40a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287430824/aae9a388-efac-4359-8ca1-fe885066d47e.png align="center")

# Task-02

* Create a Jenkins project to run the "docker-compose up -d" command to start the multiple containers defined in the compose file (Hint- use day-19 Application & Database docker-compose file).
    
    1. add a build step "docker-compose down" command to stop and remove the containers defined in the compose file.
        
    2. Then add the "docker-compose up -d" command.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692290058960/979723c2-2f31-4f44-9c9f-995468ba9596.png align="center")
        
        1. Build the project
            
        2. Once the build is completed, you can view the output in "Console Output"
            
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692290380033/c66d2104-4e81-4208-b110-638b369a736d.png align="center")
    
    1. Can browse the ip:8001
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692290289246/f7f7e2f2-a06a-4921-af9f-5051988bf5a6.png align="center")

Thank you for reading this blog! Hope you find this article helpful.

*Happy Learning!*