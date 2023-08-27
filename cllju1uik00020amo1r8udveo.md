---
title: "Day 27 Task: Jenkins Declarative Pipeline with Docker"
datePublished: Sun Aug 20 2023 19:20:07 GMT+0000 (Coordinated Universal Time)
cuid: cllju1uik00020amo1r8udveo
slug: day-27-task-jenkins-declarative-pipeline-with-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692559153667/f422aabb-926b-483c-bacf-25cdd84d08bd.webp
tags: docker, groovy, jenkins, ci-cd, trainwithshubham

---

let's integrate Docker and your Jenkins declarative pipeline

## Use your Docker Build and Run Knowledge

**docker build -** you can use `sh 'docker build . -t <tag>' it` in your pipeline stage block to run the docker build command. (Make sure you have docker installed with correct permissions.

**docker run:** you can use `sh 'docker run -d <image>'` in your pipeline stage block to build the container.

**How will the stages look**

```bash
stages {
        stage('Build') {
            steps {
                sh 'docker build -t trainwithshubham/django-app:latest'
            }
        }
    }
```

# Task-01

* Create a docker-integrated Jenkins declarative pipeline
    
    Click on new-items &gt; Pipeline project type &gt;Name the pipeline
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692544309040/67adc8e3-a5bc-4bc7-937f-c933e021c60d.png align="center")
    
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692556053709/524d406b-5c87-4af3-a0bb-27fa5ab5f309.png align="center")
        
    * Save and run the pipeline.
        
    * You should see the pipeline execute each stage and run your application inside a Docker container.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692555930610/9093e403-3ab0-4446-b6d2-bb681ea0f10f.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692556230567/1958f51f-8c0a-4806-9320-499688a307b2.png align="center")
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692555898606/a0b21122-d768-4808-b79d-046245495324.png align="center")

# Task-02

* Create a docker-integrated Jenkins declarative pipeline using the `docker` groovy syntax inside the stage block.
    

To include docker in the stage block, the docker pipeline and docker plugin need to be installed.

Go to Dashboard &gt; Manage Jenkins &gt; Manage Plugins &gt; Available Plugins &gt; Select the required plugins ‘Docker’ and ‘Docker Pipeline’&gt; Click on Install without restart.

Write the code

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692558017000/830cb033-b1b1-46e0-9ce5-8347cf7a8a96.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692557900064/41a31348-9938-4398-8837-d919110d92c7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692557933530/d352846f-a794-4b27-b745-ccf64d73666e.png align="center")

The above defines a pipeline with two stages: `build` and `Run`. The `build` stage uses the Docker agent to build a Docker image based on the specified image name. The `reuseNode` option is set to `true`, indicate that the same node (Jenkins agent) should be reused for both the `build` and `Run` stages. The `steps` block within the `build` stage contains a shell command that prints the Python version

We tried running docker-compose in the above code.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692558441282/165f66fe-97e3-45eb-af8f-a17f87b31032.png align="center")

save and run the pipeline.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692558384769/0ec4e6a5-49a3-4016-a994-0a6ad66d1a3c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692558410581/284d7075-24ea-4538-b7f0-e569249372f6.png align="center")

This script defines a pipeline with two stages: `Build` and `Run`. The `Build` stage uses the Docker agent to build a Docker image based on the specified image name. The `steps` block within the `Build` stage prints a message indicating that the app is being built using the Docker image.

The `Run` stage contains two shell steps that execute `docker-compose` commands. Specifically, it stops and removes any existing containers defined in your `docker-compose.yml` file using `docker-compose down`, and then starts the containers again in detached mode using `docker-compose up -d`.

I hope you like this article.

Happy learning!