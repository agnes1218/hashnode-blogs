---
title: "Day 21 Task: Docker Important Interview Questions."
datePublished: Tue Aug 15 2023 19:13:13 GMT+0000 (Coordinated Universal Time)
cuid: cllcolpz5000109mcfz2efqgc
slug: day-21-task-docker-important-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692126726386/0cdd805a-c914-479c-85ef-7c0fe2ecf431.png
tags: docker, dockerfile, 90daysofdevops, day21, trainwithshubham

---

## Docker Interview

Docker is a good topic to ask in DevOps Engineer Interviews, mostly for freshers. One must surely try these questions in order to be better at Docker.

## Questions

* What is the Difference between an Image, Container, and Engine?
    
    **Image** - An image is a lightweight, standalone, and executable software package. It contains the code, runtime, libraries, and dependencies required for the application.
    
    **Container** - A container is an instance of an image that runs as a separate and isolated process on the host system. It encapsulates the application along with its dependencies and provides an isolated environment for running the application.
    
    **Engine** - Docker Engine consists of a server (Docker daemon) and a REST API, which enables communication with the Docker client. It is responsible for creating, starting, stopping, and managing containers.
    
* What is the Difference between the Docker command COPY vs ADD?
    
    **COPY**: The **COPY** command in Docker is used to copy files or directories from the host into the container.
    
    **ADD :** The **ADD** command also copies files and directories from the host into the container, but it has additional capabilities. It can also retrieve files from URLs and automatically decompress archives into the container.
    
* What is the Difference between the Docker command CMD vs RUN?
    
    CMD: The CMD command is used to specify the default command that should be executed when a container is started from an image. This command can be overridden when starting a container, which means that it does not have to be executed every time a container is started.
    
    RUN: RUN command, on the other hand, is used to execute a command during the image-building process. It will run command(s) in a new layer on top of the current image and commit the results. The command(s) in a RUN instruction will always be executed when the image is being built.
    
* How Will you reduce the size of the Docker image?
    
    **Choose a Smaller Base Image**: Start with a smaller base image that contains only the necessary components for your application. For example, Alpine Linux is a lightweight base image that can reduce the size of the image.
    
    **Minimize Installed Packages**: Only install the packages and libraries that are essential for your application. Remove any unnecessary tools or libraries that won't be used in production.
    
    **Avoid Unnecessary Files:** Exclude things like logs, caches, and temporary files.
    
    **Combine Commands**: Minimize the number of layers in your Dockerfile by chaining commands together. For example, you can combine `RUN` commands to install packages and clean up in a single step to avoid creating extra layers.
    
    **Clean Up**: Use the `RUN` instruction to remove temporary files and cleanup after installation to reduce the size of the image. For example, remove package cache and unused dependencies.
    
    **Compress Artifacts**: If your application includes compiled binaries or other artifacts, compress them before copying into the image. This can help reduce the final image size.
    
* Why and when to use Docker?
    
    Docker is used for the following reasons:
    
    * Achieving consistency across different environments, from development to production.
        
    * Docker images can be versioned and stored in registries. This enables you to track changes to your application and its environment over time.
        
    * Ensuring portability of applications, making it easier to deploy on various platforms and cloud providers.
        
    * Isolating applications in containers, leading to better resource utilization and enhanced security.
        
    * Facilitating microservices architecture and scaling applications efficiently.
        
    * Streamlining the development, testing, and deployment processes through containerization.
        
    
* Explain the Docker components and how they interact with each other.
    
    Docker has several components that work together to provide a platform for packaging, deploying, and running applications in containers. These components include:
    
    **Docker Engine:** The Docker Engine is the underlying technology that runs and manages the containers. It is responsible for creating, starting, stopping, and deleting containers, as well as managing their networking and storage.
    
    **Docker Daemon**: The Docker Daemon is the background service that communicates with the Docker Engine. It receives commands from the Docker CLI and performs the corresponding actions on the Docker Engine.
    
    **Docker CLI:** The Docker Command Line Interface (CLI) is a command-line tool that allows users to interact with the Docker Daemon to create, start, stop, and delete containers, as well as manage images, networks, and volumes.
    
    **Docker Registries**: A Docker Registry is a place where images are stored and can be accessed by the Docker Daemon. Docker Hub is the default public registry, but you can also use private registries like those provided by Google or AWS.
    
    **Docker Images**: A Docker Image is a lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files.
    
    **Docker Containers:** A Docker Container is a running instance of an image. It is a lightweight, standalone, and executable software package that includes everything needed to run the software in an isolated environment.
    
    Users interact with the Docker Client, which communicates with the Docker Daemon. The Docker Daemon, in turn, manages images, containers, and other resources, using the Docker Engine.
    
