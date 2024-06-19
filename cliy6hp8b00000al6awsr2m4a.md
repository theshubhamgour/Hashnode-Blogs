---
title: "Exploring the Head and Tail Commands in Linux"
seoTitle: "Exploring the Head and Tail Commands in Linux"
datePublished: Fri Jun 16 2023 06:18:01 GMT+0000 (Coordinated Universal Time)
cuid: cliy6hp8b00000al6awsr2m4a
slug: head-and-tail
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/8EzNkvLQosk/upload/353225399ee29ecee9232c1643cbf02a.jpeg
tags: linux, aws, devops

---

## Introduction

When working with files in Linux, it's essential to be able to quickly peek at the beginning or the end of a file. That's where the trusty `head` and `tail` commands come to the rescue! These handy commands allow you to view a snippet of a file without having to open the entire thing. Let's dive in and discover how these commands can make your Linux adventures a whole lot easier.

## Head Command - A Glimpse into the Beginning

The `head` command lets you take a peek at the starting lines of a file. Whether you're curious about the first few lines of a text document or want to examine the initial bytes of a binary file, `head` has got you covered.

Usage: To use `head`, simply type "head" followed by the name of the file you want to explore. By default, it displays the first ten lines of the file. However, you can customize the number of lines or bytes displayed by using the appropriate options.

Example 1: Let's say you have a file called "example.txt," and you want to see the first 5 lines of its content. Just type:

```plaintext
[root@192 Desktop]# head -5 example.txt 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686895887431/474c4386-960c-4774-a184-f05872260a13.png align="center")

By executing this command, you will see the first five lines of the "example.txt" file right in your terminal. It's a fantastic way to quickly glance at the initial portion of your file without the need to open it entirely.

## Exploring the Tail Command in Linux

Have you ever found yourself curious about the end of a file without scrolling through the entire content? The tail command in Linux is here to save the day! With just a simple command, you can catch a glimpse of the final lines of a file. Let's dive into the world of the tail command and discover how it can add convenience to your Linux journey.

The tail command enables you to view the tail end of a file effortlessly. It's like fast-forwarding to the final scenes of a movie to catch the thrilling conclusion. Whether you're monitoring log files or simply curious about the last portion of a text or binary file, the tail command has your back.

Let's say you have a file called "example.txt," and you want to see the last two lines of its content. Simply enter the following command:

```plaintext
[root@192 Desktop]# tail -2 example.txt 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686896054876/49d79696-625e-4f8f-86b4-d8bc5f6093e5.png align="center")

Executing this command will display the last two lines of the "example.txt" file in your terminal. It's a convenient way to quickly catch a glimpse of the final portion of your file without scrolling through the entire document.

## Conclusion

In the vast Linux universe, the head and tail commands shine as reliable companions for file exploration. The head command allows you to take a sneak peek at the beginning of a file, while the tail command lets you catch a glimpse of the final lines. These commands bring convenience and efficiency to your Linux experience, sparing you from opening entire files when you only need a quick glance.

With the head command, you can effortlessly skim through the initial lines of a file, whether it's a text document or a binary file. By customizing the number of lines or bytes displayed, you have full control over the scope of your preview.

On the other hand, the tail command helps you witness the grand finale of a file. It's perfect for monitoring logs, as you can continuously view the last few lines and stay up to date with real-time updates. Additionally, tail enables you to explore the ending of both text and binary files, giving you a sense of closure without the need to scroll through everything.

Whether you're a seasoned Linux user or just starting your journey, the head and tail commands prove to be invaluable tools. Their simplicity and versatility make them go-to options for quickly examining files. So, go ahead and embrace the power of head and tail commands to streamline your file exploration process in Linux.