---
title: "Git and GitHub Made Simple: A Complete Guide - Part 2"
seoTitle: "Setting Up Your GitHub Remote Repository"
seoDescription: "Learn how to create and configure a remote repository on GitHub. Manage your code with ease. Your guide to effective collaboration and version control."
datePublished: Tue Oct 24 2023 18:30:12 GMT+0000 (Coordinated Universal Time)
cuid: clo4nw1ii000f08mndxqsbtf9
slug: git-and-github-made-simple-a-complete-guide-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/KPAQpJYzH0Y/upload/31bd070e9a0278fab2ea9518f2542356.jpeg
tags: github, git, devops, devops-articles

---

In the previous part, we began our journey into the world of Git and GitHub by creating a local Git environment. Now, let's take the next step and set up our remote repository on GitHub.

### **Why a Remote Repository?**

A remote repository serves as the centralized hub where your code is securely stored and shared with collaborators. It's like the vault for your precious project, accessible from anywhere with an internet connection.

### **Creating a GitHub Account**

If you haven't already, creating a GitHub account is your first step. It's a straightforward process, and it's free! Visit [GitHub](https://github.com/) and sign up.

### **Logging In and Creating a New Repository**

Once you're logged into your GitHub account, you'll be on your dashboard. This is your GitHub command center, where you manage your repositories and activities.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698140308095/0cde9137-1311-488e-b5f3-49b51c13a138.png align="center")

You'll be taken to the repository creation page. Here's where you configure your repository:

1. **Name Your Repository**: Choose a name that reflects your project.
    
2. **Access Control**: Decide if your repository should be public (open to the world) or private (restricted to you and collaborators). Note that private repositories might require a paid plan.
    
3. **Description**: Add a short description to help you and others understand the project's purpose.
    
4. **Other Options**: GitHub offers various other settings you can configure. Explore these based on your project's needs.
    

Finally, click on "Create repository."

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698140440559/0acb7e78-d0fb-4414-8712-43a251ef7920.png align="center")

### **Copying Your Repository URL**

After creating your repository, GitHub will display the repository's URL, which should look something like this: [https://github.com/theshubhamgour/git-hash.git](https://github.com/theshubhamgour/git-hash.git). You'll need this URL to link your local Git repository with the remote one.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698140616357/84eb2e43-8693-4155-8678-4e8f51431f37.png align="center")

### **Cloning the Repository**

With your repository URL in hand, you can now clone your repository to your local machine. This is like creating a synchronized copy of your project. In your terminal, navigate to the directory where you want your project to be stored and run:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop$ git clone https://github.com/theshubhamgour/git-hash.git
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143175295/71c14ab8-e1ee-4a1e-bd8f-b45130aff38b.png align="center")

This command establishes the connection between your local and remote repositories.

### **Navigating to Your Repository**

Use the `cd` command to enter your local repository:

```plaintext
theshubhamgour@ubuntuM1:~/Desktop$ cd git-hash/
```

You're now ready to add your code to the repository. Create some sample code or files that you want to track and share.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143273368/ae776fc3-dc0d-493a-ac8d-a34032350689.png align="center")

### **Adding, Committing, and Pushing Code**

With your code ready, it's time to use Git to manage it. The basic workflow involves:

1. Checking the status of your changes:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git status
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143344345/0bb95f94-0a8b-4e4e-aaf2-a5bba94a9e32.png align="center")
    
2. Staging your changes (deciding what to commit):
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git add file1.txt 
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git status
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143398103/af9019d6-60dd-490c-b377-e78a19e2956c.png align="center")
    
3. Or, to stage all changes:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git add .
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git status
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143432556/3bfbc9bf-9cf5-4940-98ed-0e7650228795.png align="center")
    
4. Committing your changes with a descriptive message:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git commit -m "Added ten sample test files"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143486791/8c2ebfa7-c669-4bf1-b396-71070157531b.png align="center")
    
5. Finally, pushing your changes to the remote repository:
    
    ```plaintext
    theshubhamgour@ubuntuM1:~/Desktop/git-hash$ git push
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143541344/2ad90aac-4e86-4757-842c-57dcefe15ffd.png align="center")

At this point, you might be prompted to enter your GitHub username and password. Once that's done, your code will be safely stored in your remote repository on GitHub.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143584682/725ce76b-900f-4371-883f-6e549c6fb8a4.png align="center")

### **Git Commit Structure**

Each Git commit has a structure that includes a commit ID (a unique identifier), user/email, timestamp, and a commit message. This structure makes it easy to track and manage changes.

### **SHA, Version, Revision, Commit ID**

You might also hear terms like SHA, version, revision, or commit ID. These are all different ways to refer to the unique identifier associated with a particular commit. They help pinpoint a specific state of your project's history.

### **Setting Up Mandatory Configurations**

Before you commit to your local repository, it's a good practice to set up your Git configurations:

```plaintext
$ git config --global user.name "Your Name"
$ git config --global user.email "youremail@example.com"
```

You can check your configurations with:

```plaintext
bashCopy code$ git config --list
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143709429/d2ed56c9-0d1e-44bd-9fcc-fcac73afb69e.png align="center")

These configurations help Git identify you and make your interactions smoother.

**Git stores all configurations in below file**

```plaintext
theshubhamgour@ubuntuM1:~/Desktop/git-hash$ cat /home/theshubhamgour/.gitconfig
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698143857250/cc711962-a553-4b82-a081-1242f51a0298.png align="center")

### **Conclusion**

With your remote repository on GitHub now set up, you're well on your way to efficiently manage and collaborate on your coding projects. Stay tuned for the next part, where we'll dive deeper into working with remote repositories, branches, and pull requests, taking your Git and GitHub skills to the next level.

This is not the end more to come Join me in this series and lets connect on [**LinkedIn**](https://www.linkedin.com/in/theshubhamgour/)