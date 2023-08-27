---
title: "Day 16 Task: Docker for DevOps Engineers."
datePublished: Fri Aug 04 2023 19:42:08 GMT+0000 (Coordinated Universal Time)
cuid: clkwzsjt3000609mq7wb05dbq
slug: day-16-task-docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691178083811/aa70b1c7-6c9d-4198-98c3-3eb46efb5d98.png
tags: docker, devops, 90daysofdevops, day16, trainwithshubham

---

### Docker

Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run.

## What is a container?

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries, and settings.

# Tasks

* Use the `docker run` command to start a new container and interact with it through the command line. \[Hint: docker run hello-world\]
    
    Run the below commands to install docker.
    
    `sudo apt update`
    
    `sudo apt install` [`docker.io`](http://docker.io) `-y`
    

Use the same command, to verify that docker is up and running.

```bash
docker run hello-world
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691167974095/3e006984-b6b9-4533-a80f-63bfb7067811.png align="center")

* Use the `docker inspect` command to view detailed information about a container or image.
    
    **docker inspect:-** It is a command that returns details, on Docker objects. Those objects can be docker images, containers, networks, volumes, plugins, etc. By default, docker inspects returns information in JSON format.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691170337031/87331dba-8627-49cd-82e8-bf77982b5921.png align="center")

* Use the `docker port` command to list the port mappings for a container.
    
    ![No alt text provided for this image](https://media.licdn.com/dms/image/D5612AQE-5KfAQvvvXA/article-inline_image-shrink_1500_2232/0/1675184339715?e=1696464000&v=beta&t=d6re_Ze0NQ_c6-1L_Gd04HwqEjG4t7bPSGswp3E0j3o align="left")
    
* Use the `docker stats` command to view resource usage statistics for one or more containers.
    
    **docker stats:** The docker stats command returns a live data stream for running containers.
    
    command - `docker stats [options] [containers...]`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691174177992/fea5a60d-92ca-4cbb-ad40-352e1aa78a17.png align="center")
    
    * Use the `docker top` command to view the processes running inside a container.
        
        **docker top:** Display the running processes of a container.
        
    * Use the `docker save` command to save an image to a tar archive.
        
    
    **docker save**: Save one or more images to a tar archive 
    
    command: **docker save \[options\] \[image\]**
    
    * Use the `docker load` command to load an image from a tar archive.
        
        command: **docker load \[options\]**
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691177823031/6a1c6c63-4ad4-450c-9a3a-6e9ccbeb14eb.png align="left")