* **Explain the terminology: Docker Compose, Docker File, Docker Image, Docker Container?**
    
    * Docker Compose A tool that allows defining and running multi-container Docker applications using a YAML file. It simplifies the management of interconnected services.
        
    * Docker File: A text file containing instructions and commands to build a Docker image. It includes information about the base image, application code, dependencies, environment setup, and more.
        
    * Docker Image: A lightweight, standalone, and executable software package that includes all the necessary components to run an application. It serves as a template for creating containers.
        
    * Docker Container: An instance of a Docker image that runs as a separate, isolated process on the host system. Containers share the host OS kernel, making them lightweight and efficient.
        
    
* **In what real scenarios have you used Docker?**
    

Docker helps in deploying and managing individual microservices as containers.

Docker containers provide consistent testing environments

Implementing continuous integration and continuous deployment (CI/CD) pipelines to automate the deployment process.

Containers can be easily scaled up or down based on demand.

Developers use Docker to create local development environments that mirror production setups.

* **Docker vs. Hypervisor?**
    
    Docker and Hypervisor are both technologies used for virtualization, but they have key differences:
    
    * Docker: Uses containerization to run applications with shared OS resources, making it lightweight and efficient. Containers share the host OS kernel, reducing overhead and improving performance.
        
    * Hypervisor: Virtualizes the entire operating system, allowing multiple virtual machines to run on a single physical host. Each VM requires its own OS kernel, resulting in higher resource consumption compared to Docker containers.
        
* **What are the advantages and disadvantages of using Docker?**
    

Advantages:

* Isolation: Containers provide a secure and isolated environment for running applications.
    
* Portability: Docker images can run on any system with Docker installed, providing consistency across environments.
    
* Scalability: Containers can be easily scaled up or down based on demand.
    
* Rapid Deployment: Docker allows quick and automated application deployment.
    
* Simplified Management: Docker provides tools for easy container management.
    

Disadvantages:

* Learning Curve: Understanding Docker and its components might require time and effort.
    
* Limited GUI Support: Docker primarily focuses on command-line interfaces.
    
* Security Concerns: Misconfigured containers can pose security risks.
    
* Container Sprawl: Poor management may lead to an excessive number of containers.
    

* **What is a Docker namespace?**
    

Docker namespaces are a technology used to provide isolation for various resources within a container. Each container has its own unique namespace, meaning that the processes running inside a container cannot see processes in other containers or the host system. Namespaces isolate process IDs, network interfaces, mount points, users, and more, making containers secure and independent.

* **What is a Docker registry?**
    

A Docker registry is a repository that stores Docker images. It serves as a central location where developers can push and pull images. Public Docker registries like Docker Hub are freely accessible by anyone, while private registries can be used for internal image sharing within organizations.

* **What is an entry point?**
    

An entry point is a user-defined command or script specified in a Docker image that is executed when the container starts. It defines the default behavior of the container. The entry point can be overridden by providing a command during the container launch.

* **How to implement CI/CD in Docker?**
    

To implement CI/CD in Docker, you can use a combination of tools like Jenkins, GitLab CI/CD, or Travis CI along with Docker. Here's a basic outline:

1. Set up a CI/CD pipeline using your preferred CI/CD tool.
    
2. Configure the pipeline to build a Docker image during the build phase.
    
3. Push the built image to a Docker registry as an artifact.
    
4. Use Docker Compose or Kubernetes to deploy the image to the target environment during the deployment phase.
    

* **Will data on the container be lost when the Docker container exits?**
    

By default, data on a Docker container will be lost when the container exits. Containers are designed to be ephemeral and disposable. However, you can use Docker volumes or bind mounts to persist data outside the container, ensuring that it is retained even after the container is stopped or removed.

* **What is a Docker swarm?**
    

Docker Swarm is a native clustering and orchestration solution for Docker. It allows you to create and manage a swarm of Docker nodes (hosts) as a single virtual system. Docker Swarm enables high availability, load balancing, and easy scaling of services across multiple nodes, making it suitable for deploying and managing containerized applications in a distributed environment.

* **What are the Docker commands for the following?**
    
    * view running containers
        
        ```bash
        
        
        docker ps 
        ```
        
    * command to run the container under a specific name
        
        ```bash
         docker run --name <container_name> <image>
        ```
        
        * command to export a docker
            
            `docker save -o <output_file_name.tar> <image_name>`
            
    * command to import an already existing docker image
        
        ```bash
        
        
        docker load -i <input_file_name.tar> 
        ```
        
    * commands to delete a container
        
        ```bash
        docker rm <container_id> docker container rm <container_id>
        ```
        
    * command to remove all stopped containers, unused networks, build caches, and dangling images
        
        ```bash
        docker system prune -a 
        ```
        
* What are the common Docker practices to reduce the size of Docker Images?
    
    Use below practice to reduce size of docker image
    
    * Use multi-stage builds to minimize the number of layers.
        
    * Choose a smaller base image that includes only necessary dependencies.
        
    * Remove unnecessary files and directories after installing dependencies.
        
    * Optimize package installation commands by avoiding unnecessary package caching.
        
    * Compress assets and clean up temporary files in the same layer.
        
    * Minimize the number of layers by combining related commands.
        
    * Avoid installing unnecessary build tools in the final image.
        

Thank you for reading this article.

*Happy Learning!*