---
title: "Delete or remove files and directories in linux"
seoTitle: "Delete or remove files and directories in linux"
datePublished: Mon Jun 12 2023 08:02:25 GMT+0000 (Coordinated Universal Time)
cuid: cliskgjnz000p0al07462c9wj
slug: delete-or-remove-files-and-directories-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/7EwWeNyzSwQ/upload/0460e66dc9b30f73e0414e85a28094a9.jpeg
tags: linux, aws, linux-for-beginners

---

## Introduction

Hello everyone! Today, we're going to dive into the wonderful world of the `rmdir` command. This nifty little tool is designed specifically to help you delete empty directories effortlessly. Whether you're a seasoned command-line guru or a beginner, we've got you covered. So, let's get started on this exciting journey!

## Deleting an Empty Directory:

Let's begin with the basics. The `rmdir` command, as mentioned earlier, is used to remove empty directories. It's a simple and straightforward process. Just open up your terminal or command prompt and type in the following command:

```plaintext
[root@192 Desktop]# rmdir dir
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686554226251/6afa28cc-ed36-485c-ae05-4faa176167fa.png align="center")

And just like that, poof! The empty\_folder is gone!

## Deleting Non-Empty Directories with rmdir -rf

Now, what if you have a directory that's not empty and you want to delete it along with all its contents? Fear not, my friend! We have a solution for you. The `rm -rf` command comes to the rescue. It stands for "remove recursively and forcefully."

To delete a non-empty directory and all its contents, use the following command:

```plaintext
[root@192 Desktop]# rm -rf folder/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686554447104/4dd94f54-7dd9-4c2d-be74-0a687bcbe109.png align="center")

This command will remove the "folder" directory and everything inside it, without asking for confirmation. Please exercise caution while using this command, as the deletion is irreversible!

## Creating Nested Directories with Ease and Deleting it.

One of the coolest features of the `mkdir` command is its ability to create nested directories. Let's break down an example to illustrate this. Imagine we're working in the `/root/192/Desktop` directory, and we want to create a nested directory structure like this: `folder/dir1/folder2/dir2`. Here's how we can do it using the `mkdir -p` command:

```plaintext
[root@192 Desktop]# mkdir -p folder/dir1/folder2/dir2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686555690223/32cc7060-c99d-4d30-b1ad-252a0ee12480.png align="center")

By running this command, we're instructing the system to create the nested directories one by one, from the outermost to the innermost. In our case, it will create the `folder` directory first, followed by the `dir1` directory inside `folder`, and so on, until it reaches `dir2`.

You might be wondering what the `-p` option does in the `mkdir` command. Well, it's quite simple! The `-p` option stands for "parents" and allows you to create parent directories that don't exist yet.

In our example, if we didn't use the `-p` option, we would encounter an error because the parent directories (`folder`, `dir1`, and `folder2`) don't exist. But thanks to the `-p` option, the command automatically creates all the necessary parent directories on the fly. It's like a magical shortcut that saves us from creating each directory individually!

## Verbose Mode: rm -v

Sometimes, you may want to see a detailed report of the files being removed. In such cases, you can use the `-v` option. It stands for "verbose" and provides additional information during the deletion process.

To remove a file with verbose output, use the following command:

```plaintext
[root@192 Desktop]# rm -r folder/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686556030848/9527b10c-9592-4aa7-8957-42d119d53118.png align="center")

When you execute this command, you'll see a list of files being deleted, along with their names. It's a handy option if you want to keep track of what's happening behind the scenes.

## Interactive Mode: rm -i

What if you want to double-check before deleting a file? The `-i` option comes to your rescue. It stands for "interactive" and prompts you for confirmation before removing each file.

To use the interactive mode, run the following command:

```plaintext
[root@192 Desktop]# rm -ri test1
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686556655531/38bcbc29-2106-43f0-b19a-5181d5efd8cc.png align="center")

Now, when you execute this command, the system will ask you to confirm the deletion of the file. You can then choose to proceed or cancel the operation. It's a great safety net to prevent accidental deletions!

## Conclusion

Congratulations! You've learned how to use the `rm` command to remove files and directories like a pro