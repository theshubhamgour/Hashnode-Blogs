---
title: "Day #2: AWS WAF  (Web Application Firewall)"
datePublished: Mon Apr 08 2024 08:09:25 GMT+0000 (Coordinated Universal Time)
cuid: cluqo8ymm000009jw0k9thunt
slug: day-2-aws-waf-web-application-firewall
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712563729610/cd642d2a-0b61-4c29-98e7-f721ea1dc403.png
tags: ec2, aws, load-balancer, ami, waf

---

AWS WAF (Web Application Firewall) is a service that protects web applications from malicious attacks by filtering and monitoring incoming traffic based on defined rules. It safeguards against common web vulnerabilities such as SQL injection, cross-site scripting, and more.

### Create AMI Template:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712562066864/90ffa504-3207-42f2-958e-96ab4b6e278c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712562186800/7f870641-b85a-44d5-bddc-73fa1a946b8e.png align="center")

Now Launch instance from the template:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712562264859/b8927c98-d60e-43f3-9bbe-742a7e2aaa8b.png align="center")

If you have a web application hosted on AWS, you can use AWS WAF to set rules that block requests from specific IP addresses or patterns commonly associated with attacks.

### Implementing AWS WAF for Web Application Protection

1. Navigate to the EC2 Dashboard and locate the "Launch Templates" section.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712551280981/abf4a0d6-5ef0-4d70-b2e1-2e49a5f13c7e.png align="center")
    
2. Click "Create Launch Template" and configure settings like AMI, instance type, and storage.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712551392960/00700de2-cf6d-493b-8cb0-34772a7be659.png align="center")
    
3. In the "Advanced Details" section, paste the provided script.
    

```bash
#!/bin/bash
sudo apt update -y
sudo apt install nginx -y
sudo echo "Hello this is a template server with ip address : $(hostname -i)" > /var/www/html/index.html 
sudo systemctl restart nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712562623714/d3e84e1b-b007-4177-a70b-aafef2067311.png align="center")

* Save the template.
    
    # **Create Load Balancer**
    
    * In the EC2 Dashboard, navigate to "Load Balancers" and click "Create Load Balancer."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712551555860/471246bd-b092-4100-a2bb-29769ba55622.png align="center")
        
    * Choose "Application Load Balancer" and configure the settings, including listener configurations.
        
        * Follow the below Steps:
            
        * configure the setting and create the auto scaling group.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712551638811/c62aaa57-68a9-4cdf-85bb-3a84c8d9ecd8.png align="center")
            
            select the VPC you want
            
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712552082686/902ff13b-7f5f-45d2-8b80-46b0ea77c1c7.png align="center")
        
* Configure scaling policies, desired capacity, and other parameters.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712552664517/28b2e03b-0be9-4efa-bc1b-b2dc9a6beae9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712559650408/2fa2bfe6-942f-4b50-bd76-6941bff037dd.png align="center")

### **Securing Your Infrastructure with WAF:**

##### **Step 4 - Configuring WAF WebACL:**

1. In the AWS WAF console, go to WebACLs and click "Create WebACL."
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712563433542/9ad3ca3b-ddde-44fa-bd83-bb7cf16457c8.png align="center")
    
3. Now Click on Add AWS resources and select the load balancer we created earlier
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712563532098/2775123f-ffad-495c-a50b-a13fc2481658.png align="center")
    
5. Define conditions for your WebACL, specifying rules to allow or block requests.
    
6. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1712563603760/bd31199d-a725-4e3d-9df9-97a896aa9fe9.png align="center")
    
7. Associate the WebACL with your Application Load Balancer.
    

By configuring a WAF WebACL, you add an additional layer of protection to your applications, safeguarding them against various cyber threats.

## Conclusion

If you have any questions, need clarifications, or want to discuss anything related to cloud technologies, feel free to reach out to me on LinkedIn. Connect with me at [**Shubham Gour**, and I'll b](https://www.linkedin.com/in/theshubhamgour/)e more than happy to assist you. 😊