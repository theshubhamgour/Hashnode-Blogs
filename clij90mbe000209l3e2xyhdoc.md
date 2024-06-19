---
title: "Touch Command - Time Travelling machine in Linux"
seoTitle: "Touch Command - Time Travelling machine in Linux"
datePublished: Mon Jun 05 2023 19:32:10 GMT+0000 (Coordinated Universal Time)
cuid: clij90mbe000209l3e2xyhdoc
slug: touch-command-time-travelling-machine-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/aQYgUYwnCsM/upload/b303e4742b1c10564d94f431fcf130f9.jpeg
tags: linux, aws, developer, devops

---

Hey there! we are going to learn about a very handy command called "touch" and how it can help you create files effortlessly. If you're new to the world of command-line interfaces or just looking to expand your knowledge, this blog post is for you! So, grab your favorite beverage, sit back, and let's dive in!

Imagine you're working on a project and need to create a new file. Instead of fumbling around with your mouse and navigating through menus, the "touch" command swoops in to save the day. It's like having a magic wand for file creation, and it works like a charm.

Alright, let's get our hands dirty and explore how to use the "touch" command with some delightful examples. Don't worry, it's a breeze to use!

## File Creation using touch - Type \[1\]

First, fire up your terminal or command prompt, and let's get ready to type. To create a file with "touch," simply type the following:

```plaintext
[root@192 Desktop]# touch myfile.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685989268527/a0adfa4b-c146-4252-9ff7-1fa72156cb09.png align="center")

Here, "myfile.txt" is the name of the file you want to create. Feel free to change it to whatever name you desire. Once you hit enter, voila! Your new file magically appears in the current directory. It's like digital sorcery!

## File Creation using touch - Type \[2\]

The "touch" command is not just limited to creating one file at a time. You can create multiple files in a single go. Isn't that fantastic? Here's an example:

```plaintext
[root@192 Desktop]# touch file1 file2 file3 file4
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685989334733/0154c3de-6301-45bd-9e32-9ad950ece578.png align="center")

In this case, we created four files: "file1 file2 file3 file4". They'll all pop up in the current directory without breaking a sweat.

## File Creation using touch - Type \[3\]

Have you ever wished you could create multiple files with similar names but different numbers? Well, with the "touch" command and a touch of creativity, you can make it happen in no time.

```plaintext
touch abc{1..5}.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685990984304/e31d8e8e-6a6a-451a-b29f-1ae86be03d22.png align="center")

By executing this single command, you've created five files named "abc1.txt," "abc2.txt," "abc3.txt," "abc4.txt," and "abc5.txt."

Let's break it down to understand what's happening:

* We start with "abc" as the base name for our files.
    
* Then we use the curly braces {} to indicate that we want to perform brace expansion.
    
* Inside the curly braces, we specify the range we desire: 1..5. This means we want to include the numbers from 1 to 5.
    
* Finally, we add ".txt" to the end to give our files the desired extension.
    

The "touch" command, with the help of brace expansion, does all the heavy lifting for us. It expands the range and creates the files in a snap

This technique comes in handy whenever you need to create multiple files with similar names and incremental numbers. It saves you time, keystrokes, and headaches! 🕒

## Question: Create files in multiple directories

Let's say we have three directories: /tmp, /home/shubham, and /usr/games. And we want to create a file in each of these directories. Are you ready? Here we go! 💪

```plaintext
[root@192 Desktop]# touch /tmp/file1 /home/shubham/file2 /usr/games/file3
```

In this command, we're using "touch" to create files in three different directories. Let's break it down:

* /tmp/file1: 📂 The "/tmp" directory is like a temporary playground where files can have fun before they're removed. We're creating a file called "file1" in this directory. Keep your eyes open for treasures in /tmp! ❄️
    
* /home/shubham/file2: 🏡 Ah, the cozy "/home/shubham" directory! It's like your own personal space where you can create files that are dear to you. Here, we're creating a file called "file2." Explore and uncover the secrets of /home/shubham! 🏠
    
* /usr/games/file3: 🎮 The "/usr/games" directory is where exciting games and adventures await! With "file3," we're creating a file that might contain the key to a hidden level or a secret achievement. Ready to level up in /usr/games? 🌟
    

And just like that, with a single command, you've created files in multiple directories, spreading your digital treasures far and wide.

## Change timestamp using touch

You might be thinking, "Okay, touch creates files, but what if I want to update the timestamp of an existing file?" Great question! The "touch" command can handle that too. If you "touch" an existing file, it will update the timestamp to the current date and time, as if you've just touched it. Clever, right?

Here's an example to demonstrate:

```plaintext
[root@192 Desktop]# touch file1
```

By executing this command, the "existingfile.txt" file will have its timestamp updated to the current moment. Handy when you want to keep things fresh!

How to check the timestamp just fire-up the below command

```plaintext
[root@192 Desktop]# stat file1
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685989552645/44320351-05f2-4d6a-93a1-367720188d18.png align="center")

