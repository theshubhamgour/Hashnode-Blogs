---
title: "Day #4 : AWS RDS, DynamoDB and AWS lambda"
datePublished: Wed Apr 10 2024 05:20:17 GMT+0000 (Coordinated Universal Time)
cuid: clutd35yd000608jxdt952cx2
slug: day-4-aws-rds-dynamodb-and-aws-lambda
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712720850628/c5332f40-acc9-4b37-afff-94da6f6cc52b.png
tags: ec2, aws, rds, iam

---

## **What is AWS lambda?**

AWS Lambda is a serverless computing service provided by Amazon Web Services (AWS) that allows you to run code without provisioning or managing servers. It automatically scales and executes your code in response to events, handling all the infrastructure management for you.

## **What is AWS RDS?**

AWS RDS is a fully-managed relational database service provided by Amazon Web Services (AWS). But what does that mean exactly? Let's break it down.

### **Relational Database**

A relational database is a type of database that stores and organizes data in a structured way, using tables with rows and columns. This makes it easy to establish relationships between different pieces of information.

### **Fully-Managed**

The term "fully-managed" is key here. With AWS RDS, you don't need to worry about the nitty-gritty details of setting up, maintaining, and securing a database. AWS handles all the heavy lifting for you, allowing you to focus on using the data rather than managing the infrastructure.

## **Why Use AWS RDS?**

Now that we have a basic understanding of what AWS RDS is, let's explore why it's beneficial for both tech and non-tech individuals.

### **1\. Ease of Use**

AWS RDS makes database management accessible to everyone, regardless of technical expertise. Setting up a database instance is as simple as a few clicks in the AWS Management Console.

### **2\. Automatic Backups and Updates**

Imagine never having to worry about backing up your data or updating your database software. AWS RDS takes care of this automatically, ensuring that your data is secure and your database software is up to date.

### **3\. Scalability**

As your business grows, so does your data. AWS RDS allows you to easily scale your database resources to accommodate increased demand without disrupting your operations.

### **4\. Security**

Data security is a top priority, and AWS RDS provides several layers of security, including encryption, network isolation, and regular security patches. Your data is in safe hands.

### **Setting Up AWS RDS, Connecting with EC2, and Performing Database Operations**

In the console, find the "Services" dropdown and select "RDS" under the "Database" section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712720751492/bf77eea4-65f0-4932-aac8-7206c783e8b1.png align="center")

Click the "Create Database" button, and the wizard will guide you through the process. You'll need to choose a database engine, specify settings, and set up security measures.

**Select Database Engine:** MySQL as the Database Engine for RDS.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712720998187/0acfd51a-40be-4557-8811-d09745f75528.png align="center")

**Configure Database Settings:** In the settings options, name your database and configure credentials in the "Credentials settings" option.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712721059863/882b64f8-1a69-4a83-97eb-6e1f78352e28.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712721395851/972de04b-940b-4524-b276-bf545bd25672.png align="center")

In the Instance configuration option, choose your preferred instance class; for this project, we are using the default class.

**Configure Storage:** In the "Storage" section, opt for 20GB of space.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712721472905/19269d14-ad91-4253-aac1-fdfb44474371.png align="center")

**Configure Connectivity:** In the connectivity option, leave all options at default, including the choice not to connect any specific EC2 instance with your DB

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712722997708/f85bf7c1-1f31-41b5-8850-bb8697e44d25.png align="center")

In the "Database authentication" option, choose "Password authentication" and keep all options unchanged.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712723275307/35e3b4c9-d83e-45a7-b58a-967f5041ac24.png align="center")

Click on "Create database".

Database creation is in progress; please allow some time for completion.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712723332412/84e7ffd2-2fbb-4dbb-93b0-a1bf0f5de24b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712723489214/bca49b53-f968-4154-93c7-8f149eff2062.png align="center")

### **Create an EC2 instance to connect to our RDS DB and log in to the EC2 instance.**

Install the mysql-client package.

