---
title: "Git and GitHub Made Simple: A Complete Guide - Part 6"
seoTitle: "Github Undo Changes"
datePublished: Sat Oct 28 2023 18:30:12 GMT+0000 (Coordinated Universal Time)
cuid: cloadng2e00000amegzefhks1
slug: git-and-github-made-simple-a-complete-guide-part-6
tags: github, git, devops, devops-articles

---

In the adventurous world of DevOps, there's no doubt that you'll occasionally find yourself making changes you'd like to undo. That's where Git comes to the rescue with its magical "undo" abilities.

## **Git Commands for Undoing Changes**

### **1.** `git checkout <filename>`

Sometimes, you accidentally make changes to a file that you'd like to revert to its previous state. The `git checkout` command helps you do just that.

Example:

```plaintext
$ git checkout myFile.js
```

### **2.** `git reset HEAD <filename>`

If you've staged changes that you'd like to unstage, the `git reset` command can help. It moves changes from the staging area back to your working directory.

Example:

```plaintext
$ git reset HEAD myFile.js
```

### **3.** `git reset --mixed HEAD~1`

The `--mixed` option is the default mode of `git reset`. It unstages changes and moves them back to the working directory. Using `HEAD~1` indicates you want to undo the last commit.

Example:

```plaintext
$ git reset --mixed HEAD~1
```

### **4.** `git reset --soft HEAD~1`

This command moves changes from the latest commit back to the staging area while keeping them in your working directory. It's useful when you want to make additional changes before committing.

Example:

```plaintext
$ git reset --soft HEAD~1
```

### **5.** `git reset --hard HEAD~1`

The most powerful option, `--hard`, discards all changes, staging, and even working directory changes. Use it carefully as it's irreversible.

Example:

```plaintext
$ git reset --hard HEAD~1
```

## **Viewing Commit Differences**

### **6.** `git log` and `git show`

To view differences between commits, you can use `git log` to list all commits and then `git show` with a commit's SHA (SHA-VALUE) to see the details.

Example:

```plaintext
$ git log
$ git show SHA-VALUE
```

## **Listing Files Committed in a Revision**

### **7.** `git diff-tree`

This command allows you to list files that were committed as part of a specific revision using its SHA (SHA-VALUE).

Example:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git log -n1
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git diff-tree --no-commit-id --name-only -r 636fd550552b399fd0ee427f6f1f5de107eb65c3
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698222446426/cac61b0e-058d-47a3-bed4-0b12bc42e2a1.png align="center")

Undoing changes in Git is an essential skill that can save you from mishaps. With these commands in your toolkit, you're well-equipped to navigate the occasional misstep on your DevOps journey. Happy coding and undoing!

## Conclusion

We've explored how to undo changes in Git. The ability to revert, unstaged, or even obliterate changes is a valuable skill for any DevOps enthusiast. Now, you're ready to tackle Git with confidence! 🚀 #DevOps #GitMagic