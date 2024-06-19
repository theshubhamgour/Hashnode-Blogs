---
title: "Kubernetes: Master and Node Configuration"
seoTitle: "Mastering Kubernetes: A Step-by-Step Guide to Setup Master and Node"
seoDescription: "Learn to set up master and node instances effortlessly using Ubuntu on AWS t2.medium."
datePublished: Sat Dec 16 2023 23:08:32 GMT+0000 (Coordinated Universal Time)
cuid: clq8o63zw000308lbhpi02dic
slug: kubernetes-master-and-node-configuration
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/eUMEWE-7Ewg/upload/38f6e01fa6d0df482bb96ef0020be176.jpeg
tags: docker, kubernetes, devops

---

## Creating Instances:

To kick things off, let's create two instances – one for the master and one for the node. Use the `t2.medium` instance type and Ubuntu as the base image.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702764528226/09840c2b-0470-4d83-be85-a21640d0a2fe.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702764639904/b7e3a389-c4ca-47df-ba73-ec2b3f35a6a9.png align="center")

## SSH Connection:

Now, let's establish an SSH connection. Whether you prefer using Putty or launching the instance directly, connect to both the master and node using your terminal.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702764976536/66924c40-5903-46b0-ad21-56d02533cdbd.png align="center")

## Kubernetes Setup:

Moving on to the Kubernetes setup, execute the following commands on both the master and node, one after the other:

```plaintext
#Here we are installing the docker engine
sudo apt update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo apt install docker.io -y
```

Adding the GPG keys and enabling Docker

```plaintext
sudo systemctl enable --now docker # enable and start in single command.

# Adding GPG keys.
curl -fsSL "https://packages.cloud.google.com/apt/doc/apt-key.gpg" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg
```

![Master](https://cdn.hashnode.com/res/hashnode/image/upload/v1702765218462/f7fcc8c8-d427-4960-b2e6-941e00b8947b.png align="center")

Just to check whether the command ran properly execute the below

```plaintext
sudo service docker status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702765285283/b3ac8b4a-2284-4ec3-a1a4-c8c1350d868b.png align="center")

Now adding and source list and installing kubeadm

```plaintext
# Add the repository to the sourcelist.
echo 'deb https://packages.cloud.google.com/apt kubernetes-xenial main' | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt update 
sudo apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
```

## Master Node Initialization:

Initialize the Kubernetes master node:

```plaintext
sudo kubeadm init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702765501051/cdc4202e-519b-4f7b-8c87-895aa8fb1447.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702765520189/bc826d27-ad90-4ce8-be56-b97a1caeac94.png align="center")

After successful execution, your Kubernetes control plane will be initialized. Set up local kubeconfig for both the `root` user and a `normal` user:

```plaintext
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702765694201/0d74b199-ba0d-4d13-9fee-8f3d34e74fc5.png align="center")

Apply Weave network for master to communicate with nodes:

```plaintext
kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702765805923/f25ce355-134e-44be-a4e9-f2db36718c05.png align="center")

## Worker Node Configuration:

Run the following commands on the worker node.

Run the following command on node to perform pre-flight checks and reset Kubernetes configurations

```plaintext
sudo kubeadm reset pre-flight checks
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766021443/e4f74e6b-b478-4f85-83c4-44df81490123.png align="center")

To generate the join command token, execute the following on your Kubernetes master node, This will provide you with the command needed for joining other nodes to the cluster. Ensure to run this on the master node and follow the displayed instructions on your worker nodes.

```plaintext
sudo kubeadm token create --print-join-command
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766180755/a59183e3-5eaf-498f-b205-d96d75ed7d7e.png align="center")

Paste the join command you got from the master node and append `--v=5` at the end. *Make sure either you are working as sudo user or use* `sudo` before the command

```plaintext
sudo kubeadm join 172.31.12.239:6443 --token iwuxnk.wbhzjrhqd226a2l4     --discovery-token-ca-cert-hash sha256:16b427ac6a78c173405351e5f7a25e91735265eabb386a7c7e1bdc0f44bef7ad --v=5
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766381961/453ecc25-1ff4-4725-abbb-07ac648328cc.png align="center")

As you may see it is trying to connect but since the port 6443 is not exposed we need to expose the port

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766444555/7b5eee13-c7b6-44a2-9622-b146464b17c8.png align="center")

## Expose Port on AWS:

Now the below operation we are going to perform on AWS on the Master instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766516525/a2d03cd7-4279-4d33-abba-9638019f5e3f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766553245/05b519a5-65db-44e3-994d-0537f1fc806a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766613381/4f20ef45-d79f-40d8-a975-8eac692c4f53.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766702383/4170f3a7-9fd8-4327-b963-e5cdb89e2ea5.png align="center")

Now execute the below on the Master

```plaintext
kubectl get nodes
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766743376/b727a090-0143-4601-be22-cd7d5e3d6938.png align="center")

## Test a demo Pod

If you want to test a demo pod, you can use the following command: Execute on Master

```plaintext
kubectl run hello-world-pod --image=busybox --restart=Never --command -- sh -c "echo 'Hello, World' && sleep 3600"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702766901531/d0ea1f92-b4cb-4cea-8a6c-09594c75fedc.png align="center")

Now goto Node and excute `docker ps` it should resemble the below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702767004889/f2e3c724-873d-43d5-bf23-c698eb65dd0a.png align="center")

This should provide you with the expected results.

## Conclusion:

You've successfully completed the Kubernetes setup journey! With instances for the master and node configured using `t2.medium` and Ubuntu, and SSH connections established, you've set the stage for a powerful Kubernetes cluster.

Consider this just the start of your Kubernetes adventure—may your orchestrations be smooth, your containers happy, and your tech endeavors full of joy!