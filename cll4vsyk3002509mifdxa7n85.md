---
title: "Day 19 Task: Docker for DevOps Engineers"
datePublished: Thu Aug 10 2023 08:12:39 GMT+0000 (Coordinated Universal Time)
cuid: cll4vsyk3002509mifdxa7n85
slug: day-19-task-docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691655091191/c59a0ed3-cdda-4695-84a8-02e1afa73a08.png
tags: docker, docker-volume, 90daysofdevops, day19, trainwithshubham

---

# Docker-Volume

Docker allows you to create something called volumes. Volumes are like separate storage areas that can be accessed by containers. They allow you to store data, like a database, outside the container, so it doesn't get deleted when the container is deleted. You can also mount from the same volume and create more containers having the same data.

# Docker Network

Docker allows you to create virtual spaces called networks, where you can connect multiple containers (small packages that hold all the necessary files for a specific application to run) together. This way, the containers can communicate with each other and with the host machine (the computer on which the Docker is installed). When we run a container, it has its own storage space that is only accessible by that specific container. If we want to share that storage space with other containers, we can't do that.

## Task-1

* **Create a multi-container docker-compose file that will bring *UP* and bring *DOWN* containers in a single shot ( Example - Create application and database container )**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691648585678/128c088a-a7e4-4796-a903-2b7f8af22e56.png align="center")
    
    * **Use the** `docker-compose up` **command with the** `-d` **flag to start a multi-container application in detached mode.**
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691648536553/4b4b2f46-5336-474e-8e07-c154229b1464.png align="center")
    
* **Use the** `docker-compose scale` **command to increase or decrease the number of replicas for a specific service. You can also add** [`replicas`](https://stackoverflow.com/questions/63408708/how-to-scale-from-within-docker-compose-file) **in deployment file for *auto-scaling*.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691648468954/b93e6bc8-ecfe-48ec-92fd-cd7135848f6b.png align="center")

* **Use the** `docker-compose ps` **command to view the status of all containers, and** `docker-compose logs` **to view the logs of a specific service.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674407245447/dad8f50e-7d2c-42ab-b223-98102ae43e50.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674407354431/64820e49-eaec-4358-9691-7ec4f3bf41a7.png?auto=compress,format&format=webp align="left")

* **Use the docker-compose down command to stop and remove all containers, networks, and volumes associated with the application.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691648804488/d0bb5ec2-b920-42ab-a04d-9dd3d9868413.png align="center")

## Task-2

* **Learn how to use Docker Volumes and Named Volumes to share files and directories between multiple containers.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691650207108/69d3287a-bd6d-4ea1-bf49-a912a7935b3c.png align="center")
    
* **The command listed below will make sure that the container image has the shared volume mounted.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691652678800/3efc9557-0d96-43f5-aaea-0467d06d89a5.png align="center")
    

* **Verify that the data is the same in all containers by using the docker exec command to run commands inside each container.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691653546180/9f2f9ee1-c00e-435d-ac0e-65f00534289d.png align="center")
    

**Use the docker volume ls command to list all volumes**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691653637544/39fb0f73-e094-4be6-8452-c8eaeabda399.png align="right")

* The **docker volume rm command to remove the volume when you're done.**
    
    ![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQGIUScuUGhEnQ/article-inline_image-shrink_1500_2232/0/1674218336553?e=1697068800&v=beta&t=ZQzuRM047QQylYAjlreKWgPB1vsYl1JkN23-3m8cgJw align="left")
    

Thank you for reading!

*Happy Learning!*