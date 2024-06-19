---
title: "User Administration - User Management in Linux"
seoTitle: "User Administration - User Management in Linux"
datePublished: Tue Jun 20 2023 15:14:16 GMT+0000 (Coordinated Universal Time)
cuid: clj4feqdg000008mjathce16i
slug: user-management-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/qWwpHwip31M/upload/87755c53abf2f5fc9386be6f46eae72f.jpeg
tags: linux, aws, devops, linux-for-beginners

---

## User Administration

Hey there, fellow Linux enthusiasts! Today, we're going to dive into the wonderful world of user administration in Linux. Specifically, we'll be talking about two popular commands: `useradd` and `adduser`. These commands are used to add new users to your Linux system, but they have some differences you should be aware of. So, let's get started!

## User Administration

* * useradd - This command is as straightforward as it sounds—it simply adds a new user to your system. However, it's worth noting that `useradd` is a low-level command that requires you to manually configure various user settings. This means that you'll have to set up the user's home directory, default shell, and other options separately. While it provides a lot of flexibility, it also means that you'll have to spend some extra time and effort to ensure everything is set up correctly.
        
    * adduser - This command is a user-friendly alternative to `useradd`. It automates many of the configuration steps, making the user creation process much simpler and more convenient. When you run `adduser`, it prompts you for all the necessary information, such as the user's password, full name, and default shell. It even takes care of creating the user's home directory and setting up appropriate permissions. In short, `adduser` does most of the heavy lifting for you, making it a great choice for everyday user administration tasks.
        

## Important files

Let's now learn about some of the most important files which we are going to use in this user management blog

1. /etc/passwd : This file stores users general information such as uid,gid,home directory, login shell, etc.
    
2. /etc/passwd- : This is the backup file of /etc/passwd
    
3. /etc/shadow : This file stores users password information such as encrypted passwords, last password, change day,password expiry,password inactive,account expiry, etc.
    
4. /etc/shadow- : This is the backup file of /etc/shadow
    
5. /etc/group : This file contains the groups general information such as group name, redirected password, groupid, and group member's list
    
6. /etc/group- : This is the backup file of /etc/group
    
7. /etc/gshadow : This file stores groups password information such as encrypted password. groupadmin, group members list.
    
8. /etc/gshadow - : This is the backup file of /etc/gshadow
    
9. /etc/default/useradd : useradd command default list file
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687273551396/1582ac29-e6db-4ad9-aa0f-8bf7ca031dfc.png align="center")
    
    1. GROUP defines the default group ID for new user accounts in Linux.
        
    2. HOME specifies the directory path where user personal files and settings are stored.
        
    3. INACTIVE determines the number of days of inactivity before a user account is disabled (-1 means no automatic disablement).
        
    4. EXPIRE sets the expiration date for the user account (empty means no specific expiration date).
        
    5. SHELL defines the default shell or command interpreter for user accounts.
        
    6. SKEL refers to the skeleton directory, which contains files copied into a new user's home directory upon creation.
        
    7. CREATE\_MAIL\_SPOOL determines whether a mail spool directory is created for each new user account (yes means it is created).
        
10. /etc/login.defs : This is main config file for user administration, group administration and password management. If this file corrupts we cannot perform user administration, group administration and password management.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687273659375/b304a339-6023-4102-8443-78634a43ca7e.png align="center")
    
    1. 0 : root user
        
    2. 1-999 : System Users
        
    3. 1000 - 60000 : Local Users
        
11. /etc/bashrc : Global login program file environment variables are set here
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687273733111/65434e23-dc44-40c8-95bb-c0a96fb18536.png align="center")
    
12. /etc/skel: Skeleton directory
    
    1. .bashrc : local user login program file
        
    2. bash\_profile: local user's profile program file
        
    3. bash\_logout: local user's logout program file
        
13. /root : root user's home directory
    
14. /home/theshubhamgour : home directory of user theshubhamgour and here /home is base directory
    
15. /var/spool/mail/theshubhamgour : Local users mail box
    

## Useradd or Adduser

Linux is multiuser and multitasking which means it can create multiple users only root has the access to create new users

The account is created by `useradd` and `adduser` command, the command effects on `/etc/passwd` and `/etc/shadow` file.

To create a user fire the below command:

