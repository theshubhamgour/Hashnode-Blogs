---
title: "Day #28: Jenkins Agents"
seoTitle: "A Step-by-Step Guide to Setting Up Agent"
seoDescription: "This comprehensive guide takes you through installing Java, configuring Docker, and setting up Jenkins agents to enhance your CI/CD workflows."
datePublished: Mon Jan 08 2024 08:30:56 GMT+0000 (Coordinated Universal Time)
cuid: clr4ny3zm000b09l4f27r29dn
slug: day-28-jenkins-agents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704701030037/6ebed4c2-2194-48ff-b3ad-8bc132e7381c.png
tags: docker, projects, devops, jenkins, pipeline

---

The `Jenkins architecture` is designed for distributed build environments. It allows us to use different environments for each build project balancing the workload among multiple `agents` running jobs in parallel.

The `Jenkins controller` is the original node in the Jenkins installation. The Jenkins controller administers the Jenkins agents and orchestrates their work, including scheduling jobs on agents and monitoring agents.

### **What is the Jenkins Master (Server)?**

Jenkins’s server or master node holds all key configurations. Jenkins master server is like a control server that orchestrates all the workflow defined in the pipelines. For example, scheduling a job, monitoring the jobs, etc.

This node manages other nodes running the Jenkins Agent.

### **What is a Jenkins Agents (Formerly Slave)?**

An `agent` is typically a machine, or container, which connects to a Jenkins controller and executes tasks when directed by the controller.

`Agents` may be connected to the Jenkins controller using either local or cloud computers. It requires a Java installation and a network connection to the Jenkins controller.

`Jenkins Agent` is a worker node that executes the tasks and builds assigned by the Jenkins Master. It works as a distributed system where the Jenkins Master assigns tasks to Jenkins Agents, which then execute the tasks on the machines they are running on.

When you create a `Jenkins job`, you have to assign an `agent` to it. Every `agent` has a label as a unique identifier. The `agent` section in the Pipeline specifies where the entire Pipeline, or a specific stage, will execute in the Jenkins environment.

### **What is a Jenkins Node?**

A `Jenkins node` is an umbrella term for Agents and Controllers, regardless of their actual roles. A node is a machine on which you can build projects and pipelines. Jenkins automatically monitors the health of all connected nodes, and if metrics go below a threshold, it takes the node offline.

## Pre-requisites

Let’s say we’re starting with a fresh Ubuntu 22.04 Linux installation. To get an agent working make sure you install Java ( same version as jenkins master server ) and Docker on it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704693818114/281f0e29-578f-47d0-8890-f3cd997ee648.png align="center")

Install Jenkins on Jenkins-Master : Refer this - [`Getting Started with Jenkins 😃`](https://theshubhamgour.hashnode.dev/day-22-getting-started-with-jenkins)

* Jenkins Master is installed and running on another machine.
    
* Docker is installed on the Ubuntu machine.
    

```abap
sudo apt update
sudo apt install fontconfig openjdk-17-jre
```

Generate an SSH key on the Jenkins master to establish a secure connection with the agent:

```abap
ssh-keygen
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704696777522/93d3e2c3-d409-452b-9899-9a10fdb5cf16.png align="center")

Copy the generated public key (`id_`[`rsa.pub`](http://rsa.pub)) and add it to the `authorized_keys` file on the agent.

Verify the Master-Agent connectivity:

```abap
cat id_rsa.pub
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704696842206/304455de-b0a9-4c08-a375-0dc8efb96cef.png align="center")

Now go to agent and paste the file on `authorized_keys`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704697001751/e03fde35-d18c-4fff-88f4-9971540956bf.png align="center")

Now to verify the Master-Agent connectivity we will execute the below command

