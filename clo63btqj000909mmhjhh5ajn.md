---
title: "Git and GitHub Made Simple: A Complete Guide - Part 3"
seoTitle: "Git Operations commands"
datePublished: Wed Oct 25 2023 18:30:09 GMT+0000 (Coordinated Universal Time)
cuid: clo63btqj000909mmhjhh5ajn
slug: git-and-github-made-simple-a-complete-guide-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/UT8LMo-wlyk/upload/bef8d2f09b8a386232d0205293e13d24.jpeg
tags: github, git, devops, devops-articles

---

Welcome to the next phase of your Git journey! In this part, we'll dive into some essential Git terminology and commands that will help you navigate the Git universe. Let's get started.

### **Git Jargon**

Before we explore commands, let's decode some Git jargon:

* **Remote Repository**: Think of this as the GitHub server or a server where your code is stored remotely. It's like the cloud storage for your code.
    
* **Working Directory**: This is your local project directory (the current directory, denoted as `.`). It's where you create, modify, and organize your files.
    
* **Local Repository**: This is the hidden `.git` directory within your project directory. It contains all the metadata and version history of your project.
    
* **Stage / "Staging Index"**: The stage is like a checkpoint where you decide what changes to include in your next commit. It's represented as `..`.
    

### **Common Git Commands**

Let's explore some common Git commands and their usage:

**Checking the Repository URL:**

You can check the repository URL using:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git remote -v
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698149097677/9789d7ad-6a60-4efe-8dcc-330fe45273b8.png align="center")

**Cloning a Remote Repository:**

To download a remote repository for the first time, use:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop$ git clone https://github.com/theshubhamgour/git-hash.git
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698149153281/7074a77d-95fd-4bec-a8ff-85bba59becf4.png align="center")

**Pulling Modified Content from Remote Repo:**

If you want to download modified content from the remote repository and merge it into your working area, use:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git pull
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698150117823/d8776f2b-4d37-4514-9dc1-3b5327fb401f.png align="left")

**Fetching and Merging Modified Content:**

To download modified content without merging it into your working area immediately, use:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git fetch
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git merge
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698150218579/baab0e05-af02-4ca2-979d-eb8f7bd3fc6f.png align="center")

**Skip Staging:**

If you want to skip the staging step and commit all pending changes, you can use the `-am` option with the commit command:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git commit -am "Skipping stage"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698150350928/ba36a6d1-ac18-4fe0-9dc0-20c534299851.png align="center")

### **Creating a Local Repository**

Let's walk through the process of creating a local repository step by step:

1. **Initialize a Local Repository**:
    
    First, create or initialize a local repository within a folder using the following commands:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop$ mkdir test-repo1
    theshubhamgour@ubuntuM1:~/Desktop$ cd test-repo1/
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ git init
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698153372904/110c8de6-5559-4feb-bd79-221047193a2d.png align="center")
    
    This sets up your local repository. Now, you can add your code or files.
    
2. **Create Source Code**:
    
    Within your local repository, you can create some source code files, for example, [`Login.java`](http://Login.java).
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ touch sample.java
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ git add sample.java
    ```
    
3. **Add Files to the Stage**:
    
    To include a file in your next commit, add it to the stage using:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ git add sample.java
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698153521314/fb2d545c-7579-4408-8f39-74a75e03cd19.png align="center")
    
4. **Commit the File to the Local Repository**:
    
    Commit your file to the local repository with a meaningful commit message:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ git commit sample.java -m "adding local init file"
    ```
    
    **Check the Commit Log**:
    
    You can check the commit log for a specific file using:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ git log sample.java
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698153743787/87df85ff-93bd-43cd-84ad-820adb8f2d77.png align="center")

1. `git remote add <folder-name> <repo-url>`: This command adds a remote repository as a reference in your local repository. The `<folder-name>` is an alias for the remote repository that you can use in Git commands. `<repo-url>` is the URL of your remote repository on GitHub.
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ git remote add test-repo1 https://github.com/theshubhamgour/test-repo1.git
    ```
    
2. `git push <folder-name>`: This command pushes your local changes to the remote repository. `<folder-name>` is the alias you assigned to the remote repository in the previous step.
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/test-repo1$ git push test-repo1
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698154586604/40c56dff-fa91-444d-b14f-2bb4b2df09ce.png align="center")
    

Now all the changes from the local will be present on the central repo

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698154664188/198a0426-d37d-4ac7-a827-aa5af3cac6d1.png align="center")

And there you have it! You've learned some essential Git commands and got a handle on Git terminology. With this knowledge, you're better equipped to work with Git in various situations.

Stay tuned for the next part, where we'll dive into branching, a powerful feature of Git that makes code management and collaboration even more efficient. Happy coding! 🚀🌟

This is not the end more to come Join me in this series and lets connect on [**LinkedIn**](https://www.linkedin.com/in/theshubhamgour/)