```bash
sudo apt upgrade
sudo apt install mysql-client -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724291428/eca0265d-b71b-4705-8e35-8462ec9d9c81.png align="center")

```bash
mysql -u root -p 
[enter root when prompted]
```

It means the MySQL client is installed, and no DB instance is running locally on my EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724409234/d1b9cf27-42db-4d66-b731-5a1fec97201d.png align="center")

### **Configuring the EC2 instance with our RDS database.**

Go to the Amazon RDS dashboard and select "Databases."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724595330/6f8bbd14-1c8d-44c1-a29b-56114454e2b2.png align="center")

Our database is in an available state. Click on the database that we created. We will be directed to the following screen:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724615305/6f0a78b4-4a97-408d-984d-5574d425e5f2.png align="center")

Now navigate to **Connected compute resources** and click on Set up EC2 connection

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724689297/b5d7db47-1d09-49cb-8668-0f14c3d6e9bb.png align="center")

On the next page, it shows that a private network has been created between the EC2 instance and the RDS database.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724735470/9d67f618-b807-413e-b41c-ca2e3b4773d1.png align="center")

Review everything and click on "Set up."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724764275/575c2c2a-660b-4646-8581-541b491c15c9.png align="center")

### **Create a Role for accessing RDS from EC2**

Go to IAM dashbaord.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724885809/365e4b1c-5a50-4efd-b703-ee7ce91d6513.png align="center")

Click on "Roles".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724926096/6ae6d488-3757-4919-b070-271837616ada.png align="center")

Click on "Create role"

Select the trusted entity as "AWS service" since we are creating a role for AWS service, and in the use case, we are selecting EC2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712724990064/e624a25b-6e91-438c-981f-7a20b9b001b0.png align="center")

Scroll down and click on "Next".

Select the policies for RDS full access and CloudWatch that you want to associate with EC2

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712725086317/4ef5388b-dfb0-4807-bddb-1d0363d29e97.png align="center")

Give a name to your role and review it

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712725135792/4a7e7955-2146-4420-865c-ae8a9937b345.png align="center")

Click on "Create role"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712725166891/21431580-88f3-4fd1-96ba-9de4037dd34f.png align="center")

Congratulations, our role has been successfully created!

It's time to assign this role to our EC2 instance.

Go to EC2 and select your instance.

Go to Actions -&gt; Security -&gt; Modify IAM role

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712725223137/0300f378-104f-4299-8ff7-21da8cef33ca.png align="center")

Now modify the IAM role for our EC2 instance. Select the IAM role.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712725265059/ed3e0912-2c3e-44cc-889c-bcbd5d157dbf.png align="center")

Click on "Update IAM role".

### Connecting EC2 with RDS

Go to the Amazon RDS dashboard and select "Databases."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712725390844/09cf0012-e91e-4922-a803-ecf10916de75.png align="center")

In the "Connectivity & security" tab, copy the Endpoint value (e.g., [**my-database.ciztdzgq76lk.us-east-2.rds.amazonaws.com**](http://database-1.cbmxgg8spoqd.us-east-2.rds.amazonaws.com)) as this is required to connect to the RDS DB from EC2.

Login to the EC2 instance and run the below command

```bash
mysql -u admin -h database-1.ciztdzgq76lk.us-east-2.rds.amazonaws.com -P 3306 -p
```

In the above command, we are connecting with the MySQL client using the user (-u) 'admin' to the host (-h) with our endpoint value that we copied. The option (-P) is for the port, which is set to 3306, and (-p) is for entering the DB password. Enter your database password when prompted.Hurray!! we successfully connected with our RDS database from our EC2 instance.

Let's list the databases in our RDS database.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702473805081/dbde1751-5c09-4ae7-a05e-5b3e7dfabdaa.png?auto=compress,format&format=webp align="left")

Let's create a database named 'aws,' create a table, and perform some insertions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702473913566/b4be29dd-86c8-478a-bdd3-f3e7f5a8aeb2.png?auto=compress,format&format=webp align="left")

There are no entries present in your database. Let's add some entries.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702473998387/5ec41f1b-cbac-4e5e-ab92-e81b776fa8a9.png?auto=compress,format&format=webp align="left")

And we have performed some insertions in our table in our database.

Let's perform some deletions as well.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702474056428/cfff7c14-723a-4979-95e4-5b265b11b9f3.png?auto=compress,format&format=webp align="left")

Whoa! We have successfully deleted the entries from our table.

We have successfully created an RDS DB, connected it to an EC2 instance, and performed various MySQL operations.

## **Conclusion**

If you have any questions, need clarifications, or want to discuss anything related to cloud technologies, feel free to reach out to me on LinkedIn. Connect with me at [**Shubham Gour,**](https://www.linkedin.com/in/theshubhamgour/) **and I'll b**e more than happy to assist you. 😊