---
title: "Day #9 : Deep Dive in Git & GitHub for DevOps Engineers."
seoTitle: "Mastering Git and GitHub: A Developer's Guide"
seoDescription: "Discover the power of Git and GitHub, the essential tools for modern developers. Learn version control, collaboration, and more."
datePublished: Mon Oct 30 2023 08:32:10 GMT+0000 (Coordinated Universal Time)
cuid: clocn6254000509medvsl4uw4
slug: day-9-deep-dive-in-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/CPvnvwfBU_o/upload/d4e248cf7b056aa6408761a7fd99b683.jpeg
tags: github, git, devops, devops-articles

---

Welcome back to our DevOps journey! Today, we're going to take a deep dive into Git and GitHub, two of the most essential tools for modern software development and collaboration. We'll answer some key questions and provide step-by-step guidance on using these tools effectively.

### **What is Git and Why is it Important?**

**Git** is a distributed version control system that allows developers to track changes to their codebase. It's vital for a few reasons:

1. **Version Control**: Git keeps track of every change made to a project, creating a history that enables you to revisit past states of your code.
    
2. **Collaboration**: Git facilitates team collaboration by allowing multiple developers to work on a project simultaneously.
    
3. **Backup and Recovery**: It provides a safety net. If something goes wrong or you lose your code, Git allows you to recover previous versions.
    

**Branching and Merging**: Git enables the creation of branches for developing features, and these branches can later be merged back into the main project.

### What is the difference Between the Main Branch and the Master Branch??

In Git, the **main branch** and the **master branch** essentially refer to the same thing: the default branch of your repository. Historically, "master" was used, but many projects are now switching to "main" due to potential connotations of the term "master." The choice between the two largely depends on your project's naming convention, and both are widely accepted.

### Can you explain the difference between Git and GitHub?

**Git** is the version control system itself, while **GitHub** is a web-based platform for hosting Git repositories. Think of Git as the engine, and GitHub as the car that houses and drives it. You use Git to manage your source code, and you can use GitHub to store, collaborate on, and share your Git repositories.

### How do you create a new repository on GitHub?

1. **Log In to Your GitHub Account:** Open your web browser and go to [GitHub](https://github.com/). Log in to your GitHub account if you haven't already.
    
2. **Access Your Dashboard:** Once you're logged in, you'll land on your GitHub dashboard. You can access it by clicking on the GitHub logo in the top left corner.
    
3. **Create a New Repository:** On your dashboard, you'll find a green button labeled "New" in the top right corner. Click on it to start creating a new repository.
    
4. **Set Up Your New Repository:** You'll be taken to a new page where you can fill in the details for your repository:
    
    * **Repository Name:** Choose a unique and descriptive name for your repository.
        
    * **Description (Optional):** Add a brief description of your repository.
        
    * **Visibility:** You can choose between Public and Private. Public repositories are visible to everyone, while Private repositories are only visible to you and collaborators.
        
    * **Initialize this repository with:** You can choose to add a README file, a .gitignore file, or a license. These are optional but can be helpful.
        

### What is the difference between local & remote repositories? How to connect local to remote?

The difference between a local repository and a remote repository lies in their location and purpose:

1. **Local Repository:**
    
    * **Location:** Your local repository is stored on your computer, specifically in a directory where you're working on a project.
        
    * **Purpose:** It serves as your working area, allowing you to make changes to files, track those changes, create branches, and test new features. A local repository is where you perform most of your development tasks.
        
2. **Remote Repository:**
    
    * **Location:** A remote repository is hosted on a remote server, typically on a platform like GitHub, GitLab, or Bitbucket. It's not on your computer but on a server accessible via the internet.
        
    * **Purpose:** Remote repositories are used for collaboration and backup. They enable multiple developers to work together on a project and provide a secure and centralized location to store your project's code. They also serve as a backup in case your local repository is lost or compromised.
        

**Connecting Local to Remote Repository:**

To connect your local repository to a remote repository, typically hosted on a platform like GitHub, follow these steps:

1. **Create a Remote Repository:**
    
    * Log in to your GitHub account (or the platform of your choice).
        
    * Create a new repository on the platform. This will be your remote repository.
        
2. **Initialize Your Local Repository:**
    
    * If you haven't already, initialize a Git repository in your local project folder. You can do this using the `git init` command.
        
3. **Link the Local Repository to the Remote Repository:**
    
    * Use the `git remote add` command to link your local repository to the remote repository. Replace `<repository_url>` with the URL of your remote repository on GitHub.
        
    * For example:
        
        ```plaintext
        git remote add origin <repository_url>
        ```
        
4. **Set the Default Branch:**
    
    * The default branch name has changed from "master" to "main" on many platforms to promote inclusive language. Use the following commands to update your local repository:
        
        ```plaintext
        git branch -M main
        ```
        
5. **Push Local Commits to Remote Repository:**
    
    * After linking, you can push your local commits to the remote repository using the `git push` command:
        
        ```plaintext
        git push -u origin main
        ```
        
    
    The `-u` option is used to set up a tracking relationship. After this, you can simply use `git push` and `git pull` without specifying the remote and branch names.
    

Your local repository is now connected to the remote repository, and you can easily collaborate with others and keep your code safe and accessible in the remote repository.

## Task 1: Set your user name and email address, which will be associated with your commits.

1. **Open a Terminal (Linux/macOS) or Command Prompt (Windows):**
    
    * On Windows, you can use the Git Bash terminal if you've installed Git. You can also use the Windows Command Prompt if Git is included in your PATH.
        
2. **Set Your Username and Email:**
    
    Use the following command to set your Git username and Git email:
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~$ git config --global user.name "Shubham Gour"
    ubuntu@ip-172-31-8-95:~$ git config --global user.email "iamtheshubhamgour@gmail.com"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698576385486/135bfbda-4ff2-4387-9c1f-b48f2d0b9c6f.png align="center")
    
