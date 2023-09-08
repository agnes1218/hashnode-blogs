---
title: "Day 42: IAM Programmatic access and AWS CLI 🚀 ☁"
datePublished: Fri Sep 08 2023 12:46:38 GMT+0000 (Coordinated Universal Time)
cuid: clmald0dl000008i801jrel6t
slug: day-42-iam-programmatic-access-and-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694177141439/03293687-e12c-463b-b230-41bd1aafb77e.png
tags: aws, devops, iam, 90daysofdevops, trainwithshubham

---

## IAM Programmatic access

In order to access your AWS account from a terminal or system, you can use AWS Access keys and AWS Secret Access keys.

## AWS CLI

The AWS Command Line Interface (AWS CLI) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

The AWS CLI v2 offers several new features including improved installers, new configuration options such as AWS IAM Identity Center (successor to AWS SSO), and various interactive features.

## Task-01

* **Create AWS\_ACCESS\_KEY\_ID and AWS\_SECRET\_ACCESS\_KEY from AWS Console.**
    

Log in to your AWS Management Console.

Click on your username in the top right corner of the console and select "Security Credentials" from the drop-down menu.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694174792219/f3c6eedc-c32d-42b1-bc5e-ae2bc0dc43f1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694174933901/7cc01119-2643-480d-9568-9fc058498952.png align="center")

Click on the "Access keys (access key ID and secret access key)" section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694174981359/9b914539-35bd-4b83-b674-03c7a33fff34.png align="center")

Your access key ID and secret access key will be displayed. Make sure to download the CSV file with your access key information and store it in a secure location.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694175039925/c709ab90-f676-476d-90df-7bc1fd623659.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694175072377/17197158-a9dc-43a7-bb3b-f577de6b139c.png align="center")

### Task-02

**Setup and install AWS CLI and configure your account credentials**

**Install the AWS CLI by following the instructions for your operating system:** [https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694175276880/ac3c5e85-6002-4845-959f-8572f5049c7b.png align="center")

Once you have installed the AWS CLI, open a terminal or command prompt and run the following command to configure your account credentials:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694175941557/ba7aa9fc-f40b-4f1f-9b25-13ae596967ce.png align="center")

You will be prompted to enter your AWS Access Key ID and Secret Access Key. Copy and paste the access key and secret key from a downloaded csv file. You will also be prompted to enter your default region and output format. Choose the region that is closest to your location and select a suitable output format.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694176262719/9c16895b-ede0-4bb2-87a1-dbeedb7fdff2.png align="center")

You have now set up and installed the AWS CLI and configured your account credentials.

***Happy Learning!***