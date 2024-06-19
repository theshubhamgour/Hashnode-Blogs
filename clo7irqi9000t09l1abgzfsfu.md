---
title: "Git and GitHub Made Simple: A Complete Guide - Part 4"
seoTitle: "Exploring Git History: Time Travel Made Easy"
seoDescription: "Discover the power of Git history with git log. Learn to filter commits, travel through time, and find the code changes that matter most. Dive into past."
datePublished: Thu Oct 26 2023 18:30:12 GMT+0000 (Coordinated Universal Time)
cuid: clo7irqi9000t09l1abgzfsfu
slug: git-and-github-made-simple-a-complete-guide-part-4
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/mRGtYItJRnA/upload/43842cfbe3e54cc326e2237bf38aeb0c.jpeg
tags: github, git, devops, devops-articles

---

In the previous parts, we learned the basics of Git, created repositories, and became code-committers. Now, let's go back in time! Git has a fantastic feature called "history," and it's like a magical time machine for your code. Buckle up, and let's dive deep into Git history.

### **Git Log: Your Time Machine**

Imagine you want to see all the changes and who made them in your project. Git's got your back with the `git log` command. You can use it to check the history of your code and even travel to a specific point in time.

**Getting Started with** `git log`

1. To see the history of a specific file, use:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log file1.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698158302560/89bed2ab-ecc5-44b5-a8af-3399b59d99c6.png align="center")
    
    This command will display all the commits related to that file.
    
2. To get a complete project history, simply type:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698158344300/a1d3e64a-ec3d-4caf-b26a-f74aaeb8ac1c.png align="center")
    
    This shows you every commit in your project.
    

**Explore Options with** `git log`

1. **Limit the Number of Commits Shown**: Use `-n` to specify the number of commits to display. For example, `git log -n 2` shows the last 2 commits.
    
    * ```plaintext
        theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log -n2
        ```
        
2. **Filter by Author**: If you want to see commits by a specific author, use `--author`. For instance, `git log --author="shubham"` will show commits by Shubham.
    
    * ```plaintext
        theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log --author="Shubham" 
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698158463664/8a00ec5a-0f17-4b51-8b8d-be65941f016b.png align="center")
        
3. **Time Travel**: You can journey through time using `--since` and `--until` to filter commits made between certain dates. For example, `git log --since="2016/12/13"` shows commits from that date onward.
    
    * ```plaintext
        theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log --since="2016/12/13"
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698158515868/cd6254c7-f12c-473e-be7d-e0e816ac0e29.png align="center")
    
4. **Search Commit Messages**: Use `--grep` to search for specific keywords or phrases in commit messages. For instance, `git log --grep="DB code"` will list commits with "DB code" in their messages.
    
    * ```plaintext
        theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log --grep="Create"
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698158580594/4a2b26a8-4888-48f9-bcad-c5b4dc783055.png align="center")
        
5. **One-Liner Logs**: If you prefer a high-level summary, `--oneline` gives you a condensed view with only commit IDs and messages.
    
    * ```plaintext
        theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log --oneline
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698158648560/29ae1af5-f006-4733-b3c8-21dc1f8f7e4b.png align="center")
        

### **Qn: Find the Unicorn Commits**

Let's say you want to find all the magical commits done by a user named "Shubham" that contain the words "Add" in the commit messages.

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log --author="Shubham" --grep="Add" -n2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698158738420/69377df5-4caa-4866-ab49-6f9c86cb88f4.png align="center")

This command will show you the commits that matches the mentiond criteria.

Now you're a Git time traveler, exploring your project's history with confidence. The `git log` command is your ticket to the past, where every line of code tells a story. Happy coding and time traveling! 🕰️

This is not the end more to come Join me in this series and lets connect on [**LinkedIn**](https://www.linkedin.com/in/theshubhamgour/)