3. **Verify Your Settings:**
    

To verify that your settings have been applied, you can use the following command to display your Git configuration:

```plaintext
ubuntu@ip-172-31-8-95:~$ git config --list
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698576423243/5c8a9f06-5407-4aaf-9adc-17bf43bf0643.png align="center")

## Task 2 : Repository Operations

* Create a repository named "Devops" on GitHub
    
* Connect your local repository to the repository on GitHub.
    
* Create a new file in Devops/Git/Day-02.txt & add some content to it
    
* Push your local commits to the repository on GitHub
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698576700834/2262f59b-a172-4612-abb3-d320e256f538.png align="center")

Write the Repository name as "DevOps" and Click on Create Repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698576916138/c092f042-d555-4719-9903-d8c02f5db343.png align="center")

Now go to your local terminal create a Directory named "DevOps" which we will connect with Github later.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698577321668/de648032-8e95-4060-9066-f2a2013562f7.png align="center")

In our local system we have created a Directory named Devops within it we have Git and a file named Day-02.txt as per the task.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698577507905/ea45d673-bf22-4644-98e2-3ad40122bb16.png align="center")

Now we initialised the local repository and marked the changes to the staging area.

It time to connect the git repo with the local for that we need to fire the below command

```plaintext
shubhamgour@Shubhams-MacBook-Air DevOps % git remote add DevOps https://github.com/theshubhamgour/DevOps.git
```

Now let's push the changes to the Central repo, we will execute the below command

```plaintext
shubhamgour@Shubhams-MacBook-Air DevOps % git push --all  
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698577835481/ed5531f8-efa5-4816-b36b-769a8b646359.png align="center")

Now when you check your Github account you will get the files present, live on the central

## Conclusion

In summary, Task-1 ensured your identity is associated with your Git commits, a fundamental step in version control. Task-2, creating and connecting a "Devops" repository on GitHub, adding a new file, and pushing local commits, demonstrates the practical application of Git and GitHub for efficient code management and collaboration in your DevOps journey. Keep up the great work, and you're well on your way to becoming a proficient DevOps engineer! 🌟👨‍💻 #DevOps #Git #GitHub #EfficientCoding