---
title: "Exploring Advanced Features of the Marvelous mkdir Command! 🌟"
seoTitle: "Exploring Advanced Features of the Marvelous mkdir Command! 🌟"
datePublished: Sun Jun 11 2023 16:49:13 GMT+0000 (Coordinated Universal Time)
cuid: clirnu5yk000409mb4uoj78bo
slug: exploring-advanced-features-of-the-marvelous-mkdir-command
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/NnAchh_qAHc/upload/5d8aac4cc6a73c924eb06e7fcbb0e820.jpeg
tags: linux, aws, redhat, permissions

---

## Introduction

Hey there, fellow Linux enthusiasts! 🙌 Let's embark on a delightful journey into the realm of directories using the marvelous `mkdir` command! 🚀✨

Today, we're going to explore how this command can be used to create directories, both single and multiple, and even collaborate on the creation of folders. So, without further ado, let's dive right in! 💪🔍

## Directory Creation

To start off, let's focus on creating a single directory. 📁💡 Imagine you want to create a folder called "shubham" on your Desktop. With the power of `mkdir`, it's as simple as a breeze! 💨 Just open up your terminal and type in the following command:

```plaintext
[root@192 Desktop]# mkdir shubham
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686496300235/cb8acba2-b895-4f38-ae9c-9bcc75249dde.png align="center")

Voila! 🎩🐇 Your new directory called "shubham" magically appears on your Desktop. It's that easy! 😄

But wait, there's more! 😮🌟 `mkdir` isn't limited to creating just one directory at a time. You can also create multiple directories in one go! Let's say you want to create directories named "folder1," "folder2," and "folder3" inside the "shubham" directory. Fear not, for `mkdir` has got you covered! 🤝💫

Here's the command you need to enter:

```plaintext
[root@192 Desktop]# mkdir dir1 dir2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686496377586/499a1f2c-807a-4e8a-b41f-8feb47bc44b2.png align="center")

## Sequential Directory Creation with {} 📁🔢

Did you know that you can create sequential directories using the `mkdir` command? It's incredibly handy when you need a series of folders with numeric or sequential names. Let's dive in and see how it works! 😎

```plaintext
[root@192 Desktop]# mkdir folder{1..5}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686496471228/a2a0997d-96f4-410f-bcb7-d32bd46f4e42.png align="center")

By using the curly braces `{}`, we tell `mkdir` to create directories with names "folder1," "folder2," "folder3," "folder4," and "folder5." It's a quick and efficient way to generate a series of directories in a single command!

## Useful Handy Options 🛠️🆒

Now that we've mastered various ways to create directories, let's explore some handy options that will make our use cases even easier. Here are a few options worth knowing:

`-v` (verbose): This option provides more detailed output, allowing us to see what's happening behind the scenes

```plaintext
[root@192 Desktop]# mkdir -v newdir
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686498266774/bb727650-bb79-4559-85d9-31e49de9bbf5.png align="center")

`-p` (Collaborative Directory): We've already touched upon this option in our previous blog post, but it's worth highlighting again. The `-p` option enables us to create directories within directories, even if the parent directories don't exist. It's perfect for collaborative projects or organizing complex folder structures! 🤝📁

```plaintext
[root@192 Desktop]# mkdir -p folder1/folder2/folder3/folder4/folder5
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686499013616/e5881055-fa7d-4790-979c-5c2c8efe0f35.png align="center")

## Recursive Listing of Created Files 📂🔍

Once we've created our directories, it's always helpful to take a peek at what we've accomplished. The `ls` command comes to our aid, but with a twist! We can use the `-R` option to recursively list the files within a directory. Let's give it a try! 🕵️‍♀️📋

```plaintext
[root@192 Desktop]# ls -R /root/Desktop/folder1/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686499074777/7dd53b5f-0045-4c4a-a989-323630d51b8d.png align="center")

With this command, `ls` will traverse through all the directories within "folder1" and display a comprehensive list of the files contained within. It's like having a bird's-eye view of our directory structure! 🦜👀

And there you have it, dear Linux enthusiasts! By now, you're well-equipped with the knowledge of creating sequential directories, utilizing handy options like `-v`, `-p`, and even exploring the contents of your directories with `ls -R`. Your Linux adventures just got even more exciting! 🎉🌟

Keep embracing the power of `mkdir`, keep exploring new possibilities, and keep spreading the Linux

## Setting Permissions during Directory Creation 🛡️🏗️

Did you know that you can specify the permissions for a directory while creating it with `mkdir`? It allows you to control who can read, write, or execute the directory and its contents. Let's dive in and see how it works! 😃

```plaintext
[root@192 Desktop]# mkdir -m 700 dir
[root@192 Desktop]# stat dir
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686501846078/ce245b91-0ed8-4d18-8d8e-f5f30140e414.png align="center")

In this example, we use the `-m` option followed by the permission code (`700`) to specify the access rights for the directory named "dir." The permission code consists of three digits, each representing the permissions for the owner, group, and others, respectively.

Here's a breakdown of what each digit signifies:

* The first digit (7 in this case) represents the permissions for the owner of the directory.
    
* The second digit (0) signifies the permissions for the group.
    
* The third digit (0) indicates the permissions for others.
    

In our example, the owner has full access with read, write, and execute permissions (7), while the group and others have no permissions (0). It's a secure way to ensure that only the owner can interact with the directory and its contents. 🔒🔐

Upon executing this command, `stat` will display a comprehensive set of information about the "dir" directory, including the permissions. You'll be able to confirm that the permissions you set during creation are indeed in place. It's like having an X-ray vision for your directory's access control!

So there you have it, my Linux-loving friends! The incredible power of the `mkdir` command is at your fingertips. Whether you're creating single directories, multiple directories, or even collaborative spaces, `mkdir` has your back! 🤩💪

Keep exploring, keep learning, and keep spreading the Linux love! 🐧❤️ Happy directory creation with `mkdir`! 📂😊