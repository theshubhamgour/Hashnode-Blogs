---
title: "Mastering the Echo Command: Formatting and Control with -e and Escape Sequences"
seoTitle: "Mastering the Echo Command: Formatting and Control with -e and Escape"
datePublished: Thu Jun 08 2023 06:55:14 GMT+0000 (Coordinated Universal Time)
cuid: climsaqhp001c09l83v3y0ar7
slug: echo-command-formatting
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/5t1lUr0NmHI/upload/889286d86103f7c494b8bb093a8e0644.jpeg
tags: linux, aws, command-line, cli, linux-for-beginners

---

## Introduction

Hey there! Welcome back to our blog. Today, we're going to dive into the versatile and powerful command known as "echo". 🌟

Echo is a handy utility that allows us to display text on the command line or in scripts. It's simple to use and offers some cool features that can enhance your command-line experience. So, let's get started!

First things first, let's talk about the basic usage of the "echo" command. All you need to do is type "echo" followed by the text you want to display. For example, if you want to print "Hello Namaste", you would type:

```plaintext
[root@192 Desktop]# echo "Hello Namaste"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686146071568/1e6c748a-a451-4f35-9485-0fe60cfc4afb.png align="center")

The "echo" command in the shell is a handy tool that allows us to display text or values on the screen. It's incredibly useful for printing messages, debugging, or even creating dynamic scripts. So let's get started and explore some of its cool features!

## Printing Special Characters

Let's explore some special characters that can be used with the "echo" command to add some formatting or whitespace to our output. These characters are known as escape sequences and are prefixed with a backslash (\\) to differentiate them from regular characters.

Escape Sequences :

1. \\n -&gt; New Line
    
2. \\t -&gt; Horizontal Tab
    
3. \\v -&gt; Vertical Tab
    
4. \\b -&gt; Backspace
    
5. \\c -&gt; Continue
    

## Let's explore with examples

1. \\n: This escape sequence stands for a newline character, which moves the cursor to the beginning of the next line. For instance, if you want to print two lines of text, you can use it like this:
    

```plaintext
[root@192 Desktop]# echo -e "This is line one.\nThis is line two."
```

1. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686146838463/35c52fa1-4d69-403d-bf7d-c7e6b7149f70.png align="center")
    
2. \\t: The \\t escape sequence adds a horizontal tab, which creates a horizontal indentation in your output. Here's an example:
    
    ```plaintext
    [root@192 Desktop]# echo -e "Name:\tShubham Gour\nAge:\t22"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686147065471/805d6c2e-2a2e-432f-949c-5c9ecc4f8cde.png align="center")
    
3. \\v: The \\v escape sequence inserts a vertical tab, which behaves similarly to the newline character but moves the cursor to the beginning of the next line with some additional vertical spacing. Try this out:
    
    ```plaintext
    [root@192 Desktop]# echo -e "This is paragraph one.\vThis is paragraph two."
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686147152321/fbf3760c-668a-4660-8f14-4b30ce7f0d82.png align="center")
    
4. \\b: This escape sequence represents the backspace character, which moves the cursor one character back. It can be useful for erasing or overwriting characters. Check out this example:
    

```plaintext
[root@192 Desktop]# echo -e "Pass\b\b\b\b\b\bHidden"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686147383064/0158b705-e8e1-4f0d-8a6c-98f4ea077692.png align="center")

1. /c : suppress trailing new line with backspace interpreter ‘-e‘ to continue without emitting new line.
    
    ```plaintext
    [root@192 Desktop]# echo -e "Hello \c"
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686207238812/c9a25d95-807f-46f3-a940-e93b20214c2b.png align="center")

## Set Variables with and display value with echo

Let's touch on setting and deleting variables with the "echo" command. Variables are like containers that can hold different values. You can assign a value to a variable and then access that value whenever needed. Here's how you can set a variable using "echo":

```plaintext
[root@192 Desktop]# name="Shubham Gour"
[root@192 Desktop]# echo $name
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686147776233/fa3f64c3-f12d-434e-b5a0-b12246d6a667.png align="center")

In this example, we assign the string "Shubham Gour" to the variable "name" and then use "echo" to display its value.

## Unset Variables and display with echo

