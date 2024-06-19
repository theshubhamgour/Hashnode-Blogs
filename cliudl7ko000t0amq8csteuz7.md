---
title: "Absolute and Relative Paths in Linux: Your Guide to Navigating the File System"
seoTitle: "Absolute and Relative Paths in Linux"
datePublished: Tue Jun 13 2023 14:25:37 GMT+0000 (Coordinated Universal Time)
cuid: cliudl7ko000t0amq8csteuz7
slug: absolute-and-relative-paths-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686668133905/c541e41b-e217-4a60-a202-5b030eb3fd1e.png
tags: linux, aws, devops

---

## Introduction

Paths are like directions that help us navigate through the file system in Linux. Whether you're exploring the terminal, writing scripts, or managing files, understanding absolute and relative paths is key! Let's dive in

## 🌈 Absolute Paths

Think of absolute paths as the full address starting from the root directory, denoted by a forward slash ("/"). They provide a complete route to a specific location in the file system. 🏠✨

For example:

* `/home/user/Documents` represents the Documents folder inside the user's home directory.
    
* `/var/log/syslog` points to the syslog file stored in the log directory.
    
* `/etc/passwd` leads to the password file in the etc directory.
    
* `/usr/bin/python3`: This absolute path leads to the Python3 executable located in the `/usr/bin` directory.
    
* `/etc/apache2/httpd.conf`: Here, we have the Apache configuration file stored in the `/etc/apache2` directory.
    
* `/var/www/html/index.html`: This path points to the `index.html` file inside the `/var/www/html` directory, typically used for web server files.
    

Absolute paths always begin from the root directory, regardless of the current location. They're like GPS coordinates that pinpoint the exact location on the map! 📍🗺️

## 🌟 Relative Paths

Relative paths, on the other hand, are like directions based on the current location. They are defined relative to the directory you're currently in. 🚶‍♀️🗂️

For example:

* If you're currently in the `/home/user` directory, then `Documents` refers to the Documents folder directly within it.
    
* Similarly, if you're in the `/var/log` directory, `syslog` refers to the syslog file in that same directory.
    
* And if you're in the `/etc` directory, `passwd` points to the password file located there.
    
* If you're currently in the `/home/user` directory:
    
    * To access the `Pictures` directory located within it, you can simply use `Pictures`.
        
    * To go up one level and access the parent directory `/home`, you can use `..`.
        
    * To navigate to a file in the `Downloads` directory, you can use `Downloads/file.txt`.
        
* If you're in the `/var/log` directory:
    
    * To access the `auth.log` file in the same directory, you can directly use `auth.log`.
        
    * To go back to the parent directory `/var`, you can use `..`.
        
    * To reach the `syslog` file in the `/var/log` directory, you can use `syslog`.
        
* If you're in the `/etc` directory:
    
    * To access the `hosts` file in the same directory, you can use `hosts`.
        
    * To go up one level and access the parent directory `/`, you can use `..`.
        
    * To navigate to the `cron.d` directory, you can use `cron.d`.
        

Relative paths are convenient when you're already inside a particular directory and want to navigate to another location nearby. They're like giving directions to a nearby landmark! 🏰🗺️

Remember, relative paths don't start with a forward slash. They depend on the current working directory.

## Example:

Let's say you want to make a directory structure like the one below here is the line of command you will be firing on from your terminal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686668262990/2b24c163-0278-4be8-be9d-456f40c383fb.png align="center")

```plaintext
[root@192 Desktop]# mkdir -p /linux/{RHCSA/{rhel7/{usr,partition},rhel8/{vdo,stats},rhel9/{security,LVM}},RHCE/{rhel7,rhel8}}
```

Once the above is done it is time to add the files to the `RHCE` director under the `rhel7` and `rhel8` folder

```plaintext
[root@192 Desktop]# touch /linux/RHCE/rhel8/ansible
[root@192 Desktop]# touch /linux/RHCE/rhel7/config
```

## Conclusion

In conclusion, understanding the difference between absolute and relative paths in Linux is essential for navigating the file system effectively.

Absolute paths provide the complete route from the root directory, regardless of your current location. They start with a forward slash and act as fixed coordinates, pointing directly to a specific location in the file system. Think of them as a GPS system that can take you anywhere, no matter where you are.

On the other hand, relative paths are defined based on your current directory. They don't start with a forward slash and are used to navigate to locations nearby. Relative paths are like giving directions based on landmarks around you, such as going up a level or moving to a directory adjacent to your current one.

By understanding both absolute and relative paths, you can effectively navigate through the file system, access files and directories, and execute commands with ease. So, whether you're a beginner exploring Linux or an experienced user managing files and directories, knowing the difference between absolute and relative paths will undoubtedly make your Linux journey smoother.

Feel free to experiment with different paths, explore your file system, and have fun while mastering the art of navigating in Linux! If you have any further questions, don't hesitate to ask. Happy exploring! 🌟🚀