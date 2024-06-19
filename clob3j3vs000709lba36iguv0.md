---
title: "Day #8 Basic Git & GitHub for DevOps Engineers"
seoTitle: "Basic Git & GitHub for DevOps Engineers"
datePublished: Sun Oct 29 2023 06:34:40 GMT+0000 (Coordinated Universal Time)
cuid: clob3j3vs000709lba36iguv0
slug: day-8-basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/NWmcp5fE_4M/upload/b5fa6316a3c7c21426a9ee6337f8500e.jpeg
tags: github, git, devops, devops-articles

---

## [What is Git?](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day08/README.md#what-is-git)

Git is a version control system that allows you to track changes to files and coordinate work on those files among multiple people. It is commonly used for software development, but it can be used to track changes to any set of files.

With Git, you can keep a record of who made changes to what part of a file, and you can revert back to earlier versions of the file if needed. Git also makes it easy to collaborate with others, as you can share changes and merge the changes made by different people into a single version of a file.

## [What is Github?](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day08/README.md#what-is-github)

GitHub is a web-based platform that provides hosting for version control using Git. It is a subsidiary of Microsoft, and it offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. GitHub is a very popular platform for developers to share and collaborate on projects, and it is also used for hosting open-source projects.

## [What is Version Control? How many types of version controls we have?](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day08/README.md#what-is-version-control-how-many-types-of-version-controls-we-have)

Version control is a system that tracks changes to a file or set of files over time so that you can recall specific versions later. It allows you to revert files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more.

There are two main types of version control systems: centralized version control systems and distributed version control systems.

1. A centralized version control system (CVCS) uses a central server to store all the versions of a project's files. Developers "check out" files from the central server, make changes, and then "check in" the updated files. Examples of CVCS include Subversion and Perforce.
    
2. A distributed version control system (DVCS) allows developers to "clone" an entire repository, including the entire version history of the project. This means that they have a complete local copy of the repository, including all branches and past versions. Developers can work independently and then later merge their changes back into the main repository. Examples of DVCS include Git, Mercurial, and Darcs.
    

## [Why we use distributed version control over centralized version control?](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day08/README.md#why-we-use-distributed-version-control-over-centralized-version-control)

1. Better collaboration: In a DVCS, every developer has a full copy of the repository, including the entire history of all changes. This makes it easier for developers to work together, as they don't have to constantly communicate with a central server to commit their changes or to see the changes made by others.
    
2. Improved speed: Because developers have a local copy of the repository, they can commit their changes and perform other version control actions faster, as they don't have to communicate with a central server.
    
3. Greater flexibility: With a DVCS, developers can work offline and commit their changes later when they do have an internet connection. They can also choose to share their changes with only a subset of the team, rather than pushing all of their changes to a central server.
    
4. Enhanced security: In a DVCS, the repository history is stored on multiple servers and computers, which makes it more resistant to data loss. If the central server in a CVCS goes down or the repository becomes corrupted, it can be difficult to recover the lost data.
    

Overall, the decentralized nature of a DVCS allows for greater collaboration, flexibility, and security, making it a popular choice for many teams.

## Exercises

1. Create a new repository on GitHub and clone it to your local machine
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698560842565/8aa4fd34-3aa6-421b-a013-80d1931da983.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698560884621/dc8c6be7-dfbb-4946-9651-66babbc554a2.png align="center")
    
2. Make some changes to a file in the repository and commit them to the repository using Git
    
    ```plaintext
    shubhamgour@192 Desktop % git clone https://github.com/theshubhamgour/github-test-repo.git
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698560926652/0d84abe4-c3d0-43c8-91e6-743e50dc0880.png align="center")
    
    Adding the changes:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698561058096/7db14a86-0e2d-409f-8ccc-e32703b3b0a5.png align="center")
    
3. Push the changes back to the repository on GitHub :
    
    ```plaintext
    shubhamgour@192 github-test-repo % git push
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698561117701/194f3b56-95e8-4abb-8429-e1f18ac66ae0.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698561156009/abaf8abf-18e8-44db-86cf-5fbbe4bdb7bd.png align="center")
    
    That was all for the day! See you in the next one.