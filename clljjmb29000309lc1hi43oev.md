---
title: "Day 26 Task: Jenkins Declarative Pipeline"
datePublished: Sun Aug 20 2023 14:28:05 GMT+0000 (Coordinated Universal Time)
cuid: clljjmb29000309lc1hi43oev
slug: day-26-task-jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692541627101/fd7aa0a5-921d-469c-b374-bb5011073d50.jpeg
tags: continuous-integration, continuous-deployment, jenkins, 90daysofdevops, trainwithshubham

---

**What is a Pipeline -** A pipeline is a collection of steps or jobs interlinked in a sequence.

**Declarative:** Declarative is a more recent and advanced implementation of a pipeline as a code.

**Scripted:** Scripted was the first and most traditional implementation of the pipeline as a code in Jenkins. It was designed as a general-purpose DSL (Domain Specific Language) built with Groovy.

# Why you should have a Pipeline

The definition of a Jenkins Pipeline is written into a text file (called a [`Jenkinsfile`](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)) which in turn can be committed to a project’s source control repository.  
This is the foundation of "Pipeline-as-code"; treating the CD pipeline as a part of the application to be versioned and reviewed like any other code.

**Creating a** `Jenkinsfile` and committing it to source control provides a number of immediate benefits:

* Automatically creates a Pipeline build process for all branches and pull requests.
    
* Code review/iteration on the Pipeline (along with the remaining source code).
    

# Pipeline syntax

```bash
pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                // 
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}
```

# Task-01

* Create a New Job, this time select Pipeline instead of Freestyle Project.
    
    Create a Jenkins declarative pipeline select new items &gt; pipeline and give the pipeline name.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692539773828/ff2f4186-31ee-4a5b-8497-49726635715e.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692539904432/3abca6c6-07cb-4c67-bcf1-0b9d762e8e2a.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692540096897/677d3c49-c3a5-451b-a818-7fedab6afe13.png align="center")
    
    **Pipeline:**
    
    The Declarative pipeline should start with the pipeline block and this is the mandatory block.
    
    **Agent**:
    
    Agent signifies where the Jenkins build job should run. In this case, we have selected agents as any.
    
    **Stages:**
    
    stages block consists of different executable stage blocks. we have name stage “Hello”.
    
    **Steps:**
    
    Steps blocks consist of the actual operation which needs to be performed inside Jenkins.
    
    we are printing “**Hello World**“.
    

You can manually build the project by clicking on "**Build Now**".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692540502247/5c093f7a-3318-4afb-bb27-4815d63e3f01.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692540477119/2fced705-f7d3-4bec-9cba-8e19f4885299.png align="center")

Thank you for reading this blog!

**Happy learning!**