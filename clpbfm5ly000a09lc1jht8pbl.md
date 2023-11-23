---
title: "Day 80 Project-1"
datePublished: Thu Nov 23 2023 16:52:40 GMT+0000 (Coordinated Universal Time)
cuid: clpbfm5ly000a09lc1jht8pbl
slug: day-80-project-1
tags: devops, jenkins, pipeline, ci-cd, 90daysofdevops, trainwithshubham

---

# Project Description

The project aims to automate the building, testing, and deployment process of a web application using Jenkins and GitHub. The Jenkins pipeline will be triggered automatically by GitHub webhook integration when changes are made to the code repository. The pipeline will include stages such as building, testing, and deploying the application, with notifications and alerts for failed builds or deployments.

## Task-01

# **Jenkins CI/CD pipeline with GitHub Webhook integration for Deploying Docker applications on EC2 instances using the declarative pipeline**

**Step — 1 Install Java**

```plaintext
sudo apt update 
sudo apt install openjdk-11-jre
```

**Step — 2 Install Jenkins**

```plaintext
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

**Step — 3 Start Jenkins**

```plaintext
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

Unlock Password Jenkins
cat /var/lib/jenkins/secrets/initialAdminPassword

```

**Step — 4 Https://Ipaddress:8080**

Make sure port 8080 is been added to a security group

![No alt text provided for this image](https://media.licdn.com/dms/image/D4E12AQGuIUFlhufSuA/article-inline_image-shrink_1500_2232/0/1671638141012?e=1706140800&v=beta&t=NIEh-gVr8jTfmfEzX2tqke0-5mw5rKRD65E_BvD3Ud8 align="left")

Go to ec2 instance

cat /var/lib/Jenkins/secrets/initialAdminPassword

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700756972009/70083db4-4242-4a0a-b560-c6458e1dab7e.png align="center")

Now Click on, “Install Suggested Plugins”

Install the suggested plugins.

**Step — 5 Setting Up Free style Project in Jenkins and generating ssh-keygen so that github communicate with jenkin server.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700757040960/c682bbda-13e6-4741-b91a-b40c9d2b89c8.png align="center")

Jenkins Dashboard, Click on “New Item”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700757177435/f33a5ac7-b1cf-4db1-985e-9f5229a5d7a4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700757228484/2ae27e69-77b7-4fe7-9245-33f5c2f51649.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700757284878/9b9b9595-8029-4492-ae3f-450d0033be9e.png align="center")

![](https://miro.medium.com/v2/resize:fit:1400/1*9QpQt-ecnlMH8dcDMxWIkg.png align="left")

**Step — 7 Creating Webhook using jenkins payload URL and selecting build triggers**.

```plaintext
http://YOUR_HOSTNAME:8080/github-webhook/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700757371322/bce3d531-bf9f-454f-9df1-29cae30c60fd.png align="center")

**Step — 8 Test build**

![No alt text provided for this image](https://media.licdn.com/dms/image/D4E12AQEGhDdNujRjmw/article-inline_image-shrink_1500_2232/0/1671638605585?e=1706140800&v=beta&t=LyQeyqmCFjgmCdN61grUYLsQyZCe3ZknDRvkaVs5vew align="left")

***Happy Learning!***