```plaintext
[root@192 Desktop]# useradd theshubhamgour
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687271272612/594bb053-ee77-4d0b-927b-2c350bd4e7cb.png align="center")

Users home directory will automatically be created in the `/home` directory. By default the ownership and group ownership is set to users.

Now to check whether the user is created execute the below command

```plaintext
[root@192 Desktop]# tail -1 /etc/passwd
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687272020122/d25463eb-336e-4f65-b9c5-c1401fe1c5c4.png align="center")

The command you executed is `tail -1 /etc/passwd`. Let's unravel its meaning step by step:

1. The `tail` command is used to display the last few lines of a file. In this case, you're targeting the file `/etc/passwd`.
    
2. `/etc/passwd` is a file in Linux that stores information about user accounts on the system. Each line in the file represents a user account entry.
    
3. The `-1` option passed to `tail` tells it to display only the last line of the file. So, you'll see the final entry from the `/etc/passwd` file.
    

---

Now, let's take a closer look at the output you received:

`theshubhamgour:x:1001:1001::/home/theshubhamgour:/bin/bash`

* **Username (**`theshubhamgour`**):** This field indicates the username of the user account.
    
* **Password placeholder (**`x`**):** In the past, the `/etc/passwd` file used to store encrypted passwords. However, modern systems store hashed passwords in a separate file for security reasons. The `x` in this field represents the placeholder indicating that the password is stored elsewhere.
    
* **User ID (**`1001`**):** This field represents the unique numerical ID assigned to the user.
    
* **Group ID (**`1001`**):** This field indicates the unique numerical ID assigned to the user's primary group.
    
* **User information (**`::`**):** These two colons represent fields that traditionally contained additional user information, such as the full name or contact details. However, they are often left empty nowadays.
    
* **Home directory (**`/home/theshubhamgour`**):** This field specifies the path to the user's home directory, which is where their personal files and settings are stored.
    
* **Default shell (**`/bin/bash`**):** The final field denotes the default shell assigned to the user, which determines the command interpreter they use.
    

By examining the last line of the `/etc/passwd` file, you were able to retrieve the user account details for `theshubhamgour`, including the username, user ID, group ID, home directory, and default shell.

Keep in mind that the `/etc/passwd` file is vital for user administration on Linux, and understanding its structure can help you manage user accounts effectively.

---

Now, let's take a closer look at the second output you received:

`theshubhamgour:!!:19528:0:99999:7:::`

This line represents the entry for the user `theshubhamgour` in the `/etc/shadow` file. Similar to the `/etc/passwd` file, the `/etc/shadow` file consists of several fields separated by colons. Let's understand what each field represents:

* **Username (**`theshubhamgour`**):** This field corresponds to the username of the user account.
    
* **Password field (**`!!`**):** In the `/etc/shadow` file, the password field stores the hashed or encrypted password. In this case, the `!!` indicates that there is no password assigned to the user. It means that the user account is locked and cannot be accessed with a password. This is often used when alternative authentication methods are employed, or when the account is disabled or awaiting password setup.
    
* **Last password change (**`19528`**):** This field represents the number of days since the password was last changed. It is measured in days since January 1, 1970 (also known as the Unix epoch).
    
* **Minimum password age (**`0`**):** This field indicates the minimum number of days that must pass before the password can be changed. A value of `0` means there is no minimum age requirement.
    
* **Maximum password age (**`99999`**):** This field sets the maximum number of days after which the password must be changed. In this case, the value `99999` means that the password can remain unchanged for an extended period.
    
* **Password warning period (**`7`**):** This field specifies the number of days before the password expires that the user should be warned about it. In this example, the warning will be given seven days in advance.
    
* **Inactive (**`:`**):** This field, when populated with a value, determines the number of days after the password expires before the account is considered inactive. In this case, it is empty, indicating no specific inactivity period.
    
* **Account expiration (**`:`**):** Similar to the previous field, this field, when populated, represents the expiration date of the account. An empty value means the account does not have a set expiration date.
    

Remember that the `/etc/shadow` file is crucial for password management and account security in Linux. Understanding its structure and the information it holds is important for effective user administration.

I hope this explanation helps you grasp the meaning behind the `useradd & adduser` command and its output. If you have any more questions or need further assistance, feel free to ask. Happy exploring and learning!