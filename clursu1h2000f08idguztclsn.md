---
title: "Day #3 : S3 , IAM and AWSCLI"
datePublished: Tue Apr 09 2024 03:05:33 GMT+0000 (Coordinated Universal Time)
cuid: clursu1h2000f08idguztclsn
slug: day-3-s3-iam-and-awscli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712631858335/e800f741-9447-4f1d-a43f-d9d0606d1acd.png
tags: aws, s3, iam, aws-cli

---

## What is S3 Bucket in AWS?

* Amazon Simple Storage Service (Amazon S3) is a scalable object storage service provided by Amazon Web Services (AWS). It is designed to store and retrieve any amount of data from anywhere on the web.
    
* S3 is commonly used for a variety of purposes, such as backup and restore, archiving, content distribution, and hosting static websites.
    

## What is IAM in AWS?

* IAM stands for Identity and Access Management. IAM is a web service that helps you securely control access to AWS resources. It enables you to manage users, groups, and permissions to securely access and use AWS services and resources.
    

#### key components of IAM:

* Users
    
* Groups
    
* Roles
    
* Policies
    
* IAM Documentation
    

## What is AWSCLI?

* The AWS Command Line Interface (AWS CLI) is a set of open-source command-line tools for interacting with Amazon Web Services (AWS) services. It allows users to control and manage AWS services directly from the command line, rather than using the AWS Management Console.
    

### **TASK 1- Make a private S3 bucket in AWS and change the policy so you can access its stuff without making it public.**

**Creating a Private S3 Bucket:**

1. **Access AWS Console:** Log in to AWS and find the S3 service.
    
2. **Bucket Creation:** Click "Create Bucket" and follow the prompts, ensuring the bucket is private.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712630412037/7790446f-d308-4da2-b0cb-f2062729d8c6.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712630462266/736bed7c-7db4-4d00-9bee-f2a1ea2c5c81.png align="center")
    
3. **Policy Adjustment:** Modify the bucket policy to allow your IAM user access while keeping it private.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712630665088/795171e1-b147-40d8-9f69-68c31a588167.png align="center")
    

## **TASK 2- Configure AWSCLI on your Ubuntu machine.**

1. **Install AWS CLI using**`curl` and `unzip`: Open a terminal and run the following commands:
    
    ```bash
       # Install unzip if not already installed
       sudo apt update
       sudo apt install unzip
    
       # Download and install AWS CLI using curl
       curl "https://d1vvhvl2y92vvt.cloudfront.net/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
       unzip awscliv2.zip
       sudo ./aws/install
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712630239033/00b89a2f-b17f-49f6-800e-d23009363e20.png align="center")
    
2. **Configure AWS CLI:** After installing the AWS CLI, you still need to configure it. Run the following command:
    

```bash
 aws configure
```

Enter your AWS access key, secret key, default region, and output format as prompted.

Example:

```bash
   AWS Access Key ID [None]: YOUR_ACCESS_KEY
   AWS Secret Access Key [None]: YOUR_SECRET_KEY
   Default region name [None]: YOUR_REGION
   Default output format [None]: json
```

Replace `YOUR_ACCESS_KEY`, `YOUR_SECRET_KEY`, and `YOUR_REGION` with your actual AWS access key, secret key, and desired region.

Note: Keep your AWS credentials secure.

* **Verify Configuration:** To verify that the configuration is successful, you can run a simple command such as:
    
    ```bash
      aws s3 ls
    ```
    
    If your configuration is correct, it should list your S3 buckets.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712630700794/f0b5643c-e8c6-42f0-ae7f-7de6c7279d15.png align="center")
    

Now you have the AWS CLI installed and configured on your Ubuntu machine using `curl` and `unzip`.

## **TASK 3 : Create EC2 from AWS CLI**

**Create an EC2 instance using AWSCLI.**

```bash
aws ec2 create-key-pair --key-name newclikey
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712630858720/c2ea8a01-5325-4db1-82a3-c9ef5eef9854.png align="center")

**Step3: Create Security group to attach to ec2 instance**

```bash
aws ec2 create-security-group --group-name=mynew-sg --description="My security group"
```

Now, Copy that security group's id

**Step4:Add inbound rule to security group**

```bash
aws ec2 authorize-security-group-ingress --group-id=sg-04a099de5be77b1fb --protocol=tcp --port=443 --cidr=0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-id=sg-04a099de5be77b1fb --protocol=tcp --port=22 --cidr=0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-id=sg-04a099de5be77b1fb --protocol=tcp --port=80 --cidr=0.0.0.0/0
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712630819028/01bc6c0c-a8de-43d9-a2a2-6b50aa087639.png align="center")

**Step5: Create instance**

```bash
aws ec2 run-instances --image-id=ami-0fc5d935ebf8bc3bc --instance-type=t2.micro --region=us-east-1 --key-name=newclikey --security-groups=mynew-sg
```

Now, navigate to your ec2 dashboard\*\*.\*\* you can see the instance(demo-ec2) there.

#### TASK 4 - Setting Up AWS IAM for a New Team Member

`Scenario:` Imagine you're working as an IT administrator at Global Tech Inc., a multinational company with diverse cloud computing needs. The company heavily relies on AWS services for its operations. You have a new colleague, Alex, who recently joined your team. Alex's role involves monitoring the company's computing resources and managing data storage. Your task is to set up Alex's AWS access.

What needs to be done:

* Configure AWS IAM (Identity and Access Management) to provide Alex with specific access rights. Alex should be able to:
    
    * View EC2 Instances: Alex needs to monitor the virtual servers running in the AWS cloud but should not be able to modify them.
        
    * Create S3 Buckets: Alex is responsible for creating new storage spaces for various projects.
        

**Solution:**

**Step1:** \*\*Creating a New IAM User-\*\*For our new member ALEX, create an IAM user-named as "alex".Specify the user details and choose programmatic access for AWS CLI usage.

\*\*Step2: Assigning IAM Policies -\*\*IAM policies define permissions. For Alex's role, we'll create custom policies to grant access to monitor EC2 instances and create S3 bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712631616895/457ea40f-a8a4-4246-bb5c-9d2e6857ed8e.png align="center")

## Conclusion

If you have any questions, need clarifications, or want to discuss anything related to cloud technologies, feel free to reach out to me on LinkedIn. Connect with me at [**Shubham Gour**, and I'll b](https://www.linkedin.com/in/theshubhamgour/)e more than happy to assist you. 😊