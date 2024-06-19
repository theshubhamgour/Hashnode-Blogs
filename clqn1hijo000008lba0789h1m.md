---
title: "Day #19: Docker for DevOps Engineers"
datePublished: Wed Dec 27 2023 00:30:05 GMT+0000 (Coordinated Universal Time)
cuid: clqn1hijo000008lba0789h1m
slug: day-19-docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/QJssnBZfqmQ/upload/6508b2d1b1a0143ad23eb1884674dfd7.jpeg
tags: docker, devops, docker-volume

---

# Docker-Volume

Docker allows you to create something called volumes. Volumes are like separate storage areas that can be accessed by containers. They allow you to store data, like a database, outside the container, so it doesn't get deleted when the container is deleted. You can also mount from the same volume and create more containers having same data. [reference](https://docs.docker.com/storage/volumes/)

### **Features of Docker Volumes**

* Volumes are easier to back up or migrate.
    
* You can manage volumes using Docker CLI commands or the Docker API.
    
* Volumes work on both Linux and Windows containers.
    
* Volumes can be more safely shared among multiple containers.
    
* Volume drivers let you store volumes on remote hosts or cloud providers, encrypt the contents of volumes, or add other functionality.
    
* New volumes can have their content pre-populated by a container.
    
* Volumes on Docker Desktop have much higher performance from Mac and Windows hosts.
    

# Docker Network

Docker allows you to create virtual spaces called networks, where you can connect multiple containers (small packages that hold all the necessary files for a specific application to run) together. This way, the containers can communicate with each other and with the host machine (the computer on which the Docker is installed). When we run a container, it has its own storage space that is only accessible by that specific container. If we want to share that storage space with other containers, we can't do that.

### **Create a Volume**

Creates a new volume that containers can consume and store data in.

**COPY**

```plaintext
docker volume create --name <volumename> --opt type=none --opt device=location --opt o=bind

Where, location = Where we want to store data.
       --opt or -o = Set driver specific options.
       --type = Cluster Volume access type(mount, block).
```

Multiple containers can use the same volume in the same time period. This is useful if two containers need access to shared data.

`Volume names` must be unique among drivers. This means you cannot use the same volume name with two different drivers. If you attempt this `docker` returns an error.  
If you specify a `volume name` already in use on the current driver, Docker assumes you want to re-use the existing volume and does not return an error.

### **List of Volumes**

To list all the volumes present.

```plaintext
docker volume ls
```

### **Start a Container with Volumes**

If you start a container with a `volume` that doesn't yet exist, Docker creates the `volume` for you.

The below command will mount volume to container:

```plaintext
docker run -d --mount source=<volumename>,target=<workdir of container> -p <hostport:containerport> appname
```

`--mount`: Consists of multiple key-value pairs, separated by commas and each consisting of a `<key>=<value>` tuple.

* The `type` of the mount, which can be `bind`, `volume`, or `tmpfs`. This topic discusses volumes, so the type is always `volume`.
    
* The `source` of the mount. For named volumes, this is the name of the volume. For anonymous volumes, this field is omitted. Can be specified as `source` or `src`.
    
* The `destination` takes as its value the path where the file or directory is mounted in the container. Can be specified as `destination`, `dst`, or `target`.
    
* The `readonly` option, if present, causes the bind mount to be mounted into the container as read-only. Can be specified as `readonly` or `ro`.
    
* The `volume-opt` option, which can be specified more than once, takes a key-value pair consisting of the option name and its value.
    

### **Volume Details**

To get the volume details, use the below command:

```plaintext
docker volume inspect <volumename>
```

By default, this command renders all results in a JSON array.

### **Delete Volume**

To delete the volume attached to a container, use the below command:

```plaintext
docker stop <containername>
docker rm <containername>
docker volume rm <volumename>
```

### **docker-compose with Volume**

```plaintext
version : "3.3"
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    depends_on:
      - db
  db:
    image: mysql
    ports:
      - "3306:3306"
    environment:
      - "MYSQL_ROOT_PASSWORD=test@123"
```

In this example, I have defined two services: web and db. The web service represents the application container and the db service represents the database container.

Now using docker-compose up we can start both containers:

```plaintext
docker-compose up
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703636903337/8039f4bf-18e0-4ac7-98b8-3908db69e734.png align="center")

Use the `docker-compose scale` command to increase or decrease the number of replicas for a specific service. You can also add [`replicas`](https://stackoverflow.com/questions/63408708/how-to-scale-from-within-docker-compose-file) in deployment file for *auto-scaling*.

**COPY**

```plaintext
docker-compose up --scale web=4
```

To scale down you can use:

```plaintext
docker-compose up --scale=2
```

To down the docker-compose:

```plaintext
docker-compose down
```

To create a docker volume:

```plaintext
sudo docker volume create --name myvol_1
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703636950332/5b253d90-c1b1-4fb5-9df6-f7cfb2325fc5.png align="center")

To mount the volume in a container:

```plaintext
docker run -d -v myvol_1:/app/data <image_id>
```

![](https://miro.medium.com/v2/resize:fit:875/0*nG8DToWIaTf6t37M align="left")

For shared volumes, include it in the docker-compose.yaml file:

![](https://miro.medium.com/v2/resize:fit:875/0*gdOjwFJnIqklf2LA align="left")

To see list of volumes:

```plaintext
docker volume ls
```

![](https://miro.medium.com/v2/resize:fit:875/0*azfhf2iRNqum5Q0s align="left")

To inspect the volume:

```plaintext
docker volume inspect myvol_1
```

![](https://miro.medium.com/v2/resize:fit:875/0*6zSPlmwhwSAd-1tv align="left")

By using the docker exec command, I have verified that the data in both the containers is same:

```plaintext
docker exec -it <cont_ID> <command_oryou_can_start_bash>
```

I have used ls for the listing of all directories.

![](https://miro.medium.com/v2/resize:fit:875/0*6xD1PwM809tuIWt5 align="left")

### **Conclusion**

In conclusion, `Docker volumes` provide a way to persist and share data between containers in a Docker environment. They offer several advantages over bind mounts. When using Docker volumes, you can either create anonymous volumes or named volumes. `Anonymous volumes` are created automatically by Docker, while `named volumes` are explicitly defined in the Dockerfile or Docker Compose file.

Unlike container file systems, `volumes` exist independently of containers, allowing data to persist even when containers are stopped or removed. Volumes facilitate data sharing among containers and enable easy backup, restoration, and migration. They also enhance collaboration by separating application code from data storage concerns.

`Docker volumes` contribute to the scalability and maintainability of containerized applications, making them a fundamental component in the Docker ecosystem.