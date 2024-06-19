---
title: "Day #21: Docker Important interview Questions."
datePublished: Fri Dec 29 2023 02:25:48 GMT+0000 (Coordinated Universal Time)
cuid: clqq0i1d4000008jwevf981vn
slug: day-21-docker-important-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/OQMZwNd3ThU/upload/96b20819b6fd9fdc9bd8a168156a3159.jpeg
tags: interview, docker, devops

---

1. **What is the Difference between an Image, Container, and Engine?**
    
    * *Image:* A Docker image is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, such as code, runtime, libraries, and system tools.
        
    * *Container:* A Docker container is a running instance of a Docker image. It encapsulates the application and its dependencies, providing isolation and portability across different environments.
        
    * *Engine:* The Docker Engine is the core of Docker. It's a client-server application that builds and runs Docker containers. It includes a server, REST API, and a command-line interface for interacting with containers.
        
2. **What is the Difference between the Docker command COPY vs ADD?**
    
    * *COPY:* This command is used to copy local files into the container. It is straightforward and copies files from the build context to the destination in the image.
        
    * *ADD:* While similar to COPY, ADD has additional features such as the ability to unpack compressed files and copy files from remote URLs. However, it is recommended to use COPY for basic file copying to maintain simplicity.
        
3. **What is the Difference between the Docker command CMD vs RUN?**
    
    * *CMD:* Specifies the default command to run when a container starts. It sets the default behavior of the container. You can override CMD by providing arguments during the `docker run` command.
        
    * *RUN:* This command is used during the image build process. It executes commands to install software packages, make configurations, and perform other tasks necessary for preparing the image.
        
4. **How Will you reduce the size of the Docker image?**
    
    * Use a minimal base image to reduce the initial size.
        
    * Minimize the number of layers in your image by consolidating commands.
        
    * Remove unnecessary files and dependencies after installing them to reduce the image size.
        
    * Optimize and clean up within a single RUN command to avoid creating extra layers.
        
    * Leverage multi-stage builds to separate build-time dependencies from the final image.
        
5. **Why and when to use Docker?**
    
    * *Why:* Docker ensures consistent development, testing, and deployment environments, making it easier to manage and scale applications.
        
    * *When:* Use Docker when you want to achieve consistency across different environments, simplify collaboration between development and operations teams, and deploy applications in a scalable and isolated manner.
        
6. **Explain the Docker components and how they interact with each other.**
    
    * Docker consists of the Docker Engine, Images, and Containers. The Docker Engine manages Containers using Images. Images are used to package applications and their dependencies, while Containers are the running instances of those Images.
        
7. **Explain the terminology: Docker Compose, Docker File, Docker Image, Docker Container?**
    
    * *Docker Compose:* A tool for defining and running multi-container Docker applications. It uses a YAML file to configure the application's services, networks, and volumes.
        
    * *Docker File:* A script containing instructions for building a Docker image. It defines the environment, dependencies, and configuration of the application.
        
    * *Docker Image:* A lightweight, standalone, and executable package that includes everything needed to run an application, such as code, runtime, libraries, and system tools.
        
    * *Docker Container:* A running instance of a Docker image. Containers are isolated and encapsulate the application and its dependencies.
        
8. **In what real scenarios have you used Docker?**
    
    * Used Docker for creating consistent development and testing environments across the team.
        
    * Employed Docker in a microservices architecture for managing and deploying individual components.
        
    * Integrated Docker into CI/CD pipelines for automated testing and deployment.
        
9. **Docker vs Hypervisor?**
    
    * *Docker:* Utilizes containerization, sharing the host OS kernel. It is lightweight and efficient.
        
    * *Hypervisor:* Virtualizes the entire operating system, allowing multiple OS instances on a host. It is heavier and may have more overhead.
        
10. **Advantages and disadvantages of using Docker?**
    
    * *Advantages:* Portability, scalability, resource efficiency, and consistent environments.
        
    * *Disadvantages:* Learning curve, potential security concerns, and increased complexity in some scenarios.
        
11. **What is a Docker namespace?**
    
    * A Docker namespace provides isolation for containers, ensuring that processes within a container cannot see or interfere with processes in other containers. It creates a separate namespace for each container, including the process ID namespace.
        
12. **What is a Docker registry?**
    
    * A Docker registry is a centralized repository for storing and distributing Docker images. Docker Hub is a popular public registry, but private registries can also be used for storing custom images.
        
13. **What is an entry point?**
    
    * The entry point is the command or script that runs when a Docker container starts. It defines the default behavior of the container.
        
14. **How to implement CI/CD in Docker?**
    
    * Implement CI/CD in Docker by using Docker images in the build and deployment pipeline. This involves automatically building Docker images, testing them, and deploying to production environments.
        
15. **Will data on the container be lost when the Docker container exits?**
    
    * By default, data within a container is lost when the container exits. To persist data, it should be stored in volumes or mounted from the host system.
        
16. **What is a Docker swarm?**
    
    * Docker Swarm is Docker's native clustering and orchestration solution. It allows multiple Docker Engines to work together in a swarm, enabling high availability and scalability for applications.
        
17. **Docker commands for the following:**
    
    * *View running containers:* `docker ps`
        
    * *Run container under a specific name:* `docker run --name container_name image_name`
        
    * *Export a Docker container:* `docker export -o filename.tar container_id`
        
    * *Import an existing Docker image:* `docker import filename.tar`
        
    * *Delete a container:* `docker rm container_id`
        
    * *Remove all unused resources:* `docker system prune`
        
18. **Common Docker practices to reduce the size of Docker Image:**
    
    * Use a minimal base image to reduce the initial size.
        
    * Combine commands in the Dockerfile to minimize layers.
        
    * Remove unnecessary files and dependencies after installing them.
        
    * Optimize and clean up within a single RUN command.
        
    * Leverage multi-stage builds to separate build-time dependencies.