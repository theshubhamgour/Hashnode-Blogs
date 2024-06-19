---
title: "Deploying a Two-Tier Application with Docker"
seoTitle: "Mastering Two-Tier Apps with Docker and MySQL"
seoDescription: "Explore the synergy of Docker and MySQL as we navigate the creation of a robust two-tier application. Uncover the magic of custom networks, troubleshoot ..."
datePublished: Tue Nov 21 2023 08:52:04 GMT+0000 (Coordinated Universal Time)
cuid: clp83ke2b001g08l1dpzie6uk
slug: deploying-a-two-tier-application-with-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700556610303/1bfd945c-b69a-4df8-9612-4708e0a5de5d.png
tags: docker, devops, trainwithshubham

---

### **Section 1 : Setting Up Your Development Environment:**

#### Installing Docker:

Walk through the process of installing Docker on your machine. Provide step-by-step instructions for different operating systems. Here we are using ubuntu as a base machine.

* Run the following command to uninstall all conflicting packages:
    

```console
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700553800887/5bb0efcb-c72c-42e4-b244-52ea37b08f11.png align="center")

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

* Set up Docker's `apt` repository. Press Yes or Y in case of prompt.
    

```plaintext
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700553832232/97012849-bdac-4fca-ab8a-1f53a7906b3f.png align="center")

* To install the latest version, run:
    

```plaintext
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

If you're getting any errors i recommend you to visit here: [Documentation](https://docs.docker.com/engine/install/ubuntu/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700553939126/cdf2c9d0-9560-40da-8803-a1d285102d76.png align="center")

* Now verify the installation execute the below command
    
    ```plaintext
    docker --version
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554008715/400342cd-b395-4eb2-a312-7c32e2a9db5f.png align="center")

Enable docker service

```plaintext
service docker start
service docker status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554063566/0dbf1b26-164b-4738-8a78-7c81424aa122.png align="center")

* Setting up the GitHub project: Below is the project we will be using :
    

```plaintext
https://github.com/theshubhamgour/two-tier-flask-app.git
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554152646/ef1dbe00-0d1b-4f73-b5a0-b951083957f4.png align="center")

* Clone the project :
    

```plaintext
git clone https://github.com/theshubhamgour/two-tier-flask-app.git
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554271329/90d6ea8a-65b5-4ccc-9032-6fcf776ea806.png align="center")

### **Section 2 : Building Docker images and containers**

Before we dive into Docker, let's briefly revisit the design of our two-tier application. Our example will consist of a simple web application as the front end and a MySQL database as the back end.

```plaintext
docker build -t flask-app .
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554513528/6bb28238-5c60-441f-8c7c-3fd269333673.png align="center")

Here's what's happening:

* **docker build:** This is like telling Docker, "Hey, get ready, we're making something cool."
    
* **\-t flask-app:** The `-t` is for "tag," and we're giving our creation a name - let's call it `flask-app`.
    
* **. (dot):** This is your way of saying, "Everything I need to build this awesomeness is right here in this directory."
    

Check the image is now created :

```plaintext
docker images
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554572070/343366b9-08e7-4d0d-8fa5-42c2d470620f.png align="center")

Now that we have created the docker image of the flask-app it is time to create the image for MySQL

```plaintext
docker run -d -p 3306:3306 -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_ROOT_PASSWORD=test@123 --name mysql mysql:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554734564/73966f9a-c6f6-4ca5-8b47-1121e8f6ee89.png align="center")

* **docker run:** Think of it as the magic words that bring your container to life.
    
* **\-d:** This one's like saying, "Hey, Docker, run this in the background so I can do other cool stuff."
    
* **\-p 3306:3306:** It's like opening a door (port 3306) on your computer so you can talk to MySQL inside the container.
    
* **\-e:** These are like secret messages you're passing to MySQL inside the container.
    
    * `MYSQL_DATABASE=testdb`: "Hey MySQL, create a database called testdb."
        
    * `MYSQL_USER=admin`: "Introducing your main user, admin."
        
    * `MYSQL_PASSWORD=admin`: "And admin's secret password is... well, admin!"
        
    * `MYSQL_ROOT_PASSWORD=test@123`: "Oh, and don't forget the big boss's password - test@123."
        
