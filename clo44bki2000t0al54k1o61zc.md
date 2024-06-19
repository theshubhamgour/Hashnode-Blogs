---
title: "Git and GitHub Made Simple: A Complete  Guide - Part 1"
seoTitle: "Understanding Git and GitHub: A Beginner's Guide"
seoDescription: "Discover Git and GitHub in this beginner-friendly guide. Learn the basics, setup, and start collaborating with ease. Your gateway to version control."
datePublished: Tue Oct 24 2023 09:22:25 GMT+0000 (Coordinated Universal Time)
cuid: clo44bki2000t0al54k1o61zc
slug: git-and-github-made-simple-a-complete-guide-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/wX2L8L-fGeA/upload/234aaf7568f801ad1d254bd1f40eb92e.jpeg
tags: github, git, devops, devops-articles

---

If you're new to the world of version control and collaboration, don't worry. We've got you covered. In this easy-to-understand guide, we'll break down Git and GitHub, making it a easier to grasp.  

## What is VCS (Version Control System)?

* A Version Control System (VCS) is a software tool that tracks changes in files. It's like a time machine for your code, allowing you to manage different versions, collaborate with others, and keep your work organized.
    

## Why Do We Need VCS?

* **Collaboration**: VCS enables multiple people to work on the same code without conflicts.
    
* **History and Tracking**: It records changes, showing who did what and when.
    
* **Backup and Recovery**: It's a safety net for your work.
    
* **Branching and Merging:** You can work on new features separately and merge them later.
    
* **Conflict Resolution**: It helps resolve conflicts when changes clash.
    
* **Remote Collaboration**: It allows global teamwork via platforms like GitHub.
    

## **Key VCS Features:**

* **Commit**: Save changes with a meaningful message.
    
* **Branching**: Create separate lines of development.
    
* **Merging**: Combine changes from different branches.
    
* **Conflict Resolution**: Handle conflicts when multiple people edit the same code.
    
* **History Tracking**: Keep a log of changes, who made them, and when.
    
* **Rollback**: Revert to a previous version when needed.
    
* **Collaboration**: Enable teamwork without complications.
    

## **What's Git?**

Think of Git as your magical time-traveling journal for code. When you make changes to your code, Git keeps track of every edit. If you ever need to revisit a previous version, Git can take you back in time, just like a time machine for your work.

**Why Do We Need It?**

Imagine working on a group project. Everyone's adding their bit, and things can get messy. Git helps keep things organized. It lets multiple people work on the same project simultaneously without stepping on each other's toes. It's like a well-choreographed dance where everyone knows their steps.

## **Meet GitHub**

GitHub is like the online hub for your Git repositories. You can think of it as a cloud storage system for your code. It's a place where you can share your code with others, collaborate, and track changes together. Like a digital playground for coders.

## **Git Installation on Ubuntu:**

To install Git on Ubuntu, follow these simple steps in your terminal:

1. Update the package list to ensure you're installing the latest version:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop$ sudo apt-get update
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698135040133/d00314a8-2f26-403e-a611-42afc384a461.png align="center")
    
2. Install Git:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop$ sudo apt-get install git -y
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698135145877/70e9c746-858e-4bc5-81d9-a18e13d28902.png align="center")

**Verify Git Installation:**

To check if Git is successfully installed, use the following commands:

1. To find the path to the Git executable:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop$ which git
    ```
    
2. To check the Git version:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop$ git --version
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698135203667/2f2ce100-5798-4a87-a8aa-ceac4eaa6156.png align="center")

## **Git Uninstallation:**

If you ever need to remove Git from your system, you can do so with the following command:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop$ sudo apt-get remove git
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698134962508/9699c042-6fdc-408b-99c4-809dab66dc6d.png align="center")

## Git Architecture Diagram

The below diagram illustrates the basic structure of a Git repository and its relationship with the working directory and the staging area. Here's a brief explanation:

* **Source Area(Working Area)**: This is where you create and edit your files. It's essentially your working directory, where you make changes to your project.
    
* **Stage(Staging Area)**: The staging area is like a checkpoint or a middle ground between your working directory and the local Git repository. It's where you prepare changes to be committed. You can think of it as a place where you decide which changes are ready to be saved as a snapshot in the Git repository.
    
* **.git (Local Repository)**: This is the heart of Git, where all the version history and metadata for your project are stored. It's essentially a database that keeps track of all changes, branches, commits, and more.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698136988093/241bda2a-f129-4e78-8aa4-5b9f9a858968.png align="center")

## CVCS VS DVCS

* **Centralized VCS (CVCS)**: In CVCS, there's a central repository that acts as a single point of truth for the entire project. Examples of CVCS include CVS, SVN, Clearcase, and Perforce. All team members commit their changes to this central repository.
    
* **Distributed VCS (DVCS)**: In DVCS, like Git, every developer has their own local repository that contains the entire project history. These repositories can be synchronized and share changes with others. Git is a prime example of a distributed version control system.
    

## **Basic Git Commands**

1. **git init**: This command creates a new Git repository. It's like saying, "Hey Git, this folder is where we'll track changes."
    
2. **git clone**: Use this to copy a repository from GitHub to your local computer. It's like getting a new toy to play with.
    
3. **git add**: Think of this as gathering all your code changes and getting them ready to be committed.
    
4. **git commit**: When you're happy with your changes, commit them. It's like saving your game progress.
    
5. **git push**: Send your committed changes back to GitHub. It's like sharing your cool new drawings with your friends.
    
6. **git pull**: Get the latest updates from GitHub to your local repository. It's like checking the mailbox for new letters.
    

## **Creating a Repository on GitHub**

1. Log in to your GitHub account.
    
2. Click the '+' sign in the top right corner and select 'New repository.'
    
3. Give your repository a name and description.
    
4. Choose public or private (public is like an open book, while private is like a diary with a lock).
    
5. Click 'Create repository.
    

## **Collaborating with Others**

Collaboration is the heart of GitHub. To work with others on a project:

1. Invite collaborators by going to 'Settings' &gt; 'Manage access.'
    
2. They can 'fork' your repository (make a copy) to their account.
    
3. They make changes and create a 'pull request' to suggest merging their changes into your project.
    
4. You can review their changes and, if everything's good, 'merge' them into your project.
    

That's the basics of Git and GitHub. You're now equipped to start your coding adventure. Just remember, it's okay to make mistakes; Git can always help you turn back the clock.

This is not the end more to come Join me in this series and lets connect on [LinkedIn](https://www.linkedin.com/in/theshubhamgour/)