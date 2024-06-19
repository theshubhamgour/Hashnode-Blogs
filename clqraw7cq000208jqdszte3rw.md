---
title: "Day #22 : Getting Started with Jenkins 😃"
datePublished: Sat Dec 30 2023 00:04:32 GMT+0000 (Coordinated Universal Time)
cuid: clqraw7cq000208jqdszte3rw
slug: day-22-getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703894425323/778469ff-0da8-4589-a3d4-299164f52530.png
tags: devops, jenkins, pipeline

---

## **What is Jenkins?**

Jenkins, a Java-based open-source automation platform equipped with plugins, is tailored for continuous integration and continuous delivery. Its purpose is to facilitate the seamless creation and testing of software projects, simplifying the integration of changes for developers and DevOps engineers.

`Plugins` are the primary means of enhancing the functionality of a Jenkins environment to suit organization or user-specific needs.

`Jenkins` uses `master-slave` architecture. `Jenkins Master` will distribute its workloads to the slave and `Jenkins Slaves` work on the basis of requests received from the Jenkins Master.

### **What is Pipeline in Jenkins?**

A `pipeline` is a concept that introduces a series of events or tasks that are connected in a sequence to make quick software releases.

For example, there is a task, that task has got five different stages, and each stage has got several steps. All the steps in phase one must be completed, to mark the latter stage to be complete.

The `Pipeline` is responsible for building codes, running tests, and deploying new software versions. The `Pipeline` executes the job in a defined manner by first coding it and then structuring it inside several blocks that may include several steps or tasks.

### **  
What is CI/CD in Jenkins?**

The term “CI/CD” refers to the Continuous Integration/Continuous Delivery.

`Continuous Integration (CI)`**:** is a practice that integrates code changes from multiple developers into a shared repository. It can automatically trigger builds and tests whenever changes are pushed to the repository, enabling quick feedback on code quality and preventing integration issues. It only doesn't eliminate bugs but also helps in finding and removing them quickly.

`Continuous Delivery (CD)`**:** is the phase where the changes are made in the code before deploying. Jenkins enables the continuous delivery of software by automating the deployment process. It can deploy applications to various environments, such as development, staging, and production, based on predefined configurations. This helps ensure consistent and reliable deployments.

However, you will see in most of the places "CD" is also refer to as `Continuous Deployment`. So, `Continuous Deployment` automates the release process, deploying changes to production automatically once tests pass, While `Continuous Delivery` focuses on ensuring software is always release-ready with manual approval.

### **Different Types of Jenkins Projects:**

1. `Freestyle Project`**:** This is the most basic project type in Jenkins. It provides a lot of flexibility and allows users to define build steps and configurations based on their specific requirements. It is suitable for simple or custom-build processes.
    
2. `Pipeline Project`**:** Jenkins Pipeline is a powerful and extensible way to define the build, test, and deployment workflows as code. It uses a domain-specific language (DSL) or a declarative syntax to define the entire build pipeline, including stages, steps, and conditions. Pipeline projects are highly versatile and recommended for complex build processes and CD workflows.
    
3. `Multibranch Pipeline`**:** This type of project is useful when you have multiple branches in your source code repository, and you want to build and test each branch separately. Jenkins automatically detects new branches and creates build pipelines for them, providing visibility into the status of different branches.
    

### **Installation of Jenkins**

Step 1: Update Packages: Run the following command to update the package lists for upgrades and new installations:

```abap
sudo apt-get update
```

Step 2: So, before installing Jenkins, firstly we have to install Java on our machine.

Below is the command to install Java: -

```abap
sudo apt install openjdk-11-jre
```

Step 3: Check whether the java is installed or not.

```abap
java --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703892837775/8664893f-acce-4e75-b932-bfecc136a48d.png align="center")

Step 4: Now, moving ahead with the installation of Jenkins, below is the command to install Jenkins on your machine. Add the Jenkins repository key to the system using the following commands: [Link to the documentation](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu)

```abap
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703892955592/7535c2b4-0c19-42ed-a047-b854ab149c17.png align="center")