* **\--name mysql:** This is like giving your container a name – let's call it `mysql`.
    
* **mysql:latest:** You're saying, "I want to use the latest version of MySQL, please."
    

Launching Your Flask App with MySQL

```plaintext
docker run -d -p 5000:5000 -e MYSQL_HOST=mysql -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_DB=testdb  flask-app:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554844922/21a947fe-d2d2-4858-82e2-9a33ee9c53fa.png align="center")

* **docker run:** The magical phrase that commands Docker to kickstart your container.
    
* **\-d:** Shorthand for saying, "Run this in the background; I've got other tricks up my sleeve."
    
* **\-p 5000:5000:** Opens the door at port 5000 on your computer, ready to welcome your Flask app.
    
* **\-e:** More secret messages for your Flask app to talk to MySQL.
    
    * `MYSQL_HOST=mysql`: "Hey Flask, MySQL lives at the address 'mysql'."
        
    * `MYSQL_USER=admin`: "Introducing your database user, admin."
        
    * `MYSQL_PASSWORD=admin`: "Admin's secret password? You guessed it - admin."
        
    * `MYSQL_DB=testdb`: "And the chosen kingdom for your app is testdb."
        
* **flask-app:latest:** You're saying, "Docker, meet my Flask app. It's the latest and greatest version!"
    

### **Section 3 : Enable Ports on AWS**

Now let's enable the ports on Security groups on AWS

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554953814/820d2ebc-aedf-4882-800e-ec1c5e32be57.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700554997220/306a2405-71b3-49be-a2ef-9e8f83fe84f9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700555054922/651acf72-b5e9-4129-af37-ae8472533fdb.png align="center")

Now copy the public ip followed by :5000 you should resemble the below

`<public-ip>:5000`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700555145845/11cb2b6a-d90c-481d-92e1-4f3ff689dd34.png align="center")

The error message "MySQLdb.OperationalError: (2005, 'Unknown server host 'mysql' (-2)')" indicates that there's an issue with the hostname resolution for the MySQL server. This typically happens when the application (in this case, Flask app) is unable to find the host 'mysql' that you specified in the connection settings.

### **Section 4 : Docker image mapping**

Now you need to kill the running images and to do so execute the below command

```plaintext
docker kill 139604ef119c 59575e3d1c1a
```

here are the hashes as the docker container ID which you can get by running docker ps

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700555337180/e76651a0-d795-48dd-a19a-2a7fccfb021a.png align="center")

The `docker network ls` command lists all the networks created on your Docker host. You can use this command to check which networks are available and to verify if your containers are connected to the same network.

```plaintext
docker network ls
docker network create -d bridge two-tier-app-nw
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700555401793/e07b23fd-0475-424c-855b-676dccdc5c76.png align="center")

Here's a brief breakdown of the command:

* `docker network create`: Initiates the creation of a Docker network.
    
* `-d bridge`: Specifies the driver for the network. In this case, it's the default bridge driver, which is suitable for most use cases.
    
* `two-tier-app-nw`: This is the name you've given to your network. You can replace it with any name that makes sense for your application.
    

By creating a custom bridge network, you've set up an isolated environment for your containers to communicate, making it easier to manage and ensuring that your containers can find each other using their container names as hostnames.

Now incase if you are getting error while running the images execute followed by kill command

```plaintext
docker system prune
```

The `docker system prune` command is a powerful tool for cleaning up your Docker system by removing unused data, such as stopped containers, unused networks, and dangling images. It helps free up disk space and keep your Docker environment tidy.

Now we are all set to go : Let's add MySQL to the network `two-tier-app-nw` we created

```plaintext
docker run -d -p 3306:3306 -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_ROOT_PASSWORD=test@123 --name mysql --network two-tier-app-nw mysql:latest
a9e1f9730f72ce1a6ea772f319061735fd51510140cb20ec432d36a3801e84be
```

Here's a quick breakdown of your `docker run` command:

* `-d`: Runs the container in the background (detached mode).
    
* `-p 3306:3306`: Maps port 3306 on your host to port 3306 in the container, allowing you to access the MySQL service on your host machine.
    
