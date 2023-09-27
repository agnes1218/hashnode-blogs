---
title: "Day 52: Your CI/CD pipeline on AWS - Part 3 🚀 ☁"
datePublished: Wed Sep 27 2023 13:41:01 GMT+0000 (Coordinated Universal Time)
cuid: cln1so4pk000309kx4iynffpd
slug: day-52-your-cicd-pipeline-on-aws-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695821983291/1d732871-53d1-4c01-841b-929e7cb6807f.webp
tags: aws, devops, codedeploy, ci-cd, 90daysofdevops

---

## [What is CodeDeploy?](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day52/tasks.md#what-is-codedeploy-)

* AWS CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.
    

CodeDeploy can deploy application content that runs on a server and is stored in Amazon S3 buckets, GitHub repositories, or Bitbucket repositories. CodeDeploy can also deploy a serverless Lambda function. You do not need to make changes to your existing code before you can use CodeDeploy.

# [Task-01 :](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day52/tasks.md#task-01-)

* **Read about Appspec.yaml file for CodeDeploy.**
    

The `appspec.yaml` file is typically used in the context of AWS CodeDeploy. The application specification file (AppSpec file) is a YAML-formatted or JSON-formatted file. The AppSpec file for an EC2/On-Premises deployment must be named appspec. yml or appspec.yaml , unless you are performing a local deployment.

The appspec.yaml file is a configuration file that defines how the deployment should proceed. It specifies the deployment process, including which files should be deployed, where they should be deployed, and any scripts or hooks that should be executed during the deployment.

The appspec.yaml file typically includes the following sections:

```yaml
version: 0.0
os: linux
files:
  - source: /path/to/source/code
    destination: /path/on/target/server
hooks:
  BeforeInstall:
   - location: scripts/before_install.sh
      timeout: 300
      runas: ec2-user
```

1. version: This section specifies the version of the AppSpec file format being used.
    
2. os: This section specifies the operating system of the target instances.
    
3. files: This section specifies the source and destination locations of the files to be deployed.
    
4. hooks: This section specifies any scripts or hooks that should be executed during the deployment, such as scripts to stop and start the application.
    

### **Deploy index.html file on EC2 machine using nginx**

For code commit and code build steps, please follow my Day 51 task article.

**Create a CodeDeploy application:**

You need to create a CodeDeploy application to deploy your **index.html** file. You can do this in the AWS Management Console.

In CodeDeploy, go to Applications and click on 'Create application'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695813705443/c4bd21e1-8fc3-44d5-89c0-588d9a8a3dbf.png align="center")

Select compute platform 'EC2/on premises' and click on 'Create application'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695813773556/c3b44491-992f-4327-baf8-2fb5495c3d14.png align="center")

Create a 'service role' for enabling communication between code deploy and other aws services.

Go to IAM service and create 'code-deploy-service-role' with below permissions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695814209504/7bd44fd6-159a-4dfc-9855-ac5d041e6748.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695814224217/24a6179c-81fc-40b4-a377-49a5230bfbb4.png align="center")

**Set up an EC2 instance:**

You will need to create an EC2 instance on which you want to deploy the **index.html** file.

Create an Ubuntu EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695814409037/2260bd7a-2f66-40cb-96ce-37adf1aba158.png align="center")

**Create a deployment group:**

Once you have created a CodeDeploy application, you need to create a deployment group. A deployment group is a set of EC2 instances where you want to deploy your application.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695814500334/7a5bf571-a432-4730-a4fc-4c410213cac1.png align="center")

Add a deployment group name and choose 'Service role'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695814726075/b1072a0d-a718-48b0-8593-bf742dc779a3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695814748547/25f6261b-bd55-45fb-b0f5-ac27f94547bc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695814833909/a4b22426-6193-476a-857c-c52c2ab77be1.png align="center")

A deployment group is created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695815534200/6ad25e7b-a73c-4ba5-bdf2-c3458304b25b.png align="center")

