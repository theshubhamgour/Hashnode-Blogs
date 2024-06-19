---
title: "Git and GitHub Made Simple: A Complete Guide - Part 7"
seoTitle: "Mastering Git Branches: A DevOps Guide"
seoDescription: "Explore the world of Git branches and understand branching strategies in this comprehensive guide. Learn to keep your codebase clean and organized."
datePublished: Sun Oct 29 2023 18:30:13 GMT+0000 (Coordinated Universal Time)
cuid: clobt3azq000009jn240ahuj7
slug: git-and-github-made-simple-a-complete-guide-part-7
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/842ofHC6MaI/upload/13a947add26ed22bb6426b13f8c674ec.jpeg
tags: github, git, devops, devops-articles

---

Welcome to Phase 7 of our DevOps journey. Today, we're diving into the world of branching in Git.

## **What is a branch?**

A branch is like a parallel universe for your code. It allows you to work on new features or bug fixes without affecting the main codebase\[Master or Main Branch\]. Think of it as a sandbox for your ideas.

## **Why and When Do We Create a Branch?**

Branching is a fundamental concept in Git, allowing multiple developers to work together efficiently. It's your way of keeping your code organized, clean, and ready for whatever the future holds.

Branches are handy when you want to:

* Develop a new feature
    
* Fix a bug
    
* Experiment with new ideas
    
* Keep your main codebase clean
    

## **Listing All Branches**

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git branch
```

This command lists all the local branches in your repository.

## **Creating a New Branch**

The branch can be created by the following command**\-** `git branch new_branch_name`

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git branch release-1.1
```

Create a new branch with the given name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698240089326/e9ac40c1-271c-418b-b26d-d82712d7a67a.png align="center")

## **Listing All Remote Branches**

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git branch -r
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698240123553/3d4460e9-1d31-43a2-a146-7a18932fed37.png align="center")

List all the branches on your remote repository.

## **Switching to a New Branch**

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git checkout release-1.1 
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git branch
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698240173679/0a5f9e94-c4d0-4746-8659-aed9b8e7996e.png align="center")

Switch to the branch you want to work on.

## **Creating and Switching to a New Branch in One Go**

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git checkout -b release-1.2
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git branch
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698240314397/729e7d4b-8130-42ad-9eae-5a1ff8a120d1.png align="center")

This one-liner creates and switches to a new branch. Is Handy, right?

## **First Push of a Newly Created Branch to Remote Repo**

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git remote add git-hash https://github.com/theshubhamgour/git-hash.git
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git push origin release-1.2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698240480026/a2753483-0ada-4187-97ed-801ff916a468.png align="center")

These commands add a remote repository and push your new branch to it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698240527333/d5ac640f-02d7-4576-9c56-89b544383b85.png align="center")

## **Merging Files from Source -&gt; Target Branch**

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git merge release-1.2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698240956134/93b88eaa-ec6c-4f3c-b061-d60e252c5c1f.png align="center")

Merge changes from the source branch to your target branch.

## **Understanding HEAD**

HEAD is like your GPS in Git. It always points to the latest commit in your repository. It helps you navigate through your project's history.

HEAD is a pointer in git which

\- Always points to the latest commit in the repository

\- Always points to tip of the current reposiotory

\- Always points to parent of the next commit

So go ahead, create branches, experiment, and keep your codebase in tip-top shape. Your DevOps journey continues, and you're doing great!

And as i always say - This is not the end more to come Join me in this series and let's connect on [**LinkedIn**](https://www.linkedin.com/in/theshubhamgour/)

#DevOps #Git #Branching #VersionControl #HappyCoding