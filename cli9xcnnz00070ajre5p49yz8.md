---
title: "Vagrant Installation Guide: Setting Up a Virtual Development Environment Made Easy"
seoTitle: "Vagrant Installation Guide"
seoDescription: "Vagrant Installation Guide: Setting Up a Virtual Development Environment Made Easy"
datePublished: Tue May 30 2023 06:55:41 GMT+0000 (Coordinated Universal Time)
cuid: cli9xcnnz00070ajre5p49yz8
slug: vagrant-installation-guide
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/NLSXFjl_nhc/upload/319658e04a38d1a5c29786239f4cdbf1.jpeg
tags: ubuntu, vagrant, linux

---

Hey there! Today, we're going on an exciting journey into the world of Linux. Specifically, we'll explore how you can set up Linux on your Windows machine using Vagrant. So, if you've been curious about Linux and why it's worth learning, you're in for a treat. Let's dive right in!

## What is Linux?

First things first, what exactly is Linux? Well, Linux is an open-source operating system that has gained immense popularity in the tech world. It's known for its stability, security, and flexibility, making it a go-to choice for servers, embedded systems, and even personal computers. Linux comes in various distributions, or "distros," such as Ubuntu, Fedora, and CentOS, each with its own unique features and user interfaces.

Now, let's talk about setting up Linux on your Windows machine using Vagrant. Vagrant is a powerful tool that allows you to create and manage virtual machines effortlessly. With Vagrant, you can spin up a Linux environment with just a few commands, enabling you to experiment, learn, and develop on Linux without altering your Windows setup.

The process is straightforward. You'll need to install Vagrant on your Windows machine, select a Linux distribution and version, and then let Vagrant handle the rest. It will download the necessary files, configure the virtual machine, and provide you with a ready-to-use Linux environment. It's like having the best of both worlds!

But why stop at learning Linux? Let's talk about the real-world applications of Linux. Linux is everywhere, powering some of the most critical systems we rely on daily. It's the backbone of web servers, databases, cloud infrastructure, and even smartphones (through Android). By understanding Linux, you'll gain insights into these technologies and enhance your ability to work with them effectively.

So, whether you're a developer, system administrator, or an aspiring tech enthusiast, learning Linux is a smart move. It opens doors to new career opportunities, provides a stable and secure computing environment, and empowers you with command-line prowess.

In conclusion, Linux is a versatile operating system that's worth exploring. Setting up Linux on your Windows machine using Vagrant is a fantastic way to dip your toes into the Linux world. The skills you gain will be valuable in various industries and can take your career to new heights. So, why wait? Start your Linux journey today and unlock the limitless possibilities that await!

## Installation Using Vagrant

In Order to Use Vagrant in your Windows follow along with us and we will be good to go, Visit the below link and download the vagrant file depending upon your system type

Download Vagrant : [Install | Vagrant | HashiCorp Developer](https://developer.hashicorp.com/vagrant/downloads)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685338583795/20c4cced-63dd-443a-825d-21b61cb6bda7.png align="center")

One the Installation of Vagrant is done you can visit the below link and download the Oracle Virtual Box

Download Virtual box: [Downloads – Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685338785736/da7a6b6b-0edc-4399-971b-132f401e1b5c.png align="center")

While installation of the Virtualbox if you're getting the below error then don't worry it is simply asking you to install the Microsoft Visual C++ 2019 edition into your system

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685338930291/cfe81b71-d0b8-4b7d-bd0c-88c93014dda5.png align="center")

Visit here: [Latest supported Visual C++ Redistributable downloads | Microsoft Learn](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685339150301/d114cc93-c865-4f9a-a90b-c7ce063f46c9.png align="center")

Once the installation is successfully done it will ask you for a restart and this should solve the issue and you will be good to go:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685339290107/a97fbff4-36bf-49b7-b522-ce88b3bd77a6.png align="center")

Once all the above is done this is the time to download Git into your system and this is the final step of installation, Visit the below link to download the same

