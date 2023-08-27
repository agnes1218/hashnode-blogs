---
title: "Day 28 Task: Jenkins Agents"
datePublished: Wed Aug 23 2023 18:31:58 GMT+0000 (Coordinated Universal Time)
cuid: cllo2nhya000j0ajm3ty30phx
slug: day-28-task-jenkins-agents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692722161587/884c0493-1822-4976-a2b9-02f847caa1c3.png
tags: devops, jenkins, ci-cd, 90daysofdevops, trainwithshubham

---

# Jenkins Master (Server)

Jenkins’s server or master node holds all key configurations. The Jenkins master server is like a control server that orchestrates all the workflow defined in the pipelines. For example, scheduling a job, monitoring the jobs, etc.

# Jenkins Agent

An agent is typically a machine or container that connects to a Jenkins master and this agent actually executes all the steps mentioned in a Job. When you create a Jenkins job, you have to assign an agent to it. Every agent has a label as a unique identifier.

When you trigger a Jenkins job from the master, the actual execution happens on the agent node that is configured in the job.

A single, monolithic Jenkins installation can work great for a small team with a relatively small number of projects. As your needs grow, however, it often becomes necessary to scale up. Jenkins provides a way to do this called “master to agent connection.” Instead of serving the Jenkins UI and running build jobs all on a single system, you can provide Jenkins with agents to handle the execution of jobs while the master serves the Jenkins UI and acts as a control node.

## Pre-requisites

Let’s say we’re starting with a fresh Ubuntu 22.04 Linux installation. To get an agent working make sure you install Java ( same version as Jenkins master server ) and Docker on it.

Note:- While creating an agent, be sure to separate rights, permissions, and ownership for Jenkins users.

# Task-01

* **Create an agent by setting up a node on Jenkins**
    
    **Create a new AWS EC2 Instance and connect it to the master(Where Jenkins is installed)**
    
    **The connection of the master and agent requires SSH and the public-private key pair exchange.**
    
    **Verify its status under the "Nodes" section.**
    

Installed 2 ec2 instance

1. Jenkins-master
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692723559679/cdcaa39b-45b8-4e46-8af8-4e0e56fd70de.png align="center")
    
2. Jenkin-slave
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692723538461/fb1d93fc-20b8-4d95-ae8f-c125369edd04.png align="center")
    
    In the 'Jenkins-master' instance install Jenkins, the docker.
    
    **.Generate SSH keys on the “Jenkins-master” EC2 instance**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692808921883/81b075dd-3015-4612-a616-86612cf67026.png align="center")
    
    Copy the authorized\_keys
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692809009420/56de4154-762b-418d-9f50-97645fd27387.png align="center")
    

Add public key from “Jenkins-master” instance to “Jenkins-slave” instance under location “.ssh/authorized\_keys”

Jenkins-agent:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692809036424/320477da-9ddb-4021-b4ed-ee997437a23e.png align="center")

Create an agent by setting up a node on Jenkins

Go to the Jenkins dashboard, and click on “Manage Jenkins” Then

Click on “Manage Nodes and Clouds”

To create a node click on "New Node" on the left side

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692812218745/9e217959-e0f7-4045-91fa-2aeb61814d39.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692812239978/bcd8ecb6-45da-46e7-b5b2-dc52aed19b99.png align="center")

Add the private key that we created in the 'Jenkins-master' instance using ssh-keygen.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692814740658/f5b26d42-9061-4ad9-8201-8481f78aa59a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692814850743/cd6b74a4-b592-4212-b6f8-d51e32523486.png align="center")

## **Task-02**

Run your previous Jobs on the new agent

Use labels for the agent, your master server should trigger builds for the agent server.

Go to the configuration of your job, Add label expressions, in add the node label that you created.

![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQHg8Sg_C710ew/article-inline_image-shrink_1500_2232/0/1679231921521?e=1695859200&v=beta&t=JI6tiPenu56p0J8yT05FawH05zw_8Gth2LU069U2CAY align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692815143848/a2cd0a2b-60f4-4a3f-9fd4-111c0ff37f15.png align="center")

Build your project.

Check the console output for more details.

Thank you for reading this blog!

*Happy Learning!*