### **You have to setup a CodeDeploy agent in order to deploy code on EC2.**

**Install the CodeDeploy agent:**

You need to install the CodeDeploy agent on your Ubuntu EC2 instance. The CodeDeploy agent is a software package that runs on your instance and interacts with CodeDeploy to deploy your application. You can install the CodeDeploy agent by running the following script on your EC2 instance:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695816254473/cd50fc91-9c56-434a-9329-8434ceb68cc4.png align="center")

Run the script using the command bash [install.sh](http://install.sh)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695816300600/427abc70-2651-490e-9989-2910acdff0e8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695816376407/3180d0ad-9da7-4144-a8fd-b858903a1d4d.png align="center")

**Create an index.html file:**

you need to create an **index.html** file that you want to deploy. You can create a simple HTML file using any text editor.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695816624417/3b875681-8515-448e-89b4-aa4f6d6ed8ed.png align="left")

# [Task-02 :](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day52/tasks.md#task-02-)

Add appspec.yaml file to CodeCommit Repository and complete the deployment process.

You need to create an appspec.yaml file that tells CodeDeploy what to do with your application. Here is an appspec.yaml file that deploys the index.html file on nginx. also create 2 scripts for installing nginx and starting nginx.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695817146849/4b6d549b-1256-4988-a76e-30f8b7b210f3.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695817163854/9484cdf9-58b4-447c-891b-a83732b2b408.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695817225707/498bbf9c-8a11-4ebc-be8d-60a343d72bb9.png align="left")

Push all the files to code commit using 'git add' and 'git commit' commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695817766322/0e0a2a0d-fbb8-44a8-9152-ac812522ef35.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695818656941/b90545c9-2b07-4e0a-8af1-04d2caa6a82e.png align="left")

In build projects, Edit and choose 'Artifacts'.

first create 'S3 bucket'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695820207823/e59f4468-b5c7-491d-87d9-f48e96ee81dc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695820170374/53fad669-aac3-45f0-9f01-b89fa924de76.png align="center")

In Artifacts, select artifact type as Amazon S3 and choose bucket name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695820577108/ab91bcc6-e48f-4238-8111-ced3ae755625.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695820645445/0f839773-680d-4b8b-8962-8a4d6c159bd6.png align="center")

After building completion, go to S3 bucket and copy S3 url of nginx\_code\_output zip file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695820838699/7a77915a-fb17-4d19-974a-482d7b96734d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695820859438/14bcb50c-20ea-432b-98a2-7c61883080dd.png align="left")

Create deployment:

In the Application, Go to Deployments and click on 'Create deployment'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821184119/d5a153ab-9f21-43f5-b123-8dc6404d8670.png align="center")

In revision type, select Amazon S3 and paste the above copied S3 url to the revision location.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821226792/c2cfbf4d-d5ce-45ed-9a03-0a015797a416.png align="center")

Click on 'Create deployment'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821256425/de81e394-421f-47f3-b841-f51da5672fd7.png align="left")

Deployment is created. but events are in a pending state.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821305978/6bf71b1e-11a4-437e-97ca-584ecd2c48c9.png align="left")

EC2 doesn't have any role policy to retrieve the data from S3 to CodeDeploy.

Go to IAM &gt; Roles&gt; EC2-code-deploy-role

Attach that service role to EC2 instance.

Select EC2 instance, In actions, go to security and click on 'Modify IAM role'.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821413057/b4ec28f1-2404-4e1f-86d9-c68712be6888.png align="left")

Select service role.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821432608/9a0402e7-800f-46e9-a03b-5db64a1d2f40.png align="left")

After updating the IAM role, restart the code-deploy agent.

Deployment status is Succeeded.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821582515/2ebc7538-4fc7-4ee8-9ae8-f7e7e39557a9.png align="left")

Browse the instance public IP address, it will show the output of the index.html file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695821621520/b630635d-a66e-49d3-9116-3e2c088edfef.png align="center")

***Happy Learning!***