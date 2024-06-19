---
title: "Day #20: Docker CheatSheet for DevOps"
datePublished: Wed Dec 27 2023 23:25:00 GMT+0000 (Coordinated Universal Time)
cuid: clqoeloe3000008jlg7ac1mbo
slug: day-20-docker-cheatsheet-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Ci2-X-kVIcg/upload/6d8221b0fe304b6815ca561618e62a68.jpeg
tags: docker, cheatsheet

---

## Introduction

Docker has revolutionized the way we build, ship, and run applications. This Docker cheatsheet and guide will walk you through the essential commands in a friendly and easy-to-understand manner.

### **Docker Basics:**

#### 1\. **Installation:**

Docker Desktop is available for Mac, Linux, and Windows. It simplifies the installation and management of Docker, allowing developers to get started quickly. Detailed installation instructions can be found in the [official Docker documentation](https://docs.docker.com/desktop).

* **Windows/macOS:**
    
    ```plaintext
    Download Docker Desktop from https://www.docker.com/products/docker-desktop
    ```
    
* **Linux:**
    
    ```plaintext
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
    ```
    

#### 2\. **Check Docker Version:**

```plaintext
docker --version
```

#### 3\. **Hello World:**

```plaintext
docker run hello-world
```

### **Managing Containers:**

#### 4\. **Run a Container:**

```plaintext
docker run -d --name my_container nginx
```

* `-d`: Run in the background (detached).
    
* `--name`: Assign a name to the container.
    

#### 5\. **List Running Containers:**

```plaintext
docker ps
```

#### 6\. **Stop and Start a Container:**

```plaintext
docker stop my_container
docker start my_container
```

#### 7\. **Remove a Container:**

```plaintext
docker rm my_container
```

### **Working with Images:**

#### 8\. **List Downloaded Images:**

```plaintext
docker images
```

#### 9\. **Pull an Image:**

```plaintext
docker pull alpine
```

#### 10\. **Remove an Image:**

```plaintext
docker rmi alpine
```

### **Building Images:**

#### 11\. **Dockerfile:**

Create a file named `Dockerfile` with instructions to build an image.

```plaintext
FROM ubuntu:latest
RUN apt-get update && apt-get install -y python3
```

#### 12\. **Build an Image:**

```plaintext
docker build -t my_custom_image .
```

### **Networking:**

#### 13\. **Create a Bridge Network:**

```plaintext
docker network create my_network
```

#### 14\. **Run a Container on a Specific Network:**

```plaintext
docker run --network my_network -d nginx
```

### **Data Volumes:**

#### 15\. **Create a Volume:**

```plaintext
docker volume create my_volume
```

#### 16\. **Run a Container with a Volume:**

```plaintext
docker run -v my_volume:/app/data -d my_image
```

### **Docker Compose:**

#### 17\. **Docker Compose File (docker-compose.yml):**

```plaintext
version: '3'
services:
  web:
    image: nginx
  db:
    image: mysql
```

#### 18\. **Run Docker Compose:**

```plaintext
docker-compose up
```

#### 19\. **Stop Docker Compose:**

```plaintext
docker-compose down
```

#### **20\. Login into Docker:**

```plaintext
docker login -u <username>
```

#### 21\. **Publish an image to Docker Hub:**

```plaintext
docker push <username>/<image_name>
```

#### 22\. **Search Hub for an image:**

```plaintext
docker search <image_name>
```

### **Conclusion:**

Docker is a powerful tool that can simplify your development and deployment workflows. This cheatsheet provides a starting point, but there's much more to explore. As you delve deeper into the world of containers, Docker's official documentation will be your best companion.