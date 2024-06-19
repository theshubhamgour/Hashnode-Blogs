---
title: "Day #24: Complete Jenkins CI/CD Project"
seoTitle: "GitHub Integration with Jenkins: Seamless Automation Guide"
seoDescription: "Unlock the power of GitHub webhooks with Jenkins for automated builds, tests, and deployments. Enhance collaboration and streamline your DevOps workflow"
datePublished: Mon Jan 01 2024 03:47:43 GMT+0000 (Coordinated Universal Time)
cuid: clqudqxok000808js74x6acgo
slug: day-24-complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704080770508/0c5832a8-a52b-4d35-9008-14de5ecefbab.png
tags: docker, github, projects, devops, webhooks, jenkins, docker-compose

---

## **GitHub Integration with Jenkins**

In the realm of DevOps, Integration between GitHub and Jenkins stands as a pivotal point for achieving continuous integration and delivery. In this guide, we'll unravel the intricacies of GitHub webhooks, paving the way for seamless automation in Jenkins.

### **What are Webhooks?**

A `webhook` is an HTTP request, triggered by an event in a source system and sent to a destination system, often with a payload of data. `Webhooks` are automated, in other words they are automatically sent out when their event is fired in the source system.

This provides a way for one system (the source) to "speak" (HTTP request) to another system (the destination) when an event occurs, and share information (request payload) about the event that occurred.

Webhooks create the hyperlink between GitHub & Jenkins.

Any changes made to the GitHub repo will be automatically identified by Jenkins and will be pushed to the webhook URL.

### **What are Webhooks used for?**

Webhooks are used in a wide range of scenarios, including:

* Triggering CI (continuous integration) pipelines on an external CI server. For example, to trigger CI in Jenkins or CircleCI when code is pushed to a branch.
    
* Sending notifications about events on GitHub to collaboration platforms. For example, sending a notification to Discord or Slack when there's a review on a pull request.
    
* Updating an external issue tracker like Jira.
    
* Deploying to a production server.
    

Logging events as they happen on GitHub, for audit purposes.

## **How to create Webhook in GitHub?**

Steps to create webhook is given below: -

1. Go to your GitHub repository's settings page.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026169221/af8636b4-f047-4deb-8d6e-45aa99f7445b.png align="center")

Navigate to the "Webhooks" tab and click "Add webhook."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026261895/effc523f-b25a-4c39-b7fd-5b901869f82f.png align="center")

Configure the webhook by providing:

* **Payload URL:** `<Jenkins_URL>/github-webhook/`
    
* **Events:** Select the events you want to be notified about.
    
* **Secret:** Optional, but enhances security.
    
* Click "Add webhook" to finalize the configuration.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026380916/c339fbbe-42a7-43f6-b012-8974ec3d9f4a.png align="center")
    
    Don't forget to refresh the page after setting up the webhook to ensure the webhook URL is validated.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026492290/40d74b77-91e8-413a-9cd9-166cbf0915c4.png align="center")

So, basically when you create a webhook, you specify a URL and subscribe to events that occur on GitHub. When an event that your webhook is subscribed to occurs, GitHub will send an HTTP request with data about the event to the URL that you specified. If your server is set up to listen for webhook deliveries at that URL, it can take action when it receives one.

## **Jenkins Freestyle Job With Webhook**

### *Example 1: Deploying a Node Todo Application*

**Create a Freestyle Job in Jenkins:**

* Start by creating a Jenkins freestyle job named "node-todo-cicd."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026612713/65648ca9-3e41-40ce-b846-78ddf517c49f.png align="center")

**Configure the Job:**

* Source Code Management: Select Git and enter the GitHub repository link and branch name.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026689881/a07f5b09-061d-4cce-a429-b4bf9995c8c9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026713812/b19ce79f-6676-4911-8215-3ad5184a3603.png align="center")

Now Before proceeding forward make sure you are creating the development branch on github

In the Build Steps section &gt; Select Add Build Steps &gt; Select Execute Shell &gt; And type the commands required for your activity.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026794499/46c59cf2-a598-438a-994e-6414e13db878.png align="center")

Build Steps: Add an Execute Shell build step with the necessary commands.

```abap
 docker build -t todoapp .
 docker run -d --name django-todo-app -p 8000:8000 todoapp:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704026900049/6d14df3e-bcef-4331-9e8c-b24da1812be6.png align="center")

In your GitHub Repository in which you have added WebHook, make some changes in any file and then commit that changes as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704027126096/17f3586e-2109-4a4d-82f1-4ba4e7f150f4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704027194229/99df9db6-3352-4635-80f0-2340b4a3d5d5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704027244857/6ffa3214-3873-498a-bf4b-71f28a046445.png align="center")

After committing, you can go to your Jenkins Job and can see that the build is getting triggered.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704078458548/4598db97-005c-4ef8-b35d-19621715d532.png align="center")

To Solve the above issue you need to execute the below command : [Trouble Shoot Source](https://stackoverflow.com/questions/47854463/docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socke)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704027378153/a9d9b109-96ed-4aa8-ad66-2ece2d4c07b5.png align="center")

```abap
sudo chmod 777 /var/run/docker.sock
sudo usermod -aG docker $USER
sudo usermod -a -G docker jenkins
sudo reboot
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704078826362/6de6c412-6e77-4b12-bdcc-b6c7554f5b48.png align="center")

**Access Your Application:**

* Visit `<public-ip:8000>` in your web browser to view your Node todo app live.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704079064836/67484b6a-a602-4363-9936-3612a00a706f.png align="center")

### *Example 2: Docker Compose with Webhooks*

We will create a Jenkins project to run the "docker-compose up -d" command to start the multiple containers defined in the compose file. Setting up with a cleanup step in the Jenkins project to run the "docker-compose down" command to stop and remove the containers defined in the compose file.

**Enhance the Jenkins Project:**

* Modify the existing Jenkins freestyle project pipeline by incorporating Docker Compose commands.
    
* Add build steps for:
    
    ```abap
      docker-compose down
      docker-compose up -d
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704079175933/918f22f4-f4f7-48ee-a317-ea1162515ac8.png align="center")
    
    **Trigger the Build:**
    
    * Make changes in any file in your GitHub repository.
        
    * Commit the changes to trigger the build in Jenkins.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704079326259/765c1de2-ae8f-4851-a9dd-6600f422f0f1.png align="center")

You can see the build got triggered after committing the changes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704079302762/3c1ee637-4b80-4588-9c70-9ff4840306bd.png align="center")

**Resolve Docker Port Conflict:**

* If a port conflict arises, stop and remove the conflicting container using:
    
    ```abap
    docker kill <container_id> && docker rm <container_id>
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704079419049/f60e9243-84ec-4a29-927a-77b573e31397.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704079474718/7fd10a00-b3f4-4844-b798-8969c032989b.png align="center")

**Test Your Application:**

* Verify the accessibility of your application via `<public-ip:8000>`.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704079553316/2b0cb57b-0581-4b24-99e7-a44eca9c99e4.png align="center")

## **Conclusion**

In conclusion, GitHub webhooks serve as the bridge that enables real-time communication between GitHub repositories and Jenkins, triggering automated builds, tests, and deployments upon code changes. This seamless integration enhances collaboration, accelerates development cycles, and ensures an efficient continuous integration and delivery process.

By harnessing the synergy between GitHub webhooks and Jenkins, development teams can achieve greater efficiency, faster feedback loops, and a more robust and automated software delivery pipeline.

In this guide, we've executed a freestyle project on Jenkins to deploy a Node todo application on Docker. If you have questions or insights to share, feel free to leave a comment below.