Let's break it down step by step:

* **File**: This line displays the name of the file you're inspecting. In our case, it's simply "file1."
    
* **Size and Blocks**: Here, we learn that the file has a size of 0 bytes and occupies 0 blocks. It's an empty file, ready for your content!
    
* **IO Block**: This line informs us about the input/output block size, which is 4096 bytes in this case.
    
* **Device and Inode**: These details provide information about the device and the unique identifier (inode) associated with the file.
    
* **Links**: The number of links shows how many references point to this file. In our case, it's 1 link.
    
* **Access, Modify, Change, and Birth**: These timestamps represent different aspects of the file's life cycle. "Access" refers to the last time the file was accessed, "Modify" indicates the last modification time, "Change" reflects the last time the file's metadata was changed, and "Birth" marks the file's creation time. All these timestamps are provided in a detailed format.
    
* **Permissions, Uid, and Gid**: Finally, we have information about the file's permissions, user identifier (uid), and group identifier (gid). This tells us who can read, write, or execute the file.
    

By using the "stat" command, we can gain a deeper understanding of our files and their characteristics. It's like peering into their digital souls! 😄🔍

So, the next time you're curious about a file's properties, remember to call upon the "stat" command for an enlightening experience. Discovering the hidden details of your files has never'

## Touch Timestamp - Change Acess and Modify Date time

Imagine you're working on a project, and you need a file that appears to have been created on a specific date and time. With the "touch" command's magical "-d" option, you can manipulate the file's timestamp and make it seem like it traveled through time!

```plaintext
[root@192 Desktop]#touch -d "10 March 2023 10:10:10" file1
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685991828220/589ca4ff-ae12-43a7-8bdc-782d04aa5096.png align="center")

By including the "-d" option followed by the desired date and time in quotes, you've successfully altered the timestamp of the file named "file1." It's like stepping into a time machine and landing at 10:10:10 on March 10, 2023.

## Touch Timestamp - Change Acess and Modify as per the system's current time

* Change Access time : Imagine you have a file named "file1," and you want to update its access time to reflect the current moment. Let's dive right in and see how it works.
    

```plaintext
[root@192 Desktop]# touch -a file1
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685992067783/820d753a-bc8a-4401-b77a-4fa99e23bfab.png align="center")

The "Access" timestamp has been updated to reflect the moment you executed the "touch -a" command. It's now showing the current time, as if the file was accessed just a moment ago.

With the "touch" command's "-a" option, you can make files appear freshly accessed, whether it's for testing purposes, record-keeping, or simply satisfying your curiosity about file access times.

Change Modify Time : Imagine you have a file called "file2," and you want to update its modification time to a specific moment. The "touch" command is here to assist! Let's dive right in and see how it works

```plaintext
[root@192 Desktop]# touch -m file2
```

By using the "-m" option with the "touch" command, you have successfully updated the modification time of the file named "file2." It's as if the file's contents were modified at the exact moment you executed the command.

The "Modify" timestamp has been updated to reflect the moment you executed the "touch -m" command. It now shows the current time, as if the file's contents were modified just a moment ago.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685992513572/66e56d66-deb0-448f-b0cf-0e186c452e3d.png align="center")

## Touch Timestamp - Referencing from a file

1. Imagine you have two files, 'file1' and 'file2,' and you want to synchronize their timestamps. With 'touch -r,' the magic is at your fingertips. Simply execute the following command:
    

```plaintext
[root@192 Desktop]# touch -r file1 file2
```

In this example, 'file2' will inherit the timestamps of 'file1.' Their access, modification, and change times will align, creating a harmonious union between the two files.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685993211620/5cc9ed10-4d2a-4900-a5f2-b507f9bdf132.png align="center")

So there you have it, The "touch" command is your trusty companion for creating files effortlessly in the command-line interface. Whether you need to create one file or a whole bunch, "touch" has got you covered. And don't forget about its handy timestamp-updating feature for existing files!

I hope this friendly introduction to the "touch" command has sparked your curiosity and encouraged you to explore the world of command-line interfaces further. Stay tuned for more exciting command-line adventures in future blog posts!

Until then, Happy Linux-ing!

Love my content Let's Connet Here: [https://www.linkedin.com/in/theshubhamgour/](https://www.linkedin.com/in/theshubhamgour/)