Download Git : [Git - Downloads (](https://git-scm.com/downloads)[git-scm.com](http://git-scm.com)[)](https://git-scm.com/downloads)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685339378394/e7733678-13b4-452a-b2c5-d28659e2b789.png align="center")

Now we need to set up the path where we are going to work, to check where we are supposed to work use the below command and this will display all the drives in your system

```plaintext
fsutil fsinfo drives
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685339496011/97dda55f-ceaa-4b48-bd89-950b92fcac9c.png align="center")

Now to select the Drive where you want to work let's say you want to select C Drive in order to do the same just type `C:` and it will switch to C Drive. Now it's time to create a directory for vagrant and here we will place all the operational file which we are going to use for booting purposes

```plaintext
mkdir vagrantvms
```

Now create the directory for the OS image it is Ubuntu in our case

```plaintext
mkdir ubuntu
cd ubuntu
```

Now it's time to initialize the file, Goto the vagrant cloud and search for the image

copy the image name as highlighted in the below image: [Vagrant box ubuntu/trusty64 - Vagrant Cloud (](https://app.vagrantup.com/ubuntu/boxes/trusty64)[vagrantup.com](http://vagrantup.com)[)](https://app.vagrantup.com/ubuntu/boxes/trusty64)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685340997624/11a14967-fce2-4ec9-bfed-30ad5896a45c.png align="center")

Open git bash and type the following command

```plaintext
vagrant init ubuntu/trusty64
```

now it's time to pull the vagrant image for the vagrant cloud

```plaintext
vargant pull ubuntu/trusty64
```

Now it's time to launch the image file

```plaintext
vagrant up
```

upon execution, you can notice the changes in the virtual box in the Ubuntu image

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685341373177/74537956-9986-4f41-a590-dca55e4cacf0.png align="center")

If by any chance you're not able to boot your ubuntu image there is a cent possibility that your VagrantFile is not configured open the vagrant file and check whether it matches the below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685429335460/dc126b3f-f25a-4a3f-be45-8e555e1f7f6a.png align="center")

Once all the things are set you will get the below once you fire up the above command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685341080064/9f1627fd-e66f-42c7-8682-800bb58dd5d4.png align="center")

Woohoo! You did it! You've successfully set up your very own Linux environment using Vagrant on your Windows machine. Now, let's take a closer look at what's happening after you've logged in via SSH. Prepare for the grand tour!

Welcome to Ubuntu 14.04.6 LTS! 🎉 This LTS (Long-Term Support) version of Ubuntu is all about stability and reliability. It's like having a trusty companion by your side for your Linux adventures. The specific kernel version you're working with is GNU/Linux 3.13.0-170-generic, specially crafted for x86\_64 architecture.

Now, let's take a closer look at the system information that's being displayed:

* System load: The system load reflects how much work your system is currently handling. Right now, it's at a pretty relaxed 0.29, which means your system isn't breaking a sweat.
    
* Processes: There are currently 83 processes happily running behind the scenes, doing their thing.
    
* Usage of /: The system is using a mere 3.6% of the total 39.34GB available on the root filesystem. You've got plenty of room to stretch your legs and save your files!
    
* Users logged in: You'll notice that there are currently no users logged into the system. You've got this whole Linux playground all to yourself!
    
* Memory usage: Your system is utilizing 24% of its available memory, which means you have a good amount of free memory for all your exciting projects.
    
* IP address for eth0: Your primary network interface has been assigned the IP address 10.0.2.15. It's like your Linux machine has its own little corner of the network to call home.
    
* Swap usage: The swap space, which acts as an extension to physical memory, is currently not being used. Your system is feeling pretty confident with its memory management!
    

## Final Note

Please note the next time you want to boot up the Ubuntu image file - Just follow the below steps: Open Git and type the following in the Bash terminal

* `vagrant up` - to start the image file
    
* `vagrant ssh` - to make a ssh connection with the VirtualBox image file
    
* `vagrant halt` - to suspend the session which is currently running
    

Now that you've got your Linux environment up and running, it's time to dive in, explore, and let your creativity soar. Linux offers a wide range of possibilities, and there's always something new to discover. Remember, the Linux community and documentation are there to lend a helping hand whenever you need it.

Happy Linux-ing, everyone!