```abap
ssh ubuntu@<public-ip>
ssh ubuntu@3.106.133.96
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704697241765/0cded5d5-89ff-4445-b8c1-3f57c02a79d0.png align="center")

See the above was success which means master and node can be connected via ssh

## **Jenkins Agent Setup**

* Navigate to Jenkins and click on "Manage Jenkins."
    
* Select "Manage Nodes and Clouds."
    
* Click on "New Node" to set up a new agent.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698057370/d8757c2d-e374-4bfd-a965-4314bf1222f5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698094090/366b50e9-f978-4f1a-9280-5c7043438267.png align="center")

* Provide a Node name (e.g., `development-server`) and set the number of Executors (CPU cores).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698131215/1b4e1276-78f2-4b95-891d-1192fd592823.png align="center")

Now Create a directory in agent and copy the directory path using pwd

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698267173/f2c7e867-d353-4fe5-b8f5-17261de2550b.png align="center")

Number of Executors meaning the number of CPU's form the node we want to dedicate for builds and operations

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698607961/8a196b83-5b02-4a6e-8182-0316e540142f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698635998/2e445a6f-37de-4c7f-bcef-ed38c005d8f6.png align="center")

Add credentials by entering the private key from the Master node.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698414762/3e4045ae-3cf9-4bec-a1aa-a7aa47c39a5e.png align="center")

To get the private key you need to navigtate to .ssh/id\_rsa

```abap
cd .ssh
cat id_rsa
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698543607/e142ae09-4a96-4166-8bbd-f8cffc4c0c7c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698524107/23245ca2-7f42-42ba-bcbc-3e18a5bef301.png align="center")

Your Node is configured let's check the connectivity

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704698769148/63655d4c-81a2-4db4-a9e9-bad828e8a832.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704699002322/41a4e42c-894f-43c6-8cd9-be8a126d6e0e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704699024784/c37ad5d9-66f7-444f-8871-a41ea8c2887e.png align="center")

The above message indicates that the node is connected to the master and is ready for build execution

## **Creating a Jenkins Job with Node Configuration:**

* Create a new Jenkins freestyle project (e.g., "Node-todo-cicd").
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704699355600/d04bc564-e8e8-4e5d-9edf-336999d9507b.png align="center")

Enter the details in the pipeline by choosing pipeline script from SCM as we will use the jenkins file from our central repo and we are using development branch as this is for the development environment

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700041988/1f87a880-75f7-4e02-b29c-a4629c28b99a.png align="center")

In order to run it on the node we will need to setup the agent to development-server which is the name we have given earlier to our node

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704699667553/efa85678-5ede-4c98-8a4c-f653fea59047.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700064301/4682e6e9-46d1-4b5b-8c5c-b41c0d1fabb9.png align="center")

Once the above is configured we will now build the project

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700212453/6ee414de-fdd0-4c92-b207-f4d07a29301f.png align="center")

As expected the build failed it is because we haven't added the credentials of docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700228739/14855207-b4fe-4ac9-b07c-bb78f99fa4cb.png align="center")

This can be validated on the logs

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700263156/bdb40146-1c2d-4d9e-a8d1-926fb0d84a19.png align="center")

* Navigate to "Manage Jenkins" &gt; "Credentials."
    
* Select global credentials and add Docker credentials.
    
* Use the ID as the label, which will be referenced in the Jenkinsfile.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700490471/bbd924e7-4c82-4e1b-8d6b-c83cb9c3dac5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700551996/6e42fa53-b080-4ecf-8a0b-1eed9c978040.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700694889/c310223d-3c16-4b7f-9464-a8c807cb8695.png align="center")

Here the ID is our Label which we ar going to user in the Jenkins File

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704700845584/27685b35-4d9f-4ab9-81f6-1308880aeff6.png align="center")

Run the Jenkins job again, and if it fails due to missing Docker credentials, configure Docker credentials in the Jenkins global settings.

Once configured, run the job again, and this time, it should be successful.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704701013203/0ddf7f50-a7d2-429a-9ae4-feb7f4c935b3.png align="center")

## **Accessing the Jenkins Agent:**

1. In the browser, navigate to `<agent-public-ip>:8000`.
    
2. Congratulations! You have successfully set up and run a Jenkins job on your agent.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704701140294/c32014ae-4b33-4792-bd17-0ce9eb338335.png align="center")

By following these steps, you've created a scalable and distributed Jenkins environment, enabling efficient CI/CD processes. Adjust the configurations based on your specific requirements for development, testing, and deployment workflows.

## Conclusion

In conclusion, setting up a Jenkins agent on Ubuntu opens doors to a distributed and efficient CI/CD environment. This guide has walked you through the process, from installing Java to configuring Docker and running successful Jenkins jobs. By leveraging agents, you've optimized your workflows, enabling seamless collaboration and scaling your development and deployment processes. Cheers to a well-configured Jenkins setup!