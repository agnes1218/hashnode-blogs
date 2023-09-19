---
title: "Day 46: Set up CloudWatch alarms and SNS topic in AWS"
datePublished: Tue Sep 19 2023 07:29:38 GMT+0000 (Coordinated Universal Time)
cuid: clmpzvpvr000509jlb8xr3kti
slug: day-46-set-up-cloudwatch-alarms-and-sns-topic-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695108489415/678036e8-6b69-4a5e-b3cd-6693e04c2729.png
tags: aws, devops, cloudwatch, sns, trainwithshubham

---

## What is Amazon CloudWatch?

Amazon CloudWatch monitors your Amazon Web Services (AWS) resources and the applications you run on AWS in real-time. You can use CloudWatch to collect and track metrics, which are variables you can measure for your resources and applications.

## What is Amazon SNS?

Amazon Simple Notification Service is a notification service provided as part of Amazon Web Services since 2010. It provides a low-cost infrastructure for the mass delivery of messages, predominantly to mobile users.

## Task :

Create a CloudWatch alarm that monitors your billing and sends an email to you when it reaches $2.

**To enable the monitoring of estimated charges**

1. Open the AWS Billing console at [https://console.aws.amazon.com/billing/](https://console.aws.amazon.com/billing/).
    
2. Choose Billing Preferences from the navigation bar.
    
3. Decide on Billing Notifications Received.
    
4. choose Preferences to save.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695107144503/307bb9e2-0f2f-436d-a06d-50e34767cb72.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695107176906/d81bc213-5f98-42c6-b772-ce5d55688465.png align="center")

### Creating a billing alarm

Log in to the AWS management console and go to the cloud watch section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695104122924/04391f9f-8202-4c92-a53b-1397609cb91a.png align="center")

Click on Create Alarm

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695104476900/7df99f33-c56c-47cf-b434-9186b93e244c.png align="center")

Choose Billing in Browse, then select Total Estimated Charge.

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQFX10Ls9_dhTw/article-inline_image-shrink_1500_2232/0/1679470806931?e=1700697600&v=beta&t=2Jy3qdJyVupWJN-RmHPGqk1fsjsf4vkG-a4ONY4EVPk align="left")

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQGeB9ryjyNmdw/article-inline_image-shrink_1500_2232/0/1679470979330?e=1700697600&v=beta&t=_GNwDqx-arQesZ8JQ0cK1im5F9ZWTtojNQYKWToqgcM align="left")

Choose metric after selecting the Estimated Charges metric checkbox.

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQFOb7JbicfpwA/article-inline_image-shrink_1500_2232/0/1679471100555?e=1700697600&v=beta&t=xlZYxJBrjvf_Wfjeh5Mz7Z0hK4eC3b40h3T7w41vkaE align="left")

Choose maximum under statistic. Select a period of 6 hours

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQEAOdC9iehx8w/article-inline_image-shrink_1500_2232/0/1679471242752?e=1700697600&v=beta&t=WV3VhfnaPNsa0kqp2W3BSITu0-p4FDlrdCMhUTey3U4 align="left")

Choose Static as the threshold type. Choose Greater for Whenever EstimatedCharges is.

**Choose a threshold amount to $2.**

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQE6AmS7Tyj8Rw/article-inline_image-shrink_1500_2232/0/1679471313511?e=1700697600&v=beta&t=oFjKgMiWg45sxDahxefk2sqU9oa2w0Hu8jKdpyugiUg align="left")

To get notifications while your alarm is in the ALARM state, enter an Amazon SNS subject under Notification.

By choosing "Create a new topic," you can either choose an already-existing Amazon SNS topic or start a brand-new one.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695107417367/8e959cb7-4ef6-4f0b-9087-4211261829ab.png align="left")

Choose Add Notification if you want your alarm to deliver different alerts for the same alarm condition or for several alarm states.

select Next.

Give your alarm a name under "Name and description."

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQGrXwzrq_Cxag/article-inline_image-shrink_1500_2232/0/1679471595393?e=1700697600&v=beta&t=lvC2GYllTNKI5u3VNCZKBRmox1y07Lp11dleZnlhfSc align="left")

Click on "**Create alarm**"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695107795159/a2243c8a-cac7-4b12-a477-ac903aac01fa.png align="center")

Click on "**Delete**" to delete the alarm

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695107842351/d985c47c-5bdd-480a-8381-fbfed2bc9728.png align="center")

***Happy Learning!***