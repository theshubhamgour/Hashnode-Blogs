---
title: "Day #26: Jenkins Declarative Pipeline"
datePublished: Wed Jan 03 2024 08:57:13 GMT+0000 (Coordinated Universal Time)
cuid: clqxjon5y000009jw4u9xa9k3
slug: day-26-jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704272171529/e13994dd-6cc3-4d9a-a0eb-78c900a78509.webp
tags: devops, jenkins, pipeline

---

## Some terms for your Knowledge

**What is Pipeline -** A pipeline is a collection of steps or jobs interlinked in a sequence.

**Declarative:** Declarative is a more recent and advanced implementation of a pipeline as a code.

**Scripted:** Scripted was the first and most traditional implementation of the pipeline as a code in Jenkins. It was designed as a general-purpose DSL (Domain Specific Language) built with Groovy.

# Why you should have a Pipeline

The definition of a Jenkins Pipeline is written into a text file (called a [`Jenkinsfile`](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)) which in turn can be committed to a project’s source control repository.  
This is the foundation of "Pipeline-as-code"; treating the CD pipeline as a part of the application to be versioned and reviewed like any other code.

**Creating a** `Jenkinsfile` and committing it to source control provides a number of immediate benefits:

* Automatically creates a Pipeline build process for all branches and pull requests.
    
* Code review/iteration on the Pipeline (along with the remaining source code).
    

# Pipeline syntax

```abap
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

# **Creating your first Pipeline**

1. Provide a name for your new item (e.g. **Dec-Pipeline**) and select **Pipeline**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704271551788/134d238e-4e8b-4a39-954f-fd43da65be7a.png align="center")
    
2. Now Select Pipeline and enter the below pipeline to validate the execution steps
    
    ```abap
    pipeline {
        agent any
    
        stages {
            stage('Initalisation Phase') {
                steps {
                    script {
                        echo 'Running Stage 1...'
                    }
                }
            }
    
            stage('Staging') {
                steps {
                    script {
                        echo 'Running Stage 2...'
                    }
                }
            }
    
            stage('Execution Phase') {
                steps {
                    script {
                        echo 'Running Stage 3...'
                    }
                }
            }
        }
    
        post {
            success {
                echo 'Pipeline executed successfully!'
            }
        }
    }
    ```
    
    Let's break down the provided declarative Jenkins pipeline:
    
    ```abap
    pipeline {
        agent any
    ```
    
    * `pipeline`: This keyword marks the beginning of the pipeline block.
        
    * `agent any`: This specifies that the pipeline can run on any available agent (Jenkins node). The `any` keyword means it is not restricted to a specific agent.
        
    
    ```abap
    stages {
            stage('Initialization Phase') {
                steps {
                    script {
                        echo 'Running Stage 1...'
                    }
                }
            }
    
            stage('Staging') {
                steps {
                    script {
                        echo 'Running Stage 2...'
                    }
                }
            }
    
            stage('Execution Phase') {
                steps {
                    script {
                        echo 'Running Stage 3...'
                    }
                }
            }
        }
    ```
    
    * `stages`: This block defines the different stages of the pipeline. In this example, there are three stages: `Initialization Phase`, `Staging`, and `Execution Phase`.
        
    * `steps`: Each stage can have one or more steps defined in the `steps` block. In this case, there is a single step in each stage.
        
    * `script`: The `script` block allows you to execute arbitrary Groovy script. In each stage, it's used to print a message using the `echo` command.
        
    
    ```abap
    post {
            success {
                echo 'Pipeline executed successfully!'
            }
        }
    ```
    
    * `post`: This block is used to define post-build actions or conditions. In this case, there is a `success` block, which will be executed if the pipeline completes successfully.
        
    * `echo 'Pipeline executed successfully!'`: Inside the `success` block, it prints a success message using the `echo` command.
        
    
    In summary, this pipeline has three stages with corresponding messages, and it prints a success message if all the stages complete successfully.
    
3. Click the **Save** button and watch your first Pipeline run
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704271977328/a2c26957-4a31-4df5-8e1b-344adfa95678.png align="center")
    

## Conclusion

To sum it up, the exploration of Jenkins Multibranch Pipelines has uncovered a world of possibilities in continuous integration and delivery. With the power to automate the building and deployment of multiple branches, Jenkins proves to be a valuable asset.

As we continue the DevOps journey, mastering Jenkins Multibranch Pipelines opens the door to building resilient and scalable software solutions. Cheers to more exploration and learning in the world of DevOps!