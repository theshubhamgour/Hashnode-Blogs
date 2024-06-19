---
title: "Ansible Installation for Managing Instances"
datePublished: Sun Dec 24 2023 18:08:11 GMT+0000 (Coordinated Universal Time)
cuid: clqjsyots000308l07ro38jbg
slug: ansible-installation-for-managing-instances
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/g29arbbvPjo/upload/ccdda307dafbb4894dfe5f86c9900ef1.jpeg
tags: ansible, devops

---

## What is Ansible?

**Ansible** is an open-source automation tool that simplifies various IT tasks such as configuration management, application deployment, task automation, and orchestration. It is designed to be simple, lightweight, and easy to use, making it a popular choice for automating repetitive and complex tasks in IT environments.

Key features of Ansible include:

* **Agentless:** No need to install software on managed hosts
    
* **Declarative:** Describe the desired state, not the steps to reach it
    
* **YAML Syntax:** Human-readable and easy to write
    
* **Idempotent:** Repeated executions yield the same result
    
* **SSH-Based:** Uses secure SSH for communication
    
* **Inventory Management:** Organize and define managed hosts
    
* **Modules:** Pre-built tasks for various operations
    
* **Playbooks:** Define orchestration using YAML files
    
* **Extensibility:** Supports plugins and custom modules
    
* **Integration:** Works well with various technologies
    
* **Parallel Execution:** Executes tasks in parallel for efficiency
    
* **Task Retry:** Can retry failed tasks for robustness
    
* **Conditional Execution:** Execute tasks based on conditions
    
* **Variable Support:** Use variables for flexibility
    
* **Roles:** Organize tasks into reusable units
    
* **Handlers:** Triggered only if tasks in a play change state
    
* **Templates:** Use Jinja2 templates for dynamic content
    
* **Vault:** Securely store sensitive data
    
* **Community Support:** Large and active community
    
* **Documentation:** Comprehensive and well-maintained docs
    

### **Step 1: Create Instances on AWS**

Begin by creating four instances of type `t2.micro` with Ubuntu as the image type. This can be done through the AWS Management Console or using the AWS CLI. Once your instances are up and running, make sure to download the private key generated during the instance creation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703433322621/2e6cdedb-72c6-47be-8ccb-bbcf3d00b9cf.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703433398915/9693fcff-e26b-4950-9a77-94253dd83311.png align="center")

### **Step 2: Installation of Ansible**

SSH into your master instance and install Ansible by following these commands:

```plaintext
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible
```

Press Enter when prompted during the installation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703433532905/af3d947f-0c9d-4e09-bfad-5b6d59085ef9.png align="center")

To verify the installation, execute:

```plaintext
ansible --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703433694372/1bb50fc4-0532-4aae-802e-5dabe3eec296.png align="center")

### **Step 3: Add Private Keys to Ansible-Master**

Create a folder for the private key on your local machine and transfer the downloaded private key to the Ansible-master instance.

```plaintext
mkdir keys
cd keys
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703434109257/1db45bd8-3566-405c-969a-b09e9b77d05d.png align="center")

Now from your local - copy the private key ans transfer it to the ansible-master instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703434538011/8e20ddff-dc6a-43e8-9efe-ff92c3480258.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703434677601/60a66b53-0e7f-42a7-9e6f-0d46ab225bd1.png align="center")

### **Step 4: Configure Ansible-Master**

Run the below on ansible master instance this will list the available host connected to master as of now there is no host connected so you should resemble the below

```plaintext
ansible-inventory --list
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703434758928/8cd65b19-666f-4c0a-b40b-cb666a746917.png align="center")

Run the following commands on the Ansible-master instance to configure it:

```plaintext
sudo vim /etc/ansible/hosts
```

Add the following lines to the hosts file:

```plaintext
# Ex 2: A collection of hosts belonging to the 'webservers' group:
#Replace the IP with public IP from instance

[servers]
host_1 ansible_host=3.15.228.122
host_2 ansible_host=3.145.56.89
host_3 ansible_host=3.141.192.200

[all:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/keys/ansible.pem
```

Verify the configuration:

```plaintext
ansible-inventory --list
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703435827107/915c5e7a-146e-4763-bba9-b80616c7e5cc.png align="center")

### **Step 5: Ping All Servers**

Attempt to ping all servers at once with the following command:

```plaintext
ansible -m ping servers
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703436587303/7a792067-3071-43cd-8240-5a0badb31712.png align="center")

If you encounter issues, adjust the key permissions:

```plaintext
chmod 400 ansible.pem
```

Now execute the ping command

```plaintext
ansible -m ping servers
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703436737878/a6db2b74-d987-4c12-9ec2-fc28b8ab4ba7.png align="center")

### **Step 6: Update Hosts**

Keep your hosts updated with:

```plaintext
ansible -a "sudo apt update" servers
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703436938796/99c6d7da-fc4a-4468-a14c-fc0796741de9.png align="center")

### **Step 7: Creating a Playbook**

Create a playbook named `date_play.yml` with the following content:

```plaintext
-
  name: Date Playbook
  hosts: servers
  tasks:
    - name: Show Date
      command: date
    - name: Show Uptime
      command: uptime
```

Execute the playbook:

```plaintext
ansible-playbook date_play.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703439650288/fd36efc2-a900-4153-88b6-d0940df27bca.png align="center")

To see the output while execution execute the below

```plaintext
ansible-playbook date_play.yml --verbose
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703439912300/26259b84-bcdc-48cb-ac43-a059cd615a79.png align="center")

### **Step 8: NGINX Playbook**

Create a playbook named `nginx_play.yml` to install NGINX. Execute the playbook:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703440307794/9d845c4d-39bd-4461-9cba-3cced8713540.png align="center")

```plaintext
ansible-playbook nginx_play.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703440398669/6f09ff44-d6dc-4db9-8529-3382c7e709c8.png align="center")

Visit the public IP of any host to confirm NGINX is running.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703440470513/a127d0b7-7310-49bb-8e9c-e0fa21ce1baa.png align="center")

Congratulations! You've successfully set up Ansible to manage instances and created playbooks for basic tasks and NGINX installation. This marks the beginning of your journey into the world of automation and infrastructure as code. Happy automating!