* `-e`: Sets environment variables for configuring MySQL.
    
    * `MYSQL_DATABASE=testdb`: Creates a MySQL database named `testdb`.
        
    * `MYSQL_USER=admin`: Sets the MySQL user to `admin`.
        
    * `MYSQL_PASSWORD=admin`: Sets the password for the MySQL user.
        
    * `MYSQL_ROOT_PASSWORD=test@123`: Sets the root password for MySQL.
        
* `--name mysql`: Assigns the name `mysql` to your container.
    
* `--network two-tier-app-nw`: Connects your container to the `two-tier-app-nw` network.
    
* `mysql:latest`: Specifies the MySQL image to use, in this case, the latest version.
    

Now it's time to set the flask :

```plaintext
docker run -d -p 5000:5000 -e MYSQL_HOST=mysql -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_DB=testdb --name flask-app --network two-tier-app-nw flask-app:latest
```

Here's a quick breakdown of your `docker run` command:

* `-d`: Runs the container in the background (detached mode).
    
* `-p 5000:5000`: Maps port 5000 on your host to port 5000 in the container, allowing you to access your Flask app from your host machine.
    
* `-e`: Sets environment variables for configuring your Flask app to connect to MySQL.
    
    * `MYSQL_HOST=mysql`: Specifies the hostname of the MySQL container.
        
    * `MYSQL_USER=admin`: Sets the MySQL user to `admin`.
        
    * `MYSQL_PASSWORD=admin`: Sets the password for the MySQL user.
        
    * `MYSQL_DB=testdb`: Specifies the MySQL database to connect to.
        
* `--name flask-app`: Assigns the name `flask-app` to your container.
    
* `--network two-tier-app-nw`: Connects your container to the `two-tier-app-nw` network.
    
* `flask-app:latest`: Specifies the Docker image to use for your Flask app, in this case, the latest version.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700555863942/6cf0696b-ba5d-4cef-a0b6-4c634a5b2998.png align="center")

### **Section 6 : Inspecting Docker Network**

The `docker inspect` command is used to obtain detailed information about Docker objects, including networks. To inspect the `two-tier-app-nw` network, you can use the following command:

```plaintext
docker inspect two-tier-app-nw
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700555939424/d7feab6a-90e8-4692-a87c-e92a9d5cfc3e.png align="center")

here we validated that both the containers are on same network which is two-tier-app-nw

Now when you check your AWS on Public IP

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700556063616/1dd2524c-b196-4a4a-84be-1b9af1e32a5d.png align="center")

  
The error `MySQLdb.ProgrammingError: (1146, "Table 'testdb.messages' doesn't exist")` indicates that your Flask app is attempting to access a table named `messages` in the `testdb` database, but the table doesn't exist in the MySQL database.

Now let's create the DB in our docker container

```plaintext
docker exec -it a9e1f9730f72 bash
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700556206859/d3589b5b-6a24-4856-b4e6-5584a5306ea2.png align="center")

execute the below commands :

```plaintext
show databases;

use testdb;

CREATE TABLE messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT
);

show tables;
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700556315136/5794fa10-d7a1-41ba-9261-a3a1e59c6d8e.png align="center")

Now when you refresh you page on AWS you will get the below and congratulation you have done it!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700556379343/c106d9b0-76ac-4b78-88bd-a95d0a5ddeed.png align="center")

Enter some message and hit on Submit

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700556440644/91213378-cf46-459b-9352-51c57446e28b.png align="center")

Now lets validate it on DB

```plaintext
select * from messages;
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700556469092/099e0aec-a88a-4edb-bf30-648687f9f8c6.png align="center")

## Conclusion

In our exploration of Docker and MySQL, we've set sail into a realm of containers, networks, and data. Docker's enchanting spells, cast through `docker run` commands, allowed us to orchestrate a symphony of Flask and MySQL containers.

We carefully crafted a MySQL database, but challenges surfaced—unknown hosts and missing tables. Yet, armed with debugging tools and logs, we navigated through stormy errors, emerging victorious.

The outcome? A harmonious duo: Flask app on port 5000, MySQL guarding its treasures on port 3306. Our journey concludes with lessons learned, a resilient two-tier app, and newfound skills for future exploits.