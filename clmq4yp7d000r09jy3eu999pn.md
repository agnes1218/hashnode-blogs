---
title: "Day 47: Test Knowledge on aws 💻 📈"
datePublished: Tue Sep 19 2023 09:51:55 GMT+0000 (Coordinated Universal Time)
cuid: clmq4yp7d000r09jy3eu999pn
slug: day-47-test-knowledge-on-aws
tags: aws, 90daysofdevops, trainwithshubham, tws, day47

---

## Task-01

**Launch an EC2 instance using the AWS Management Console and connect to it using SSH.**

Click on the "Launch Instance" button to start the instance creation process

Select an Amazon Machine Image (AMI) to use for the instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695109742106/2eb58fc9-0dbd-4252-a65a-c2d559f9d7c7.png align="center")

Configure the instance details such as VPC, subnet, security groups, and storage. click on 'Launch instance'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695110275395/9c972c68-9bfb-44ee-9263-90b1ad04b2a1.png align="center")

Launch instance

Click on the "Connect" button to view the connection details.

Connect to the instance using the SSH client of your choice

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695110757967/fce10f15-3ae6-4805-9d01-aa6c0a02b625.png align="left")

**Install a web server on the EC2 instance and deploy a simple web application.**

Once connected to the instance, update the package manager and install the web server (e.g. Apache, Nginx).

```yaml
sudo apt-get install apache2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695110851177/b96e7507-8a64-45bc-a6e1-f1d8411c57d8.png align="center")

Start apache service and check status of apache service.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695110970731/587415c0-96fe-4c09-9a4d-e11ea27ac559.png align="center")

Go inside directory /var/www/html.

Create a new index.html file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695112168594/162f4a12-488e-4aba-93e2-417dd3c60bcf.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695112219755/48ff1554-472e-4fe6-8b8d-20448e74e715.png align="center")

**Monitor the EC2 instance using Amazon CloudWatch and troubleshoot any issues that arise.**

Go to the Amazon CloudWatch dashboard.

Go to the Amazon EC2 console and select the instance you want to monitor.

Click on the "Monitoring" tab and enable "Detailed monitoring"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695112529506/dfbb14e5-c5c5-4657-a025-51bdfae4df63.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695112549125/efbeaea4-a972-417a-8789-415a466256ed.png align="center")

Go to the Amazon CloudWatch console and select the "Metrics" page.

Click on the "EC2" tab to view the available EC2 metrics.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695112602551/82c62419-1ad6-4d7f-ad2f-bde0c91b0dd4.png align="center")

Configure the CloudWatch alarm for the selected metric.

Click on the "Create Alarm" button to set up an alarm.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695113001362/cf226c3a-e19d-4bf5-aa5e-c7d7b9266641.png align="center")

Select the metric CPU utilization

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695113079539/b0f62e3f-60b1-43ea-b9e6-e43b6d6a6598.png align="center")

Choose the condition that will trigger the alarm (e.g. when the CPU utilization is above a certain threshold for a certain amount of time).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695113124925/b4368e82-725c-4dff-9d27-791eb768ae2d.png align="center")

Set up additional alarm parameters such as name, description, and notification settings.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695113376872/0be12554-06b6-47b1-b98a-4c70cc5bf0bb.png align="center")

Click on '**Create alarm**'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695113415302/0ed039a2-6ccf-4342-8641-e4c1832a6b10.png align="center")

Alarm is created

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695113793888/eb4792ff-59d1-47c3-b561-e7b3229ea030.png align="left")

If an alarm is triggered, go to the CloudWatch dashboard to view the metrics and logs for the instance.

## Task-02

Create an Auto Scaling group using the AWS Management Console and configure it to launch EC2 instances in response to changes in demand.

First, create a 'Launch Template' from the ec2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115039592/1a1fa326-f72b-474c-854b-5f7aec4ae974.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115125887/487c5ab0-0728-4412-9869-59af7bba2d53.png align="center")

Launch template is created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115150709/b28916b6-88e4-4293-a87c-db1af8a53e43.png align="center")

Click on the "Create Auto Scaling group" button to start the creation process.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115212877/cb2b849f-2698-4562-b38f-5a97f47aac2e.png align="center")

Set up the scaling policies to determine when to launch new instances. configure desired, minimum, and maximum capacity of instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115317032/4d01e0f5-9866-4017-a1b1-9b562c751695.png align="center")

Select 'Target tracking scaling policy' and choose 'metric type' to CPU utilization which will create an alarm.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115391128/a955e584-e41f-4901-8b0d-3f686a7d1ae6.png align="center")

**Use Amazon CloudWatch to monitor the performance of the Auto Scaling group and the EC2 instances and troubleshoot any issues that arise.**

Target tracking policy in autoscaling creates 2 alarms with 2 different conditions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115464452/4eef04ea-3403-4a2f-97c3-7079873108fc.png align="center")

Once the alarm is set up, it will start monitoring the specified metric for the Auto Scaling group. If the metric exceeds the threshold that you have set, the alarm will be triggered and take the action that you have specified.

Go to the auto-scaling group that we created, Click on the "Monitoring" tab, and enable "Auto scaling group metric".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115511058/2e1e6724-c3f4-44f3-8f83-b5395bed07a7.png align="center")

You can also create an alarm by going to the CloudWatch dashboard.

Click on the "Create Alarm" button to set up an alarm.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115621534/b0e26d4b-b731-4183-a7af-98082075be45.png align="center")

Click on 'By Auto Scaling Group'.

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQE2n2lLFN_KNA/article-inline_image-shrink_1500_2232/0/1677237039924?e=1700697600&v=beta&t=0eUl6XMdrEuQteiKT0Q9znOkyW5isMLFc4WtXdpRWA4 align="left")

Click on 'By Auto Scaling Group'.

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQGShkQ9yT8rNQ/article-inline_image-shrink_1500_2232/0/1677237058805?e=1700697600&v=beta&t=ioJTaHZHTrvmXjthGxbfK9R0DOqGh0MpedcEwUNgT3g align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115821428/6d5c3327-41d0-45d0-8c1c-cdbb1ddfb213.png align="center")

Once the alarm is created, it will start monitoring the specified metric and trigger the configured action if the conditions are met.

**Use the AWS CLI to view the state of the Auto Scaling group and the EC2 instances and verify that the correct number of instances are running.**

Install and configure the AWS CLI on your local machine.

Install aws cli using a command.

```yaml
sudo apt-get install awsli
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695115941619/481e4724-8d26-43bf-a6bc-7a9b400279cf.png align="center")

Configure AWS cli

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695116822972/8ddef7f6-8c3d-4183-84ba-719084d0ff71.png align="left")

**Use the below command to view the state of the Auto Scaling group and the instances running in it.**

```yaml
aws autoscaling describe-auto-scaling-groups
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695116929612/cc1491a2-38bc-45db-a02d-dc1fb2561d17.png align="center")

There are 2 instances running which are launched by the auto-scaling group because we chose the desired capacity value is 2.

**Use the below command to view the state of the EC2 instances launched by the Auto Scaling group.**

```yaml
aws ec2 describe-instances
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695116998057/7ff20a40-32c1-4382-b84d-170434363ae8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695117058281/e7d1cb57-32c5-4761-a198-329136ec8aca.png align="center")

***Happy Learning!***