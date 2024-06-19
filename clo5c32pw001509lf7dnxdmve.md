---
title: "Day #4  Basic Linux Shell Scripting for DevOps Engineers."
seoTitle: "Demystifying Linux Shell Scripting for DevOps"
seoDescription: "Learn the basics of Linux Shell Scripting for DevOps. Explore #!/bin/bash, user input, and if-else. Simplify complex tech with easy scripting examples."
datePublished: Wed Oct 25 2023 05:47:31 GMT+0000 (Coordinated Universal Time)
cuid: clo5c32pw001509lf7dnxdmve
slug: day-4-basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/2idWld85f-M/upload/25867e9f286d4c2ffe981e6dda569dee.jpeg
tags: devops, shell-scripting, shell-script, devops-articles

---

Hi Everyone, welcome back today we are going to simplify one piece puzzle: Linux Shell Scripting. In this beginner-friendly guide, we'll break it down into digestible bits and see how it fits into the larger DevOps picture.

## [What is Kernel](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day04/README.md#what-is-kernel)

The kernel is a computer program that is the core of a computer’s operating system, with complete control over everything in the system.

## [What is Shell](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day04/README.md#what-is-shell)

A shell is a special user program that provide an interface to the user to use operating system services. Shell accept human readable commands from user and convert them into something which kernel can understand. It is a command language interpreter that execute commands read from input devices such as keyboards or from files.

## [What is Linux Shell Scripting?](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day04/README.md#what-is-linux-shell-scripting)

A shell script is a computer program designed to be run by a Linux shell, a command-line interpreter. The various dialects of shell scripts are considered to be scripting languages. It's a user program that serves as an interface between you and the operating system. You might wonder how you communicate with your computer – that's where the shell comes in. It takes the commands you type and makes them understandable to the kernel. It's like a translator for your computer.

## **#!/bin/bash vs. #!/bin/sh**

The `#!/bin/bash` is called a shebang or hashbang. It tells the system which interpreter to use for the script. You can also use `#!/bin/sh`, but it might use a different interpreter. `bash` is more common and provides additional features.

### **Steps to Create a Shell Script :**

* Step 1: Use any editor vim or nano script
    
    `Syntax: vim first_`[`script.sh`](http://script.sh/)
    
* Step 2: Permit to execute the file
    
    `Syntax: chmod <<permission>> <<`[`filename.sh`](http://filename.sh)`\>>`
    
    `chmod 755 first_`[`script.sh`](http://script.sh/)
    

This will set the permission read, write, execute (7), for group and others permission is being read and execute (5)

* Step 3: Execute the script as
    
    `Syntax: bash first_`[`script.sh`](http://script.sh/)`Or ./first_`[`script.sh`](http://script.sh/)
    

## Shell Script Example

```plaintext
#!/bin/bash
echo "I will complete #90DaysOfDevOps challenge"
```

The above script will print the message `"I will complete #90DaysOfDevOps challenge"` when executed.

* Write a Shell Script to take user input, input from arguments and print the variables.
    

```plaintext
#!/bin/bash
echo "Enter your name : " 
read Name
echo "Your name is : $Name"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698212402294/18352d20-41ce-40a5-94f2-2d7d0e1296e6.png align="center")

* Write an Example of If else in Shell Scripting by comparing 2 numbers
    
    ```plaintext
    #!/bin/bash
    a=4
    b=5
    if [ $a -gt $b ];
    then
            echo "$a is Greater than $b"
    else
            echo "$b is greater than $a"
    fi
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698212688263/774661b2-1545-482c-8c9d-d73c285b434a.png align="center")
    
    This script compares two numbers, `a` and `b`, and tells you which one is greater.
    
    Shell scripting is a powerful tool for automating tasks and making our DevOps journey smoother. With the right scripts, you can achieve more in less time. So, embrace the shell, start scripting, and make your computer work for you!