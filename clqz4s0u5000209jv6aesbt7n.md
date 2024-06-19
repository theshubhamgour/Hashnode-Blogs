---
title: "Day #27 : Jenkins Declarative Pipeline with Docker"
datePublished: Thu Jan 04 2024 11:35:28 GMT+0000 (Coordinated Universal Time)
cuid: clqz4s0u5000209jv6aesbt7n
slug: day-27-jenkins-declarative-pipeline-with-docker
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Hcfwew744z4/upload/af023ea3fe39a096f268adb335ad95c1.jpeg
tags: docker, devops, jenkins, pipeline

---

## **Getting Started**

1. **Open Jenkins:** Go to Jenkins in your web browser.
    
2. **Log In:** If you're not logged in, enter your Jenkins credentials.
    
3. **Dashboard:** You'll land on the Jenkins dashboard after logging in.
    

## **Creating a New Jenkins Job**

1. **New Job:** Look for an option like "New Item" or "Create New Job" on the dashboard and click it.
    
2. **Job Details:**
    
    * **Name:** Give your job a name.
        
    * **Type:** Choose "Pipeline" as your job type.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704366558027/75d0bd80-9971-458c-b171-101f6854f166.png align="center")

**Configure Pipeline**

* **Save:** Save your job configuration after entering the pipeline script.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704367112312/d11e52a5-1e42-46fe-a25e-e33831324ddd.png align="center")
    
    Use the following pipeline script:
    
    ```abap
    pipeline {
        agent any
    
        stages {
            stage('Cloning Repository') {
                steps {
                    git 'https://github.com/theshubhamgour/node-todo-cicd.git'
                }
            }
    
            stage('Build') {
                steps {
                    sh 'docker build -t todo-cicd .'
                }
            }
    
            stage('Testing') {
                steps {
                    echo 'Testing Success'
                }
            }
    
            stage('Deploying') {
                steps {
                    sh 'docker-compose down'
                    sh 'docker-compose up -d'
                    sh 'docker run -dp 8000:8000 todo-cicd'
                }
            }
        }
    }
    ```
    
* Once you've configured your pipeline script, save your job configuration.
    

## **Building Your Pipeline**

**Trigger Build:** Manually start a build or set up triggers for automatic builds on code commits.

**Check Console Output:** Monitor the progress of your pipeline by checking the "Console Output."

**Verify Application:** Make sure your application is working on port 8000.

* You can manually trigger a build of your pipeline job or set up triggers based on events like code commits. it failed earlier because the port was already occupied so we killed the existing container and then the issue was resolved
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704367523142/46a19737-07a7-402d-9bc0-250055dddba6.png align="center")
    

**Check the "Console Output"**

* Review the "Console Output" to monitor the progress of your pipeline.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704367599263/d8d8270d-8991-4675-aee3-c4b61ef4282b.png align="center")

**Verify Application**

* Check whether the application is working on port 8000.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704367620060/b0998a65-b880-46a3-a5bd-c8c6cafb37ed.png align="center")
    

### **Concluding the Jenkins-Docker Integration**

By combining Jenkins and Docker, we've simplified and accelerated our software development process. This integration ensures that our applications are built, tested, and deployed consistently. Developers can now deliver high-quality software faster and with confidence.