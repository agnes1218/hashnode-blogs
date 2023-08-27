---
title: "Day 8 Task: Basic Git & GitHub for DevOps Engineers."
datePublished: Mon Jul 24 2023 16:55:29 GMT+0000 (Coordinated Universal Time)
cuid: clkh3zv51000209l38mfja1uy
slug: day-8-task-basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690216711341/65f09b39-8bf3-4300-84d5-cad36d70b08e.png
tags: linux, github, devops, trainwithshubham, 90daysofdevops-chanllenge

---

### What is Git?

Git is a version control system that allows you to track changes to files and coordinate work on those files among multiple people. It is commonly used for software development, but it can be used to track changes to any set of files.

With Git, you can keep a record of who made changes to what part of a file, and you can revert back to earlier versions of the file if needed. Git also makes it easy to collaborate with others, as you can share changes and merge the changes made by different people into a single version of a file.

### What is GitHub?

GitHub is a web-based platform that provides hosting for version control using Git. It is a subsidiary of Microsoft, and it offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. GitHub is a very popular platform for developers to share and collaborate on projects, and it is also used for hosting open-source projects.

## What is Version Control? How many types of version controls do we have?

Version control is a system that tracks changes to a file or set of files over time so that you can recall specific versions later. It allows you to revert files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more.

There are two main types of version control systems: centralized version control systems and distributed version control systems.

1. A centralized version control system (CVCS) uses a central server to store all the versions of a project's files. Developers "check out" files from the central server, make changes, and then "check-in" the updated files. Examples of CVCS include Subversion and Perforce.
    
2. A distributed version control system (DVCS) allows developers to "clone" an entire repository, including the entire version history of the project. This means that they have a complete local copy of the repository, including all branches and past versions. Developers can work independently and then later merge their changes back into the main repository. Examples of DVCS include Git, Mercurial, and Darcs.
    

## Why do we use distributed version control over centralized version control?

1. Better collaboration: In a DVCS, every developer has a full copy of the repository, including the entire history of all changes. This makes it easier for developers to work together, as they don't have to constantly communicate with a central server to commit their changes or to see the changes made by others.
    
2. Improved speed: Because developers have a local copy of the repository, they can commit their changes and perform other version control actions faster, as they don't have to communicate with a central server.
    
3. Greater flexibility: With a DVCS, developers can work offline and commit their changes later when they do have an internet connection. They can also choose to share their changes with only a subset of the team, rather than pushing all of their changes to a central server.
    
4. Enhanced security: In a DVCS, the repository history is stored on multiple servers and computers, which makes it more resistant to data loss. If the central server in a CVCS goes down or the repository becomes corrupted, it can be difficult to recover the lost data.
    

Overall, the decentralized nature of a DVCS allows for greater collaboration, flexibility, and security, making it a popular choice for many teams.

### Task :

**Install Git on your computer**

`sudo apt-get install git` \- To install the git on the system.

`git --version` - To check the latest version of git.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690212546480/3198f552-c2a5-463c-91ca-6f5c674452a2.png align="left")

1. Login to GitHub.com
    
2. Create a repository and enter the repository name.
    
3. Choose the repository you want to be public or private
    
4. Add a README file
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690212991085/1f0148f5-0184-4609-92d6-b1865c1c8b58.png align="center")

Create a folder in your system

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690213203966/b3e60423-940b-4b21-9c58-ab33608cd3bb.png align="left")

Open the terminal and clone the URL to the working directory along with git clone .

**git clone https://github.com/your Username/ Your repository**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214162844/45a5f2c4-8ffd-4f13-a153-cd69a2ed5836.png align="center")

Make some changes to a file in the repository and commit them to the repository using Git

1. Create a file using vi editor
    
2. **git status** - To check the status of your git repository.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214451810/7412cee2-24f2-4f11-924e-f11d4d31242d.png align="center")

3 . `git add` **- moves changes from the working directory to the staging area.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214514104/a809fea3-4a70-49bb-9495-40c7b155ecfd.png align="center")

1. `git commit` - Commit changes to local git repository
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214596236/2f517afa-8ff8-4b74-8756-6fb119cd3726.png align="center")
    
    1. Push the changes back to the repository on GitHub
        
    2. `Remote -v` Request the list of all repositories that are connected to your local repository.
        
        Syntax : git remote -v
        
    3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214791336/13a3ad6d-7dae-45c1-b1fe-2b5fe1bb5cb9.png align="left")
        
        `git push` - Push changes to the remote git repository
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690216357765/80fa4506-5725-458f-a89f-5a407fe39425.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690216333962/0e7a4796-55c1-4230-a2ec-c3cae85b9d86.png align="center")

Thankyou for reading this blog!

Happy learning!