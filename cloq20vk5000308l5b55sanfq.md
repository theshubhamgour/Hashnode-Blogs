---
title: "Docker Installation issue"
datePublished: Wed Nov 08 2023 17:49:02 GMT+0000 (Coordinated Universal Time)
cuid: cloq20vk5000308l5b55sanfq
slug: docker-installation-issue

---

To resolve this issue, you can follow these steps to install Docker on Ubuntu:

1. Update the package lists to make sure you have the latest information about available packages:
    

```plaintext
sudo apt update
```

1. Install the necessary dependencies:
    

```plaintext
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

1. Add the Docker GPG key to ensure the packages are signed:
    

```plaintext
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

1. Add the Docker repository to your system:
    

For x86\_64/amd64 systems:

```plaintext
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

For ARM64/aarch64 systems (e.g., Raspberry Pi):

```plaintext
echo "deb [arch=arm64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

1. Update the package lists again to include the Docker repository:
    

```plaintext
sudo apt update
```

1. Now you should be able to install Docker and its components:
    

```plaintext
sudo apt install docker-ce docker-ce-cli containerd.io
```

If you follow these steps, you should be able to install Docker on your Ubuntu system without encountering the errors you mentioned. Make sure to run the commands with sudo or as the root user.