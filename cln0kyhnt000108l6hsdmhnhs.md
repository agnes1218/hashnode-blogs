---
title: "Day 51: Your CI/CD pipeline on AWS - Part 2 🚀 ☁"
datePublished: Tue Sep 26 2023 17:17:21 GMT+0000 (Coordinated Universal Time)
cuid: cln0kyhnt000108l6hsdmhnhs
slug: day-51-your-cicd-pipeline-on-aws-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695748589962/9c12bf7a-3175-4515-8387-f83e74c3be3e.png
tags: aws, devops, ci-cd, 90daysofdevops, codebuild

---

## [What is CodeBuild?](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day51/tasks.md#what-is-codebuild-)

* AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers.
    

# [Task-01 :](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day51/tasks.md#task-01-)

**Read about the Buildspec file for Codebuild.**

A Buildspec file is a YAML file that defines the build process for your CodeBuild project. It contains a series of commands that CodeBuild will execute to build and package your application.

**Create a simple index.html file in the CodeCommit Repository.**

**you have to build the index.html using nginx server**

Create a code commit repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695744227105/335697a3-0b70-4789-af2c-ef57094bf005.png align="center")

Copy *clone HTTPS URL*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695744264543/1b6bb71d-3d53-4131-a289-19e2652aa380.png align="center")

In git bash, clone the repository to your local machine using the **git clone** command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695744386683/94f4b9d6-e4a2-45ea-9368-466c6ffd1324.png align="center")

Inside the code commit repository create an index.html file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695744610130/46302e7d-8ddf-49cc-baaf-371912954b2a.png align="left")

Save the file and commit the changes to the repository using the **git add** and **git commit** commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695744697802/66b36e7b-8a29-4eb5-b85a-f0249f1b9307.png align="left")

```yaml
git commit -m "commit message"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695744779399/0203115a-e76f-48ee-b13b-2466a65a35a0.png align="center")

Push the changes to the repository using the **git push** command.

```yaml
git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695745000464/9c58ccab-4f3c-48ce-84ef-87c0a5d4519d.png align="center")

You have a simple **index.html** file in your CodeCommit repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695745041700/d1f60c58-34dc-41da-ae82-748a38ed4049.png align="center")

# [Task-02 :](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day51/tasks.md#task-02-)

**Add buildspec.yaml file to CodeCommit Repository and complete the build process.**

Create a Buildspec file to build the file using an nginx server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695745437654/44200409-ff12-4ef3-9ad5-14c0e4beb5df.png align="center")

Below are the functions of each build step:

* The version of the Buildspec syntax we're using is stated as **version: 0.2.**
    
* **Phases**: This lists the stages of construction for our project.
    
* **install:** utilizes the apt-get package manager to install nginx on the built environment.
    
* **build** Places a copy of the index.html file in the nginx default web root directory.
    
* **post build:** If additional nginx settings are required, it is done.
    
* Indicates where the index.html file should be included in the **build artifact.**
    

With the git add and git commit commands, you can save the file and add the modifications to the repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695745717649/24567078-2b6c-4a37-8fca-15d816b85f7e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695745790965/91c1adbc-017e-49a6-8c10-9d9fe9d0c344.png align="left")

Push the changes to the code commit repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695745849802/500fc7f7-7f71-42a5-9a2a-df633ab60d0b.png align="center")

You have two files in your CodeCommit repository: buildspec.yml and index.html.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695745938373/2d959262-3a85-48a4-bec0-dda4b53ee1f7.png align="center")

**Create build project:**

Go to the CodeBuild service. Click the "Create build project" button

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746017199/a41ea189-0d86-4266-b281-6870198b5d1a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746088333/ea99f4f7-244c-4f30-a9f9-827278390a5c.png align="center")

Choose AWS CodeCommit as the source provider in the source area, then choose the repository you previously created and branch master.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746162909/f125c166-645f-4e68-9a49-8788c41b687f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746274903/a30dc3ec-6a6e-4633-959b-1827f712a6cd.png align="center")

Choose "Use a buildspec file" in the "Buildspec" section when creating a new service role.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746306927/3c16ffde-7d5e-4665-b8eb-8a130ec7143d.png align="center")

Click "Create build project" to create your project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746337528/b4dd8d59-0a38-4ceb-9452-010a0b96442f.png align="center")

The project was successfully created.

To begin a fresh build, click the "Start construction" button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746375609/09cfbac0-b031-4782-9810-da39ed680658.png align="center")

Verify the status of the successful build.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746476578/535228d1-2a29-4cc5-bee6-85beb54d7459.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746836790/4fd0008c-b96d-4109-ac52-e07b7c7b49b5.png align="center")

To include artifacts and store them in an S3 bucket as part of a CodeBuild project.

Choose "Artifacts" under "edit" after clicking.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695746899993/76d15f2f-e034-42b2-b5dc-8150f553fded.png align="center")

First, create an S3 bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695747267558/4ac71fa3-3378-4f3b-b7e7-1fab7aa3c28d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695747332173/94dfc460-7815-4f43-8ffc-045a801ca813.png align="center")

Choose the Amazon S3 type and the bucket name you created in the previous step under Artifacts.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695747435733/d5236c00-c95f-4615-9c85-16885817f0e6.png align="center")

Choose "Update artifacts."

To begin a new build after updating artifacts, click the "Start build" button once more.

The built-in S3 bucket location will receive the artifacts after the build is finished.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695748111125/180c48e1-c906-4006-91cf-45dd78a785c3.png align="center")

The path of the file, which is /var/www/html/index.html, is specified in the artifacts phase of the buildspec.yml file. You can verify that the s3 bucket has folders and an index.html file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695748239982/a48cc93b-31ae-462d-8cff-e7368e7ba7f7.png align="center")

Click on 'index.html' file, below you can see properties of file.

Click on 'open' on right-hand side.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695748305775/3da55581-8373-4d5c-8cbf-e877fcbce572.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695748333926/096871cf-26d7-404e-921d-48b07029014e.png align="center")

***Happy Learning!***