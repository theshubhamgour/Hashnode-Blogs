---
title: "Day #7 : Understanding package manager and systemctl"
seoTitle: "Understanding package manager and systemctl"
datePublished: Sat Oct 28 2023 07:25:31 GMT+0000 (Coordinated Universal Time)
cuid: clo9pwn7l000d08mo1gzv4zdg
slug: day-7-understanding-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/uZC04ASYdq0/upload/9b4cfdb58e7816e0e7b444fd7a01440e.jpeg
tags: docker, devops, jenkins, devops-articles

---

### What is a package manager in Linux?

In simpler words, a package manager is a tool that allows users to install, remove, upgrade, configure and manage software packages on an operating system. The package manager can be a graphical application like a software center or a command line tool like apt-get or pacman.

You’ll often find me using the term ‘package’ in tutorials and articles, To understand package manager, you must understand what a package is.

### What is a package?

A package is usually referred to an application but it could be a GUI application, command line tool or a software library (required by other software programs). A package is essentially an archive file containing the binary executable, configuration file and sometimes information about the dependencies.

### Different kinds of package managers

Package Managers differ based on the packaging system but the same packaging system may have more than one package manager.

For example, RPM has Yum and DNF package managers. For DEB, you have apt-get, aptitude command line-based package managers.

## Task 1: Installing Docker

Docker is a containerization platform that allows you to package applications and their dependencies into isolated units known as containers. Here's how to get it up and running:

1. Open your terminal and run the following commands:
    
    ```plaintext
    
    ubuntu@ip-172-31-8-95:~$ sudo apt update
    ubuntu@ip-172-31-8-95:~$ sudo apt install docker
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698474559788/ed4d42f1-6a00-48a1-ab91-be9d57044eb8.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698474615979/e00d3546-7be8-4e39-a296-bb4e84d52a16.png align="center")
    
2. After the installation is complete, enable the Docker service:
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~$ sudo systemctl enable docker
    ```
    
3. Start the Docker service:
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~$ sudo systemctl start docker
    ubuntu@ip-172-31-8-95:~$ service docker status
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698475138804/2e6edbe6-c704-4a8b-8c42-efef77ec8071.png align="center")
    
4. Verify the installation by running:
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~$ docker --version
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698475164754/9fa3f94a-8484-49f7-9b8d-4ef71a8fb939.png align="center")
    

## Task 2 : Installing Jenkins:

Jenkins is an open-source automation server that simplifies building, testing, and deploying software. Let's get it installed.

1. Install Java Development Kit (JDK) 11:
    
    ```plaintext
    
    ubuntu@ip-172-31-8-95:~$ sudo apt install openjdk-11-jdk
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698475414598/70963dbe-5b20-4598-b8c2-f5b804abfb22.png align="center")
    
2. Check version:
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~$ java --version
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698475514799/3cba0fe1-bf65-4386-9a44-2204ef0b307e.png align="center")
    
3. Add the LTS (Long Term Support - Release): [Learn more here](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu)
    
    ```plaintext
    sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
      https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
      https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
      /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt-get update
    sudo apt-get install jenkins
    ```
    
4. Verify Jenkins version
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~$ jenkins --version
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698475801171/a62c7def-17f1-4160-a1a4-d8e61a0d0de8.png align="center")
    
5. Start and enable the Jenkins service:
    
    ```plaintext
    sudo systemctl start jenkins
    sudo systemctl enable jenkins
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698475920570/eb5462da-43de-4b95-8de5-49c78fc5277f.png align="center")
    
6. Retrieve the initial admin password:
    
    ```plaintext
    sudo cat /var/lib/jenkins/secrets/initialAdminPassword
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698475937013/b1cf7c78-d30c-49f0-b47c-3ced4e8f9a48.png align="center")
    
7. Open your browser and navigate to [publicIP:8080](http://localhost:8080) to complete the setup using the provided password.
    
    1. NOTE : Jenkins RUN's on Port 8080
        
        Getting a loading screen check below no worries it is expected!
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698476436769/f92a091e-c766-4997-bd11-cd32a2fa8648.png align="center")
        
        we need to do few minor changes and here we go:
        
        1. Goto : Security -&gt; Security Groups (Click on Link)
            
    2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698476530336/eaf5ebf9-6d0b-40e4-a4b7-673e5e143310.png align="center")
        
        Click on : Edit Inbound Rules
        
    3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698476596833/e7275550-983d-4c0e-9823-659caf3d58db.png align="center")
        
        Click on Add Rule
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698476670857/257888c4-ab02-4dc0-b3cc-42b5341ee7d7.png align="center")
        
        Now add a new rule : add port 8080 as given below and allow the traffic from everywhere -&gt; Tap on Save rules
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698476753459/43c335e4-1e4b-4ad6-9446-f9027b601fff.png align="center")
        
        Now again hit the same [publicIP:8080](http://localhost:8080) : Congratulation you made it
        
    4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698476818060/572b0178-6c0d-4f83-8ff4-033066530db3.png align="center")
        
    5. You will be prompted to unlock Jenkins. You can find the initial administrator password in the Jenkins server logs. You can use the following command to print it:
        
        ```plaintext
        ubuntu@ip-172-31-8-95:~$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
        ```
        
    6. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698476881808/55b10413-c6ae-4059-a891-3c88319a8658.png align="left")
        
    7. Follow the on-screen instructions to complete the Jenkins setup.
        
    8. Now, Jenkins should be successfully installed on your Ubuntu system, and you can use it for continuous integration and automation tasks.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698477120345/b0d19c21-892c-4732-9d42-4c5c8dff7dbd.png align="center")
        
8. Now we will create the admin user
    
9. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698477533840/78935086-bbff-487a-a7e3-61a4d86d7ba2.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698477553993/128f948f-16ed-472e-bc91-565d60a870cb.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698477569911/8868ce9b-2daa-4cd1-9898-f377b410cd06.png align="center")
    
    Welcome to the jenkins deahboard
    
10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698477597182/f6240150-0189-48ad-ac98-4d44990c25eb.png align="center")
    
    to stop jenkins and check the status execute the below commands
    

```plaintext
ubuntu@ip-172-31-8-95:~$ sudo systemctl stop jenkins
ubuntu@ip-172-31-8-95:~$ sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698477683564/86052942-fed3-42c2-b7bf-0439cf4ae1a6.png align="center")

## Managing Services with systemctl and systemd:

systemctl is a powerful command used to examine and control the state of the systemd system and service manager, which is commonly used in most Unix-like operating systems. With systemctl, you can start, stop, enable, or disable services and check their status. This is particularly useful when working with tools like Docker and Jenkins.

## Conclusion

In a nutshell, Day 7 of #90DaysOfDevOps introduced us to the vital role of package managers in Linux, helping us install and manage software packages efficiently. We explored different types of package managers tailored to various packaging systems.

We also dived into systemctl and systemd, understanding their significance in system and service management. The day's tasks involved installing Docker and Jenkins using package managers, along with learning how to use systemctl for service control.

Join us in this exciting DevOps journey, and stay tuned for more insights and hands-on experience in the days to come. #DevOps #Linux #PackageManagement