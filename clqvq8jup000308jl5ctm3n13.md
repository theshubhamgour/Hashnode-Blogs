---
title: "Day #25: Complete Jenkins CI/CD Project - Continued with Documentation"
datePublished: Tue Jan 02 2024 02:25:07 GMT+0000 (Coordinated Universal Time)
cuid: clqvq8jup000308jl5ctm3n13
slug: day-25-complete-jenkins-cicd-project-continued-with-documentation
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/rH8O0FHFpfw/upload/b396fe648516c0bda47f7a57a097b8ad.jpeg
tags: docker, github, devops, jenkins

---

Introduction:

In this blog, we will delve into the step-by-step process we've covered up to Day 24 of our Jenkins CI/CD project. For a quick reference to our previous blogs, you can find them \[[here](https://theshubhamgour.hashnode.dev/day-24-complete-jenkins-cicd-project)\].

### **Steps for Jenkins CI/CD Project**

**Create a Repository on GitHub:**

* Set your email and username.
    
* Clone the repository, add files, commit changes, and push to GitHub.
    

```abap
# For setting username and email id.
git config --global user.email "your email id"
git config --global user.name "Your name"
git config --global --list -> List all the git config properties

# For cloning the repository.
git clone <Your repo URL>

 #For making this Repo as a git Repo.
 git init

 #For adding files.
 git add <filename>

 #For commiting your changs.
 git commit -m "message"

 #For pushing your local changes to remote repository.
 git push origin <branchname>
```

**Launch an EC2 Instance:**

* Install required software on your instance (docker, docker-compose, java, Jenkins).
    

```abap
# For installing docker
sudo apt-get update && sudo apt-get install docker.io

 #For installing docker compose
 sudo apt-get install docker-compose

 #For installing java
 sudo apt install openjdk-11-jre

 #For adding the Jenkins repository key to the system
 curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
   /usr/share/keyrings/jenkins-keyring.asc > /dev/null

 #For adding the Jenkins repository to the package sources
 echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
   https://pkg.jenkins.io/debian binary/ | sudo tee \
   /etc/apt/sources.list.d/jenkins.list > /dev/null

 #For installing Jenkins
 sudo apt-get install jenkins

 #Check whether Jenkins is active or not
 systemctl status jenkins
```

**Add User to the "docker" Group:**

```abap
sudo usermod -aG $USER docker
```

**Set Permissions for Docker:**

```abap
sudo chown $USER /var/run/docker.sock
sudo chmod 777 /var/run/docker.sock
```

**Build Docker Image and Run Container:**

```abap
docker build Dockerfile -t <appname>
docker run -d -p hostport:containerport <imagename>
```

To see the list of images

```abap
docker images
```

Now, to run a container using your image

To see the running containers

```abap
docker ps
docker ps -a -> For all containers whether it is running or exited or stopped.
```

**Set up Inbound Rules in Security Group:**

* Allow specific ports for accessing the application via browser.
    

**Use Docker-Compose to Manage Application:**

```abap
docker-compose up
docker-compose down
```

**Configure Jenkins:**

* Access Jenkins on port 8080 via your browser.
    
* Follow the link \[Setting up Jenkins\](Setting up Jenkins) for detailed instructions.
    

**Create Jenkins Job:**

* Follow the link \[First Freestyle Job\](First Freestyle Job) for a guide on creating your Jenkins job.
    

**Integrate GitHub with Jenkins:**

* Configure Webhooks in GitHub to trigger Jenkins jobs.
    
* Add webhook functionality to your Jenkins job.
    

**Test CI/CD Pipeline:**

* Make changes to your GitHub repo.
    
* Observe Jenkins job getting triggered.
    

## **Conclusion**

This comprehensive documentation provides a detailed walkthrough of setting up a Jenkins CI/CD project using GitHub and Docker commands. ✅

Automate your software delivery pipeline by creating Jenkins jobs, ensuring consistent and reliable deployment. Jenkins orchestrates the entire process, streamlining development workflows and enhancing efficiency.