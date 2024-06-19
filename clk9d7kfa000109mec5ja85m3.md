---
title: "Managing User Password Policies with 'chage' Command in Linux"
datePublished: Wed Jul 19 2023 06:51:16 GMT+0000 (Coordinated Universal Time)
cuid: clk9d7kfa000109mec5ja85m3
slug: managing-user-password-policies-with-chage-command-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/em5w9_xj3uU/upload/b9fa9894a7e50072d1571370d15c4190.jpeg
tags: linux, aws, devops

---

## Introduction

In Linux, it's essential to enforce password policies for user accounts to enhance security. The 'chage' command is a powerful tool that allows system administrators to view and modify password-related settings for user accounts. In this blog, we will explore the different options of the 'chage' command and learn how to manage user password policies effectively.

FYI :

\[change + age = chage\] : It is used to list password policy of user using the command he can also change the password policies

* Listing User Password Policy:
    
    * The '-l' option in the 'chage' command is used to view the password policy settings for a specific user:
        
    * To see the password policy for the user 'john,' use the following command:
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689748446489/e0c0ac13-3e59-49b8-b954-beba002d65d0.png align="center")
        
        ```plaintext
        [root@192 Desktop]# chage -l john
        ```
        
* Setting Minimum Password Age:
    

* The '-m' option is used to define the minimum number of days a user must keep a password before changing it:
    
* To set a minimum password age of 7 days for 'john' use this command:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689748581518/35f3a5c1-80b1-4eeb-8cf9-36a1cc17a2be.png align="center")
    
    ```plaintext
    [root@192 Desktop]# chage -m 7 john
    ```
    
* Setting Maximum Password Age:
    

* The '-M' option allows you to specify the maximum number of days a password remains valid before the user is required to change it:
    
* To set a maximum password age of 90 days for 'bob,' use the following command:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689748730932/568ee0de-687f-4526-aec5-79edd512a688.png align="center")
    
    ```plaintext
    [root@192 Desktop]# chage -M 90 john
    ```
    
* Password Inactivity Period:
    
    * The '-I' option lets you specify the number of days after the password expires, during which the user can still log in before their account is locked:
        
    * To set a password inactivity period of 14 days for 'jane,' use this command:
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689748960019/8ed0f1a2-ab5e-409f-9831-5d00332d8c0a.png align="center")
        
        ```plaintext
        [root@192 Desktop]# chage -I 14 jane
        ```
        
* Account Expiry:
    
    * The '-E' option is used to set the expiration date for a user account. After this date, the user won't be able to log in without the account being reactivated:
        
    * To set the account expiry date of 'peter' to December 31, 2023, use the following command:
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689749091985/781d0f2f-6fac-47bd-a1a4-5968bb89e92f.png align="center")
        
        ```plaintext
        [root@192 Desktop]# chage -E '2023-12-31' peter
        ```
        
* Setting Password Expiry Warning Period:
    

* The '-W' option allows you to set the number of days before the password expires when the user receives a warning message:
    

To set a password expiry warning period of 7 days for 'guest,' use this command:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689749293387/124a07fa-e9cb-4da6-8842-030f5076cf71.png align="center")

```plaintext
[root@192 Desktop]# chage -W 7 guest
```

## Conclusion

The 'chage' command in Linux provides a convenient way to manage user password policies. By using various options, administrators can enforce password complexity, set password expiration, and enhance overall system security. Remember to regularly review and update password policies to maintain a secure environment. With the knowledge gained from this blog, you can now confidently manage user password policies in your Linux system.