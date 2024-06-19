---
title: "Linux Adventures: A Guide to Cat and Redirection"
seoTitle: "Linux Adventures: A Guide to Cat and Redirection"
datePublished: Wed Jun 07 2023 06:49:49 GMT+0000 (Coordinated Universal Time)
cuid: clilcnx7q001b08lggpnx9ouj
slug: linux-adventures-a-guide-to-cat-and-redirection
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Uaf6XwW4n10/upload/f3c700121209e9d5f75902507c8e8f72.jpeg
tags: linux, command-line, linux-for-beginners

---

## Introduction

The `cat` command is used in Unix-like operating systems to concatenate and display the contents of files. With "cat," you can effortlessly view the contents of one or more files in one go.

But "cat" isn't just about displaying files—it has a few tricks up its sleeve! You can combine multiple files, creating a mixtape of text, by listing their names after the command.

Furthermore, "cat" can be a fantastic assistant when it comes to redirecting file contents. Using the "&gt;" symbol, you can redirect the output of a command to a new file or overwrite an existing one, just as a cat leaves its paw prints on a fresh canvas. Alternatively, the "&gt;&gt;" symbol appends the output to an existing file. Enough of theory lets dive in to the Lab

## The Power of CAT command

1. `cat file1`: This command displays the contents of `file1` in the terminal.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686052312202/88038ad8-0c13-4167-a420-d391a1be0751.png align="center")
    
2. `cat file1 file2`: This command displays the contents of both `file1` and `file2` in the terminal, one after the other.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686052496653/c6c0da58-7bc0-4ada-8661-bdedcf29cf01.png align="center")
    
3. `cat file1 > output.txt`: This command redirects the contents of `file1` to `output.txt`, also it overwrites the file if it already exists. If `output.txt` doesn't exist, it will be created.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686116349299/1f267955-dd9c-4a29-9483-40af3203e7c5.png align="center")
    
4. `cat file1 2> error.txt`: This command redirects the error output (stderr) of `file1` to `error.txt`, overwriting the file if it already exists. If `error.txt` doesn't exist, it will be created.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686116428100/2ba9afd3-a48d-49fe-b63c-d845b8955a52.png align="center")
    
    In the above case there was no file with fileds, hence the error was stored in the error.txt instead of throwing the error message on terminal
    
5. `cat file1 >> output.txt`: This command redirects the contents of `file1` to `output.txt`, appending it to the file if it already exists. If `output.txt` doesn't exist, it will be created.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686117348119/026491dc-fe07-4004-a78e-8a756e8ca7d8.png align="center")
    
    In the above case we already had file1 created in out system, hence we appended the output file with the content for file1
    
6. `cat -T file1`: This command displays the contents of `file1` and shows tabs as `^I` to make them visible.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686117495407/78679876-a3f4-443f-b433-55a7ea880ead.png align="center")
    
7. `cat -E file1`: This command displays the contents of `file1` and adds a `$` symbol at the end of each line.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686117537714/faabc932-820a-4a32-b25d-b02945d071ad.png align="center")
    
8. `cat -n file1`: This command displays the contents of `file1` and adds line numbers to each line.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686117584007/d111fada-c209-440f-858d-2743d53cdbce.png align="center")
    
9. `cat -EnT file1`: This command displays the contents of `file1` and combines the options `-E`, `-n`, and `-T` to show tabs as `^I`, add line numbers, and add a `$` symbol at the end of each line.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686117659076/375d7250-5a15-461f-bcd6-6262b649b7ea.png align="center")
    

To display the contents of two files at once, you can simply list both file names after the `cat` command, separated by a space. For example, `cat file1 file2` will display the contents of `file1` and `file2` consecutively in the terminal.

## Cat Redirectors

Basically there are two types of redirectors mostly used with the CAT command namely :

1. `>` (single greater-than symbol):
    

`>>` (double greater-than symbol):

1. `>` (single greater-than symbol): The `>` symbol is used for file redirection and allows you to redirect the output of a command to a file, creating or overwriting the file if it already exists. Here's an example:
    

```plaintext
[root@192 Desktop]# echo "Hello World!" > greetings.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686118344540/70c5f17b-437e-4198-a437-3c8b64434a89.png align="center")

In this example, the text "Hello, World!" is redirected to the file `greetings.txt`. If the file already exists, it will be overwritten; otherwise, a new file will be created.

1. `>>` (double greater-than symbol):
    

The `>>` symbol is similar to `>`, but it appends the output of a command to the end of a file, instead of overwriting it. Consider this example:

```plaintext
[root@192 Desktop]# echo "Namaster Duniya" >> greetings.txt 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686118628760/57c91cc3-3143-4990-bd40-3be33996e812.png align="center")

In this case, the text "Namaster Duniya" is appended to the existing `greetings.txt` file, preserving the previous content. If the file doesn't exist, it will be created.

File redirection using `>` and `>>` is not limited to the `echo` command; you can redirect the output of other commands or even the contents of multiple files at once. Just remember to use the appropriate symbol and specify the target file name.

So, whether you're saving important notes, capturing program output, or organizing data, file redirection with `>` and `>>` provides a convenient way to manage and store information efficiently.

## Question #1 Scenario Based Question for the redirectors

Let's consider you want to list down all the items in the /root directory and you have another directory that does not exist and you want to list content of that speicifc directory but still it is an task how to do it lets crack this out

```plaintext
[root@192 Desktop]# ls /root taskdir 1>data.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686119021160/4f78ab87-f43b-40bc-965c-25e0d8c4d647.png align="center")

When you execute the above command you will be successfully listing the content of the /root directory in the data.txt file but at the same time it mentioned that the taskdir does not exist. Now you next task is to not to show error on console rather than that print it over the data.txt - Let's cover this

## Question #2 Scenario Based Question for the redirectors

Inorder the avoid the same we will make use of `2>>` which will make our command more efficient and we will be good to go with it

```plaintext
[root@192 Desktop]# ls /root taskdir 2>>data.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686119370693/f3d4fe14-0ba0-4467-aa5a-50c61111fa87.png align="center")

The above command does the same as the previous one but the only change here is we have appended the error on the data.txt file and no error was seen upon command execution

I Hope you learned lot about cat and the redirectors see you on the next blog until then Happy Linux-ing!

If you want to connect with me: [https://www.linkedin.com/in/theshubhamgour/](https://www.linkedin.com/in/theshubhamgour/)