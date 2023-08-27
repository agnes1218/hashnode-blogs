---
title: "Day 9 Task: Deep Dive in Git & GitHub for DevOps Engineers."
datePublished: Tue Jul 25 2023 09:21:00 GMT+0000 (Coordinated Universal Time)
cuid: clki378tk000h09l5hc06fffq
slug: day-9-task-deep-dive-in-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690276741804/95925eb6-4e6c-4e26-adea-2b3080774ece.png
tags: github, git, devops, 90daysofdevops, devopscommunity

---

**What is Git and why is it important?**

Git - It is a free open-source free version control system that will handle the project with speed and efficiency. It is also used for code management and to track changes in source code which allow multiple developers to work together and contribute. With git, you can keep a record of who made changes to what part of the file, so this can be reverted back to an earlier version of the file.

**What is the difference Between Main Branch and Master Branch??**

No difference between the Main and Master Branch in git, the Master branch is a default branch used to create a repository.

**Can you explain the difference between Git and GitHub?**

**Git** is a free open-source software that is maintained by Linux. You can install it on the local system. It is a Version control system to manage and track changes locally. Git mainly focuses on Version control and code management.

**GitHub** is a service that is maintained by Microsoft. It is a graphical user interface that is hosted on the web. Git hub focuses on centralizing the code. It is a service we use to store our project files.

**How do you create a new repository on GitHub?**

To create a new repository on Github:

1. Go to github.com and log in to your account.
    
2. On the upper right corner, click the + and select the new repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690271253864/492e8251-fde8-49d8-a57f-f8f2adf32614.png align="left")
    
    1. Enter the name of the repository.
        
    2. Choose whether you wanted the repository to be public or private.
        
    3. Add README file
        
    4. Click Create the Repository.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690271473540/494e9fdd-5f8a-4f01-9e6b-fcf4a9a7b3b8.png align="center")
        
        1. What is the difference between local & remote repositories? How to connect local to remote?
            
            The **local repository** is on our local computer. Git local repository is the one on which we will make local changes.
            
            A **git remote** repository is hosted on the server and it will be accessible to everyone.
            
        2. A git remote command is used to make a remote connection i.e connecting to Git local repository and Github remote repository.
            
        
        **git remote add origin https://github.com/your-username/your repository**
        
        **git push origin master**
        
    
    ## **Task 1 :**
    
    Set your user name and email address, which will be associated with your commits.
    
    1. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690273202218/fc846ded-dd9e-4084-aa57-4afd478fc48e.png align="center")
        
    
    ### **Task-2:**
    
3. Create a repository named "Devops" on GitHub
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690271473540/494e9fdd-5f8a-4f01-9e6b-fcf4a9a7b3b8.png align="center")
    
4. Connect your local repository to the repository on GitHub.
    
    `git init` the command makes the present directory to the git repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690273467987/8e2988f6-b08a-4d0f-89ac-186c1a4a8fd5.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690273585832/02d85eea-70c7-4758-98ca-a03c400f2070.png align="center")
    
    `git remote` the command connects the local repository to the local repository.
    
5. Create a new file in Devops/Git/Day-02.txt & add some content to it
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690273933886/deb4e898-9682-43c5-9778-f11d25223c24.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690274036910/113af7d5-73cc-4bfb-9824-a5ce6b5e215d.png align="center")
    
6. Push your local commits to the repository on GitHub
    
    `git push`: It uploads local repository content to a remote repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690274130219/d908d3e6-952f-448b-a00d-3931d06799cb.png align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690274204878/799e52f7-0499-4fa5-8efc-9f34af7c85a0.png align="center")
    
    Thank you for reading this blog!
    

*Happy Learning!*