Step 7: Start Jenkins: The Jenkins service should start automatically after installation. If it's not running, start it with the following command:

```abap
 sudo systemctl start jenkins
```

Step 8: Check whether Jenkins is active or not

```abap
systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893043301/8683ef0c-4fb9-441e-99cd-e5ec27775980.png align="center")

Step 9: `Jenkins` runs on port `8080`. So, go to your instance and add this port to the security group.

Step 10: Go to the Security Group:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893203522/9031997a-fcc9-4411-9b1c-61b882119e44.png align="center")

* Click on "Edit Inbound Rules":
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893236407/aef5a348-69f4-4036-ae1d-309326c017dd.png align="center")
    
* Now add a rule and save it.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893319196/96e335da-a102-4fbd-9a48-5d3cbad8c7b5.png align="center")
    

Step 11: After adding the port in `inbound rule` , Access Jenkins Web Interface: Open a web browser and enter the public IP address or DNS name of your EC2 instance followed by the Jenkins port (e.g. http://&lt;your\_public\_ip&gt;:8080). You should see the Jenkins setup wizard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893401364/6dc029d2-5806-4d72-a48d-3405d4156141.png align="center")

You can find the Admin password on the location given in the above snapshot.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893443770/abb278ad-49bc-4c7f-b3af-5be17484ca14.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893457500/45d98ed1-85dd-4ea4-87c6-bb8e3100f9dd.png align="center")

### **Setting up Jenkins**

After entering your password, you can now customize your Jenkins.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893484324/588f51d8-3179-40e3-a1b4-650b927cff61.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893506365/1dd4df07-51db-4971-92a8-73ba84bbf6ef.png align="center")

After installing the plugins, it will ask you to create the first admin user. Fill in the details.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893681306/0e666679-1523-42c2-875d-e00f0314b737.png align="center")

Your Jenkins is now readyyyyy!!!✨

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893709652/1db66770-8958-4717-af56-85a275cc4105.png align="center")

After your Jenkins is ready, You will find the below Jenkins Dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893734688/b907127c-95fb-439c-a92e-b48e5db6798a.png align="center")

### **Freestyle Project Example**

We will create a simple freestyle project pipeline.  
Step 1: Click on "New Item"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893769419/5b270342-047a-4042-aea7-ab7f079d5fb2.png align="center")

Step 2: Enter an item name and choose Freestyle mode and Click on "OK".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893851283/dbe08378-1f2c-4d70-b652-3c027e5a7150.png align="center")

Step 3: Configure your pipeline as in this case we are simply executing the shell command. So, we will directly go to "Build Steps" and leave the remaining as it is.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893928916/58c3f57b-c124-4c30-9578-7ce19a5da382.png align="center")

So, we have added a simple shell command i.e., echo "Hello World!!" in build steps and save the configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703893964465/f713e326-2ee5-4d1d-89c6-0ea1af788413.png align="center")

Step 4: Click on "Build Now".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703894005601/8564bbda-89dd-4cc5-974a-065e0dc66ae3.png align="center")

Step 5: After you click on "Build Now", you can see in Build History one pipeline gets triggered.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703894054206/db647cf9-52ef-45dd-a4b4-782e4c61e2cc.png align="center")

Step 6: You can find the output or logs of the pipeline in "Console Output". As you can see the command has been successfully executed. So, the pipeline has "Green Tick"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703894085694/8f8877f3-203a-45c7-8c5a-23b3486f2a03.png align="center")

So, this was the simple freestyle project pipeline.

### **Conclusion**

In conclusion, our journey through Jenkins has provided a comprehensive understanding of its significance in automating CI/CD workflows. By unraveling its Java-based architecture, we've seen how Jenkins simplifies tasks for developers, enabling seamless integration of changes in software projects.

The creation of a freestyle pipeline, exemplified by the "Hello World!!" demonstration, underscores the practical application of Jenkins for automation. As we embrace the efficiencies gained through this tool, we recognize Jenkins as an essential asset for modern software development, laying the groundwork for more intricate automation tasks and streamlined workflows in the future.