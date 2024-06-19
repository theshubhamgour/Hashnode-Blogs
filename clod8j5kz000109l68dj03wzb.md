---
title: "Git and Github Made Simple : The Final Part"
seoTitle: "Git and Github Made Simple : The Final Part"
seoDescription: "Merging in Git is a powerful way to bring changes from one branch into another. learn in the blog for more"
datePublished: Mon Oct 30 2023 18:30:12 GMT+0000 (Coordinated Universal Time)
cuid: clod8j5kz000109l68dj03wzb
slug: git-and-github-made-simple-the-final-part
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/HLQDfaJUTVI/upload/3ff573eb528109a6d9c4ecc598072d0b.jpeg
tags: github, git, devops, devops-articles

---

**A Guide to Resolving Git Merges with Conflicts**

Merging in Git is a powerful way to bring changes from one branch into another. However, conflicts can arise when two branches modify the same part of a file differently. In this guide, we'll walk through the steps to resolve Git merges with conflicts effectively.

## **1\. List All Branches**

Before you begin, list all the branches to get a clear view of what you're working with.

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-demo$ git branch
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698248150393/25ce39d1-fec8-4f1a-a35a-62e263c4c6c4.png align="center")

## **2\. Create a New Branch**

To initiate the conflict, create a new branch where you'll make changes. Let's call it `dev_1.2.3`.

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-demo$ git checkout -b dev_1.2.3
```

## **3\. Set the Stage**

To create a conflict, select a file that's common to both `main` and `dev_1.2.3` branches. For this example, we'll use `index.html`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698248908899/0ff5e457-2174-419e-9cd1-b06e19bd878f.png align="center")

In `main` (`index.html`):

```plaintext
Line 6: ->   <title>Webinar Booking</title>
```

In `dev_1.2.3` (`index.html`):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698249630933/7c0d3bc3-b757-4e20-82b6-6019035a2bfe.png align="center")

```plaintext
 Line 6: ->Changes are here testing conflict
```

## **4\. Merge the Changes**

With the conflict-ready branches in place, switch to the target branch where you want to merge the changes. In our case, it's `main`.

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-demo$ git checkout main
```

Now, merge the changes from `dev_1.2.3` into `master`.

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-demo$ git merge dev_1.2.3 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698249763870/81c27132-0fcf-44ea-bac0-e2952cfbd794.png align="center")

## **5\. Detecting Conflicts**

After the merge command, use `git status` to identify files with conflicts.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698249821093/b86a2322-2799-4331-9435-2a9b5f0648e1.png align="center")

## **6\. Resolve the Conflict**

Open the conflicted file, typically identified by conflict markers, and manually select the correct content. Remove the conflict markers.

**Use Vim or any editor to fix the conflicts**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698249911065/c816b15e-df22-44c4-a439-7da014fac7c7.png align="center")

## **7\. Commit Your Changes**

After resolving the conflict, stage the changes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698250061716/a6787c02-8194-444a-bc55-229fd7d34c09.png align="center")

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-demo$ git add .
```

Commit your changes to complete the merge.

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-demo$ git commit -m "Resolve merge conflict"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698250162837/99b4834e-a3ea-4bd6-b0c0-c356442b949c.png align="center")

## **8\. Push to Remote**

Finally, push the merged changes to the remote repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698250211012/d7d4d796-c48b-4097-810f-369c49d2c116.png align="center")

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-demo$ git push
```

And that's it! You've successfully resolved a Git merge conflict. This process ensures that your code stays clean and coherent, even when multiple contributors are working on the same files.

With this, we conclude our Git and Github Journey thanks for being alongside .