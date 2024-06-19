---
title: "Day #5 : AWS VPC"
datePublished: Thu Apr 11 2024 17:28:41 GMT+0000 (Coordinated Universal Time)
cuid: cluvijqqf000g07jof2799tz9
slug: day-5-aws-vpc
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712769163864/f01397fd-9f32-4c94-b002-e258e10d37ce.png
tags: aws, vpc, subnet, igw

---

Amazon Web Services (AWS) offers a robust networking service called Virtual Private Cloud (VPC) that allows users to create a logically isolated section of the AWS Cloud where they can launch resources. VPC Peering is a powerful feature within AWS that enables seamless communication between VPCs, creating a virtual network that spans multiple AWS accounts.

## **Key Concepts:**

### 1\. **Subnets:**

*(Think of subnets like different shelves in your invisible room. Each shelf has its own purpose, and they're arranged in a way that if one gets messy, it doesn't mess up the others.)*

* Think of subnets as smaller segments within your VPC. Each subnet operates in a specific Availability Zone, providing high availability and fault tolerance.
    

### 2\. **Internet Gateway:**

*(The Internet Gateway is like a magical door. It lets your things inside your invisible room connect to the outside world – like a secret door to the internet.)*

* An Internet Gateway allows your VPC resources to connect to the internet. It's like the gateway to the outside world for your virtual network.
    

### 3\. **Security Groups:**

*(Security Groups are like security guards. They decide who or what can come into your invisible room and who or what can go out.)*

* Security Groups act as virtual firewalls for your instances. They control inbound and outbound traffic to and from your resources.
    

### 4\. **Route Tables:**

*(Route Tables are like the signs in your invisible room. They tell the things where to go – whether to stay inside (in your room) or go outside (to the internet).)*

* A Route Table defines the rules for routing network traffic. It determines where the traffic is directed, whether within the VPC or outside to the internet.
    

### 5\. **CIDR Blocks:**

*(CIDR Blocks are just a way to mark your territory. They help define the range of addresses your invisible room can use.)*

* CIDR (Classless Inter-Domain Routing) Blocks are a way to specify IP addresses and routing prefixes. They help define the range of IP addresses for your VPC.
    

## How Does it Benefit You?

### 1\. **Isolation:**

* VPC provides a secure and isolated environment for your resources, separating them from other users' resources on AWS.
    

### 2\. **Customization:**

* You have complete control over your VPC's IP address range, subnets, route tables, and gateways, allowing for a customized network architecture.
    

### 3\. **Security:**

* With Security Groups and Network Access Control Lists (NACLs), you can define and control the traffic to and from your instances.
    

## **Setting Up Your First VPC:**

* **Go to VPC Dashboard:**
    
    * In the AWS Management Console, find the "VPC" service. This is where you can create and manage your Virtual Private Cloud.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712755960577/ad2d8097-848c-456e-9c9d-3673a6150cb2.png align="center")

* Click on "Create VPC" and follow the on-screen instructions. You'll need to specify the IP address range (CIDR block) for your VPC.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712756067738/121b67b2-786b-4f00-ac64-ed395f6fa58a.png align="center")

* Click on 'Create VPC'
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712756130150/adf45c80-7e90-434b-997b-d3cce6196f2c.png align="center")

* Your VPC has been created successfully.
    
