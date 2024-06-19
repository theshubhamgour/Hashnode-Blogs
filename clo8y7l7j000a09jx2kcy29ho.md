---
title: "Git and GitHub Made Simple: A Complete Guide - Part 5"
seoTitle: "Mastering Git: Essential Commands and Examples"
seoDescription: "Explore essential Git commands and their usage with clear examples. Level up your Git skills and streamline your version control workflows."
datePublished: Fri Oct 27 2023 18:30:12 GMT+0000 (Coordinated Universal Time)
cuid: clo8y7l7j000a09jx2kcy29ho
slug: git-and-github-made-simple-a-complete-guide-part-5
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/ZV_64LdGoao/upload/e5eeedf3e513317fdbc2cd8ec600ee52.jpeg
tags: github, git, devops, devops-articles

---

Welcome to the next phase of your Git journey! In Phase 5, we're diving deeper into essential Git commands that will make you a Git pro.

## Log Commands

**Command 1:** `git status`

Before making any moves, it's always a good idea to check the lay of the land. `git status` is your friend. It tells you what's happening in your Git world.

Example:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698215839975/4087a14b-5188-475e-b947-08d2783fd145.png align="center")

**Command 2:** `git diff`

Need to see the differences in your files? `git diff` is the tool. Whether you want to compare your working directory with the last commit or check the changes in a specific file, this command has you covered.

Example:

```plaintext
git diff <filename>
```

**Command 3:** `git diff --staged`

So, you've staged some changes, but you're not quite ready to commit them. Use `git diff --staged` to review what's about to be committed. It's like a final check before sealing the deal.

Example:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git diff --staged
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698216158817/8c22d5a2-58d4-4466-bedb-6bada83a1b2e.png align="center")

**Command 4:** `git diff commitA..commitB`

Ever wondered how two versions of a file differ? This command helps you compare them using their commit IDs. Understanding the changes between two specific points in time can be incredibly useful.

Example:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log file1.txt
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git diff d98f65..d0d054
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698216256250/bd7e492a-6a8b-4bb4-af69-d9279bd568c9.png align="center")

### **Deleting a File**

Deleting a file in Git is a two-step process. First, use `git rm <filename>` to remove it. Then, commit your change with a descriptive comment, and finally, push the update to your repository.

Example:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git rm file10.txt 
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git commit -m "Deleted file10.txt - NA Cached"
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git push
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698216737378/efe1e110-3451-4dea-aa94-50d2452ae280.png align="center")

### **Renaming a File/Folder**

Change file or folder names seamlessly with `git mv`. This command simplifies renaming while keeping the history intact. After renaming, commit the change and push it to your repository.

Example:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git mv git-file file10.txt
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git commit -m "Renamed: git-file -> file10.txt"
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git push
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698216854840/53375302-38e0-47fd-83aa-0fb8d81b5923.png align="center")

### **Carry History for a New File**

Sometimes, you'll want to carry over the history of an old file to a new one. Use `git log --follow <new-name>` to do just that. This can be especially handy when you're restructuring your project.

Example:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log --follow file10.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698217015042/dd512105-9be3-41f1-9f52-c8f860dd435c.png align="center")

With these commands and examples, you're well-equipped to navigate the Git universe with confidence. Git empowers you to track changes, collaborate effectively, and ensure your project's history is crystal clear.

Stay tuned for more Git wisdom in the next phase of our Git adventure! 🌟👨‍💻

This is not the end more to come Join me in this series and lets connect on [**LinkedIn**](https://www.linkedin.com/in/theshubhamgour/)

#Git #VersionControl #Coding #DevOps #SimplifyTech