To delete a variable, you can use the "unset" command. For instance try the below command:

```plaintext
[root@192 Desktop]# unset name
[root@192 Desktop]# echo $name
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686147985278/0629f8ef-9799-4f4a-b66e-1f757d46c49e.png align="center")

In the above when we hit echo $name we will get a space since the value is removed/deleted from the variable

## Practical Questions on echo

Lets now see some practical use of echo command and unleash the power we learned till now

Question 1# : Run Multiple commands in same line

```plaintext
[root@192 Desktop]# echo "Hello" ; echo "World"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686204846818/3de7edec-e3a0-4687-8ed6-1314d9f2aed6.png align="center")

Question 2#: Print Message and content at the same time

```plaintext
[root@192 Desktop]# echo "Output of the command : " ; ls
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686205823011/7681dbd0-89e5-4656-845f-2b2649172421.png align="center")

Question 3#: Print sequence with echo command

```plaintext
[root@192 Desktop]# echo {1..10}{A..E}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686205940066/53102401-3d21-419e-b2a4-628b0fa6c67c.png align="center")

Question 4#: Check exit status of the previous executed command

```plaintext
[root@192 Desktop]# echo $?
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686206031888/08bc8ec8-cb38-43c9-afc9-d83763067abc.png align="center")

Here 0 means the command was executed successfully 1 and 2 meaning error in the output of the previous command

## Let's explore System Variables

In the Linux operating system, system variables play a crucial role in managing and customizing the command-line environment. We will now unravel the significance of these variables and how they shape your Linux experience.

1. $PWD - Present Working Directory:
    
    ```plaintext
    [root@192 Desktop]# echo $PWD
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686150881252/93f1c4d2-d528-4ee5-80e9-a6c579a14498.png align="center")
    
    The PWD variable holds the absolute path to the current working directory. It helps you identify your current location within the file system. For example, running the command `echo $PWD` will display the full path to your current directory, such as `/home/user/Documents`.
    
2. $SHELL : Default Shell:
    
    ```plaintext
    [root@192 Desktop]# echo $SHELL
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686151676017/6dcec014-5426-43a2-8941-93e5ad92a7a2.png align="center")
    
    SHELL denotes the default shell or command-line interpreter for the user. It specifies the program that processes your commands. To view your default shell, use the command `echo $SHELL`, which might output something like `/bin/bash` or `/usr/bin/zsh` Based on the default shell as per your config file
    
3. $HOME : Home Directory:
    
    ```plaintext
    [root@192 Desktop]# echo $HOME
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686152077806/e54d2a1b-3352-4918-b26a-55c5309c92bc.png align="center")
    
    HOME represents the path to the user's home directory. It serves as the default location when you open a terminal session or execute certain commands. To access your home directory, you can use the shortcut `cd ~` or `cd $HOME`.
    
4. $HOSTNAME - System Hostname
    
    ```plaintext
    [root@192 Desktop]# echo $HOSTNAME
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686152188718/ae8b799b-4702-4fab-a21d-4dd1b37e9084.png align="center")
    
    The HOSTNAME variable stores the name assigned to your system on a network. It helps identify your machine when connected to other systems. To view the hostname, simply type `echo $HOSTNAME`.
    
5. $USER - Current User
    
    ```plaintext
    [root@192 Desktop]# echo $USER
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686152285418/8bc3af95-067c-4e68-ba0c-22f38917a833.png align="center")
    
    USER contains the username of the currently logged-in user. It provides a convenient way to retrieve your username programmatically. For instance, running `echo $USER` will display your username, such as `root` or `shubham`.
    
6. $0 - Current Shell Name
    
    ```plaintext
    [root@192 Desktop]# echo $0
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686152377095/5bfbea96-1ef3-4a79-b27f-cba5daf831e0.png align="center")
    
    It helps identify the active shell environment. To see the current shell, you can utilize the command `echo $0`.
    

Understanding Linux system variables like $PWD, $SHELL, $HOME, $HOSTNAME, USER and $0 allows you to navigate and customize your Linux command-line experience effectively. These variables provide essential information about your environment, efficient navigation, customization, and scripting. By harnessing their power, you can enhance your productivity and efficiency on the Linux command line.