* **Configure Subnets:**
    
    * Create subnets within your VPC to organize your resources. Each subnet should be associated with a specific Availability Zone.
        
    * Select the 'Subnets' option under Virtual Private Cloud section located in the left panel.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712756274346/ec073c20-c6db-4825-aeb7-135c97aa50e5.png align="center")
        
        * The above-showing subnets are the default ones which by default present with default VPC.
            
        * Let's create new subnets for our new VPC.
            
        * Click on 'Create Subnet'.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712756542360/08d5faae-eb99-4d0b-990f-0facd47b68a7.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712756667828/80822aac-f378-4865-ae6b-1b4b1f710f4f.png align="center")
            
        * Click on 'Create subnet'.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712756692319/37edc213-0f12-49ff-bb59-234814901aad.png align="center")
            
            * Our both new subnets are ready now.
                
        * **Set Up Internet Connectivity:**
            
            * Create an Internet Gateway and associate it with your VPC to enable internet connectivity for your resources.
                
            * Select 'Internet gateways' option under Virtual Private Cloud section located in the left panel.
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757061889/aad3d143-7dca-486a-b164-4d8aa3eacda9.png align="center")
                
                Click on 'Create internet gateway'.
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757104756/0a699a6e-6a1c-4f0d-9322-70f7c8d10b5f.png align="center")
                
                Your Internet gateway is created now and now it is asking to attach this to VPC
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757124667/d77fab59-dac2-451b-ab98-4e3e5017618a.png align="center")
                
                .Click on Action -&gt; 'Attach to VPC'.
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757166542/9dccfeca-e383-4275-91c5-e015b3c5687e.png align="center")
                
                Select your new VPC and click on 'Attach internet gateway'.
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757206083/20c33401-98c4-4618-b2e0-da260f75f266.png align="center")
                
                **Configure Route tables:**
                
                * After internet gateway setup, we need to configure our route table so that our machines get access to the internet. Without configuring this in route table, our machines will never reach to Internet.
                    
                * Select the 'Route tables' option under Virtual Private Cloud section located in the left panel.
                    
                    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757300808/267eb108-b432-4ab1-871c-b158730dedc8.png align="center")
                    
    * Let's create a new Route table for our custom VPC and not disturb the main route tables of the custom VPC.
        
    * Click on 'Create route table'.
        
        Give a name and select your VPC.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757341237/1d75662e-8ed0-4fd5-b2c9-ae3a3f1bc5b1.png align="center")
        

* Click on 'Edit subnet associations'.
    
* Select the required subnets and click on 'Save associations'.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757395365/6e646ea5-70ff-4211-aa92-d9c02db51ddc.png align="center")

Now our subnet association has been succcessfully done.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757442819/5f9736ad-6ee0-439c-b872-15cad61836af.png align="center")

Now click on 'Routes' option from the menu. -&gt; Click on 'Edit routes'.

Click on 'Add route' and give the destination which is the internet in our case it is generally taken as 0.0.0.0/0 and select the target as Internet gateway, it will show your Internet gateway ID.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757509352/1a49c6e3-bcbf-4c1f-bcbc-a7ad3d4416c2.png align="center")

Our routes are now successfully configured.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757536404/5c01e791-0c90-40b1-abd6-fdf7a17b32c3.png align="center")

**Launch Resources:**

* Now that your VPC is set up, you can start launching resources like EC2 instances or databases within the defined subnets.
    
* Let's launch an EC2 instance and see if we can ping [**google.com**](http://google.com/) or not.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757728574/18334404-0734-4e34-9af4-1d0fc872cf8d.png align="center")

In the above, we have to click on 'Edit' in Network settings and select our custom VPC and custom subnets.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757747627/57857a3d-0254-49d8-92f1-43fca3dd544b.png align="center")

Please note that 'Auto-assign public IP' is set to Disable by default.

So enable it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712757763069/cb936b36-834f-4ed8-ae2c-f7185c0da3f2.png align="center")

I have allowed SSH and ICMP for the v4 address in the Security group. Leave everything as default and click on 'Launch instance'.

Once EC2 instance is launched under a custom VPC network. We can check this in the Details option by selecting that EC2 instance.

Let's connect to this EC2 instance and ping **google.com**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704296244742/a3ffdfa3-f8c1-47fc-80e8-ce43e370df76.png?auto=compress,format&format=webp align="left")

Our EC2 is successfully created in our custom VPC and network traffics are working fine for the custom VPC.

## **Conclusion**

If you have any questions, need clarifications, or want to discuss anything related to cloud technologies, feel free to reach out to me on LinkedIn. Connect with me at [**Shubham Gour,**](https://www.linkedin.com/in/theshubhamgour/) **and I'll b**e more than [](https://www.linkedin.com/in/theshubhamgour/)happy to assist you. 😊