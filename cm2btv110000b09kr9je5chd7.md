---
title: "Deploying a Kubernetes Cluster on Amazon EKS and Running a Flask App"
datePublished: Wed Oct 16 2024 12:07:39 GMT+0000 (Coordinated Universal Time)
cuid: cm2btv110000b09kr9je5chd7
slug: eksonaws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729080205517/5f6591a3-cfa9-41d6-9de3-aded8195ef0d.png
tags: aws, kubernetes, devops, eks

---

Amazon EKS (Elastic Kubernetes Service) is a fully managed service that allows you to run Kubernetes on AWS without needing to manage your own control plane. In this guide, we'll walk through setting up an EKS cluster, deploying a simple NGINX pod, and finally deploying a Flask application using a two-tier architecture.

## Prerequisites

Before we begin, make sure you have:

1. AWS account with appropriate permissions (AdministratorAccess).
    
2. A new EC2 instance in the **us-west-2** region.
    

### Step 1: Create an Admin User on the EC2 Instance

1. **Launch a new EC2 instance** in **us-west-2**.
    
2. **Create a user with AdministratorAccess** on the instance to manage AWS resources.
    

### Step 2: Install AWS CLI on Your EC2 Instance

AWS CLI is necessary to manage AWS resources from the terminal.

1. Update the system and install `unzip`:
    
    ```plaintext
    sudo apt install unzip
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729056788952/799f1529-680b-47f2-acf0-6a8b162f177b.png align="center")
    
2. Download and install AWS CLI
    

[`https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html`](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729056730482/fb1f8d9a-5de9-4d45-9c35-8d734836f088.png align="center")

```plaintext
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729057309309/f0e79e73-a048-4702-b078-a9ff03ec6058.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729057324970/042d1dcd-8a17-4279-b64e-a42c863657e7.png align="center")

3. **Configure AWS CLI** with your credentials:
    

```plaintext
aws configure
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729057426080/b44cf99d-f9db-4c54-b0fe-4093cbab0a3c.png align="center")

4. **Test the AWS CLI** installation by listing users:
    

```plaintext
aws iam list-users
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729057493531/50fabfb8-3d16-46a1-a583-1b18d52d80d3.png align="center")

### Step 3: Install eksctl

`eksctl` is a simple CLI tool for creating and managing EKS clusters.

[https://eksctl.io/installation/](https://eksctl.io/installation/)

```plaintext
curl -sL "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp && sudo mv /tmp/eksctl /usr/local/bin
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729058003676/bbbc6e9a-c107-4a9e-a68d-d70d6bc36e40.png align="center")

### Step 4: Install kubectl

`kubectl` is a command-line tool used to interact with your Kubernetes cluster.

[https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

1. Download and install kubectl:
    

```plaintext
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729058176426/a10750a7-ff89-46bd-8476-aff476e43159.png align="center")

**Optionally validate** the kubectl binary: `Download the kubectl checksum file:`

```plaintext
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
```

Validate the kubectl binary against the checksum file:

```plaintext
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729058357529/42d89012-4664-4d1b-bc14-8d05cac96f62.png align="center")

Install kubectl

```plaintext
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729058469341/fb03523d-a173-445c-b8bd-ff571e45035f.png align="center")

### Step 5: Create an EKS Cluster

Use `eksctl` to create an EKS cluster with minimal node configuration.

1. Create the EKS cluster:
    

```plaintext
eksctl create cluster --name tws-cluster --region us-west-2 --node-type t2.micro --nodes-min 2 --nodes-max 3
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729058878627/c45e698e-6818-4aa8-89ac-0501677d8767.png align="center")

if you need to check what is going on in the backend check cloudformation

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729058936613/08a72573-5c5b-4322-b5fa-20d9ba3aa2bc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729058978046/714b91da-0679-4c41-8e76-c7fc67ba6c2c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729059021615/7801ee87-0602-4458-ac49-13f4b194fe52.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729059619872/aad5a7ed-1634-4c13-ba25-5d1140dd598d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729059651236/6bf15c2b-b495-4efb-a52e-2d53fe88227f.png align="center")

### **Verify the cluster** using `kubectl`:

```plaintext
kubectl get nodes
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729059669375/b3146b49-8d3c-4bb2-921a-7f3ea5b9a6e4.png align="center")

Check the available namespaces:

```plaintext
kubectl get namespace
kubectl get pods -n kube-system
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729059771872/7febbd89-1741-4736-9c62-e2d7a38d56d6.png align="center")

Update the kubeconfig:

```plaintext
aws eks update-kubeconfig --name tws-cluster --region us-west-2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729060865334/88fe3c6d-6a80-4f3e-8e83-f11e3931a85b.png align="center")

* `aws eks update-kubeconfig`: The AWS CLI command to update your kubeconfig file for EKS.
    
* `--name tws-cluster`: Specifies the name of your EKS cluster, in this case, `tws-cluster`.
    
* `--region us-west-2`: Specifies the AWS region where your EKS cluster is running.
    

### After running this command:

1. Your local `~/.kube/config` file will be updated with information to connect to the EKS cluster.
    
2. You can check the available nodes or resources in your cluster using `kubectl`:
    

### Step 7: Deploy a Flask App

We will now deploy a Flask application using a two-tier architecture with MySQL as the database.

1. Clone the Flask app repository:
    

```plaintext
https://github.com/LondheShubham153/two-tier-flask-app.git
```

create a namespace or apply if from the namespace.yaml file

```plaintext
kubectl apply -f namespace.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729061509759/93dd3dd0-4b7c-4180-a2f3-41005df4e522.png align="center")

Apply the MySQL manifest files:

```plaintext
kubectl apply -f mysql-deployment.yaml -f mysql-pv.yaml -f mysql-pvc.yaml -f mysql-secret.yaml -f mysql-service.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729061675777/adc80a04-f07e-4c7b-96bf-2e07d5d961da.png align="center")

```plaintext
kubectl get all -n two-tier-ns
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729061953233/c901a4c9-fb78-423e-b388-0c2b8fd148ec.png align="center")

Apply the Flask app manifest files:

```plaintext
kubectl apply -f flask-deployment.yaml -f flask-service.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729062704312/7b1e15e4-2b4e-4b99-984e-268e6edd0e35.png align="center")

```plaintext
kubectl get all -n two-tier-ns
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729063641557/0555656b-aa28-4cab-8257-8456457d8dfc.png align="center")

now all the pods are running

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729063721800/fc291adc-3c72-4bca-9894-37683d2874fd.png align="center")

copy the external ip and past on the browser

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729063769549/f318c193-b27f-4f43-a383-672191cc37aa.png align="center")

### Step 8: Clean Up Resources

1. Delete the Flask app and all resources:
    

```plaintext
kubectl delete -f .
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729063898054/60960bf2-f905-419f-99f3-da0a7ae3e3f3.png align="center")

### Finally, delete the EKS cluster:

```plaintext
eksctl delete cluster --name tws-cluster --region us-west-2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729064446168/aa58763e-95db-4e22-a0e0-7c6c61df7184.png align="center")

### Conclusion

You've successfully created and managed an EKS cluster, deployed a two-tier Flask app, and cleaned up your environment. This guide is a great starting point for working with Amazon EKS and understanding the basics of Kubernetes deployment on AWS.

Feel free to ask any questions or share your thoughts in the comments below!