---
title: "Day 10 Task: Advance Git & GitHub for DevOps Engineers."
datePublished: Wed Jul 26 2023 15:28:36 GMT+0000 (Coordinated Universal Time)
cuid: clkjvrtr9000c09lb5pjear2v
slug: day-10-task-advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690382392854/3f70ed87-daa8-4fcd-b4dd-b4a91d866009.png
tags: github, devops, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge

---

## Git Branching

Use a branch to isolate development work without affecting other branches in the repository. Each repository has one default branch and can have multiple other branches. You can merge a branch into another branch using a pull request.

Branches allow you to develop features, fix bugs, or safely experiment with new ideas in a contained area of your repository.

## Git Revert and Reset

Two commonly used tools that git users will encounter are git reset and git revert. The benefit of both of these commands is that you can use them to remove or edit changes you’ve made in the code in previous commits.

## Git Rebase and Merge

### What Is Git Rebase?

Git rebase is a command that lets users integrate changes from one branch to another, and the logs are modified once the action is complete. Git rebase was developed to overcome merging’s shortcomings, specifically regarding logs.

### What Is Git Merge?

Git merge is a command that allows developers to merge Git branches while the logs of commits on branches remain intact.

The merge wording can be confusing because we have two methods of merging branches and one of those ways is actually called “merge,” even though both procedures do essentially the same thing.

Refer to this article for a better understanding of Git Rebase and Merge

### **Task :**

Add a text file called version01.txt inside the Devops/Git/ with “This is the first feature of our application” written inside. This should be in a branch coming from `master`, \[hint try `git checkout -b dev`\], switch to `dev` branch ( Make sure your commit message will reflect as "Added new feature"). \[Hint use your knowledge of creating branches and Git commits commands.\]

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690310721796/9edba402-ea82-4001-b313-0ce6259b73bb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690310766811/21d22ad3-458f-492d-91d3-48e8f17a1279.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690310793109/76aed171-be64-4c6e-b74e-28ea59aca7d4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690310812220/0ae4f33a-f188-44e6-85de-09cdf040ed24.png align="center")

* ## Task 2:
    
    * Demonstrate the concept of branches with 2 or more branches with a screenshot.
        
    * add some changes to `dev` the branch and merge that branch in `master`
        
    * as a practice try git rebase too, and see what difference you get **version01.txt should reflect at the local repo first followed by the Remote repo for review. \[Hint use your knowledge of Git push and git pull commands here\]**
        
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311072538/d282a2e6-9f59-4f87-88a6-bb2d9cfdff89.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311206191/68445825-e2ee-4e8d-90b5-4b2734d47059.png align="center")
    
    **Add new commit in** `dev` **branch after adding below-mentioned content in Devops/Git/version01.txt: While writing the file make sure you write these lines**
    
* **1st line&gt;&gt; This is the bug fix in a development branch**
    
* **Added feature2 in the development branch**
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311552140/28f8e738-d3ca-4601-a112-c8147b258b38.png align="center")
    
    * **2nd line&gt;&gt; This is gadbad code**
        
    * **Commit this with the message “ Added feature3 in development branch**
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311673508/41e9f2dc-09de-44bc-8df1-688b8a318574.png align="center")
    
    * **3rd line&gt;&gt; This feature will gadbad everything from now.**
        
    * **Commit with the message “ Added feature4 in the development branch**
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311794459/0163f2b1-6ca3-4571-80c8-10f332ab06df.png align="center")
    
    `git log`: Git log is a utility tool to review and read the history of everything that happens to a repository. 
    
    `git log --oneline` - The online option is used to display the output as one commit
    
    per line.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311947576/1783c5e1-d62a-40af-97d1-7a8f844ecd9e.png align="center")
    
    **Restore the file to a previous version where the content should be “This is the bug fix in the development branch” \[Hint use git revert or reset according to your knowledge\]**
    
* `git reset` **:**  Reset the current HEAD to the specified state.
    
    syntax: `git reset <commit_ID>`
    
    In the below image, if you will do a git log you can see only two commits as the reset ones are deleted.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690312297252/271cde06-01a9-4e7a-9ba6-0f67d1c84ef8.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690312456100/29162ace-87f9-42e0-ba3a-8c0e0ac68727.png align="center")
    
    ## Task 2:
    
    * Demonstrate the concept of branches with 2 or more branches with a screenshot.
        
        `git branch`**:**
        
        A branch is a version of the repository that diverges from the main working project. It is a feature available in most modern version control systems. A Git project can have more than one branch
        
    
    **Git command** :
    
* **Create** a **new Branch**: git branch -b &lt;branch name &gt;
    
* **Show git branch**: git branch
    
* **To go to a specific branch**: git checkout &lt;branch-name&gt;
    
* **Creating and going to that branch:** git checkout -b &lt;branch-name&gt;
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690383922083/14a8edde-51c0-4db3-ab2d-9d1c897c6dc6.png align="center")

1. add some changes to `dev` the branch and merge that branch in `master`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690384018581/ac076a82-a928-486a-8d2f-937fde7fb7a4.png align="center")
    
    `git merge`: Git merge is a command that allows developers to merge Git branches while the logs of commits on branches remain intact.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690384145766/2ae1eac9-4872-4131-bd44-2c12e42af441.png align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690384232810/c0fc6e69-27b3-4d53-adb1-9814bf218341.png align="center")
    
2. As a practice try git rebase too, and see what difference you get.
    
    ### git rebase:
    
    Rebasing is the process of moving or combining a sequence of commits to a new base commit. Rebasing is most useful and easily visualized in the context of a feature branching workflow. The primary reason for rebasing is to maintain a linear project history.
    
    `git rebase <base>`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690384850780/464152e6-b54b-40bd-b7d0-b6e56884a9fa.png align="left")
    
    Thank you for reading this blog !
    
    ***Happy learning!***