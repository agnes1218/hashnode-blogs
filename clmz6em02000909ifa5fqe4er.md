---
title: "Day 50: Your CI/CD pipeline on AWS - Part-1 🚀 ☁"
datePublished: Mon Sep 25 2023 17:42:12 GMT+0000 (Coordinated Universal Time)
cuid: clmz6em02000909ifa5fqe4er
slug: day-50-your-cicd-pipeline-on-aws-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695663451174/29d377d1-8c3b-4428-b452-3d13fa9d6a57.png
tags: aws, devops, ci-cd, codecommit, codebuild

---

## [What is CodeCommit?](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day50/tasks.md#what-is-codecommit-)

CodeCommit is a managed source control service by AWS that allows users to store, manage, and version their source code and artifacts securely and at scale. It supports Git, integrates with other AWS services, enables collaboration through branch and merge workflows, and provides audit logs and compliance reports to meet regulatory requirements and track changes. Overall, CodeCommit provides developers with a reliable and efficient way to manage their codebase and set up a CI/CD pipeline for their software development projects.

# [Task-01 :](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day50/tasks.md#task-01-)

**Set up a code repository on CodeCommit and clone it on your local.**

Log in to the AWS Management Console and navigate to CodeCommit.

Click on Create Repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695659737499/808f990d-5df6-43bd-8bad-51c03723db1b.png align="center")

Enter a name for your repository and click on 'Create'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695659823047/7727b2a3-788c-425a-807a-9e6333d3b91a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695659841865/334211a3-f627-4a2e-bd80-3414a16c896b.png align="center")

Repository is created

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695659910500/eab0bce4-49fa-4d42-a1b5-d7bc496f0578.png align="left")

**You need to set up GitCredentials in your AWS IAM.**

Go to IAM console

Click on Users in the left-hand menu, and then click on your username.

Scroll down to the Security credentials section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695660139597/e70a3759-bdab-4448-86d8-9c74b3871d9c.png align="center")

Click on **HTTPS Git credentials for AWS CodeCommit &gt; Generate credentials**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695660213434/d6beff99-48af-4310-b780-16f595824df7.png align="left")

Click on the Download credentials button to download your Git credentials and click on 'close'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695660399291/e9a75938-26c0-422c-9dbd-b362e9de8c48.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695660421631/629f1255-45ec-46c7-b0e6-99e75979a4db.png align="center")

**Use those credentials in your local and then clone the repository from CodeCommit**

In Code Commit, Go inside your repository that you created in the above steps, in the right-hand side click on 'Clone URL' and choose 'Clone HTTPS'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695660540078/e8a9e126-5f68-4a75-92c1-40a5423c3262.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695660922230/3e114398-4554-4bb0-b518-e58904ff31f2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662355489/ee339e95-683a-4a37-a6a5-2c4cff1c8220.png align="center")

## Task-02 :

### Add a new file from local and commit to your local branch

Create a new file in the local repository directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662580229/0e33fd4b-a23b-4d6c-954a-c5920eb30df2.png align="center")

Check status using the command '**git status**'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662700988/fce52fce-fab8-404b-82f8-629982f3a9f4.png align="center")

Add the new file to your local branch using the following command:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662761277/592e1dc8-5e58-40a6-af10-4ce1f108a081.png align="left")

Commit the changes to your local branch using the following command:

```yaml
git commit -m "added new file"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662833784/c0cc6710-2030-4693-a146-deb4fcab8846.png align="center")

### Push the local changes to the CodeCommit repository.

Push the changes from your local branch to the CodeCommit repository using the following command:

```yaml
git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662903736/d375ecd3-281a-4eb6-bb40-425be7d8c18b.png align="left")

Verify that the changes have been pushed to the CodeCommit repository:

Go to the code commit repository that you created earlier, you should see the new file listed in the repository's files.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662958579/e0466148-f795-4e2c-862f-878e43596f84.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695662980693/86e40c33-e4b6-4ed1-af55-d4e1d7bdb696.png align="center")

***Happy Learning!***