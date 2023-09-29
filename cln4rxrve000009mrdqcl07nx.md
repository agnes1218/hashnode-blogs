---
title: "Day 53: Your CI/CD pipeline on AWS - Part 4 🚀 ☁"
datePublished: Fri Sep 29 2023 15:43:49 GMT+0000 (Coordinated Universal Time)
cuid: cln4rxrve000009mrdqcl07nx
slug: day-53-your-cicd-pipeline-on-aws-part-4
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696002174529/596c4e90-0a5a-4fb3-b907-f88ae22fcabe.png
tags: aws, devops, codepipeline, 90daysofdevops, trainwithshubham

---

## [What is CodePipeline?](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day53/README.md#what-is-codepipeline-)

* CodePipeline builds, tests, and deploys your code every time there is a code change, based on the release process models you define. Think of it as a CI/CD Pipeline service.
    

# [Task-01 :](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day53/README.md#task-01-)

### **Create a Deployment group of EC2 Instances.**

Create a CodeDeploy application:

In CodeDeploy, go to Applications and click on 'Create application'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695995391040/42435623-0a15-4108-80c3-798d6b89da5f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695995454991/c74d5141-a9e7-498e-b418-4df58128773e.png align="center")

Create a 'service role' for enabling communication between code deployment and other AWS services. Create 'code-deploy-service-role' with the below permissions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695995732790/d0149d18-b869-4cf2-8729-a160c86d00d4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695995709193/c2d6880c-8063-4bdc-b629-a989f5ef2bb5.png align="center")

Create an Ubuntu EC2 instance:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695996540641/4359cdd5-62a7-43b2-93de-331a87d54291.png align="center")

Create a deployment group:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695996628556/c66f8b99-d1d4-4a11-b406-fd7eb983d012.png align="center")

Add a deployment group name and choose 'Service role'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695996701850/20f51c69-1d98-4322-bcc4-c1b5fc3e6670.png align="center")

Add instance name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695996791935/8da9145e-c0b8-498a-8554-9db9851bf11a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695996826297/c85ccf7c-cd2d-4b5d-89c0-5eada6be090a.png align="center")

A deployment group is created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695996891333/cca45cc6-5181-486e-8417-89ddaa3adbba.png align="center")

Install the CodeDeploy agent in the ec2 instance:

You can install the CodeDeploy agent by running the following script on your EC2 instance:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695998982527/70c53881-548a-48d2-bc71-921934644714.png align="center")

The code agent is running.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695999023791/73eda9c2-4093-4450-83fc-eea71ed8c848.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696000032195/8d75fa08-c6c7-4661-88d1-ac8494e96874.png align="center")

### **Create a CodePipeline that gets the code from CodeCommit, Builds the code using CodeBuild, and deploys it to a Deployment Group.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696000205521/ea303334-6caf-4026-b5ce-ac2154269edc.png align="center")

Enter a name for your pipeline.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696000271680/370c5499-a3b1-451f-8f8b-9362b23cc183.png align="center")

Under "Source provider," choose "AWS CodeCommit."

Select the repository and branch you want to deploy.

Click "Next."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696000704266/35cbb2b3-aada-4e6c-b206-3b6d4c6c7b13.png align="center")

Under "Build provider," choose "AWS CodeBuild."

Select "build project name."

Click "Next.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696000735818/ba2ea9de-3171-4c3e-9378-b348baf77597.png align="center")

Under "Deploy provider," choose "AWS CodeDeploy."

Select the deployment group you created earlier.

Click "Next."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696000776594/0dfb8eea-c23e-4ba5-a842-160d118a41fa.png align="center")

Review the pipeline settings and click "Create pipeline."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696000820606/1c87eed8-a2c6-4e99-9656-0f0890011f4f.png align="center")

pipeline will automatically trigger a build and deploy the new code to the EC2 instance.

Successfully created a CodePipeline that automates the deployment process.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696001190323/dba8b82f-68d9-4502-a299-e8b25cad26c7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696001208334/9c4cd9b7-8881-4d26-a82c-071fb5d15038.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696001225242/f88ca986-e9a7-463f-b740-a8024120b2e2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696001241088/55eddd0f-d00f-4ad7-a60b-4c9bc8c3be7e.png align="center")