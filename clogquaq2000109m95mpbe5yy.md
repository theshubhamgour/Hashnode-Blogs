---
title: "Day #10 :  Advance Git & GitHub for DevOps Engineers."
seoTitle: "Advance Git & GitHub for DevOps Engineers"
datePublished: Thu Nov 02 2023 05:26:04 GMT+0000 (Coordinated Universal Time)
cuid: clogquaq2000109m95mpbe5yy
slug: day-10-advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/EUzk9BIEq6M/upload/cca63f1fac909e673cf066121aa7fdef.jpeg
tags: git, devops, devops-articles

---

## Git Branching

Use a branch to isolate development work without affecting other branches in the repository. Each repository has one default branch and can have multiple other branches. You can merge a branch into another branch using a pull request.

Branches allow you to develop features, fix bugs, or safely experiment with new ideas in a contained area of your repository.

## Git Revert and Reset

Two commonly used tools that git users will encounter are those of git reset and git revert. The benefit of both of these commands is that you can use them to remove or edit changes you’ve made in the code in previous commits.

## Git Rebase and Merge

### What Is Git Rebase?

Git rebase is a command that lets users integrate changes from one branch to another, and the logs are modified once the action is complete. Git rebase was developed to overcome merging’s shortcomings, specifically regarding logs.

### What Is Git Merge?

Git merge is a command that allows developers to merge Git branches while the logs of commits on branches remain intact.

The merge wording can be confusing because we have two methods of merging branches and one of those ways is called “merge,” even though both procedures do essentially the same thing.

## Task : Merge Conflict Reslove

Add a text file called version01.txt inside the Devops/Git/ with “This is first feature of our application” written inside. This should be in a branch coming from `master`, \[hint try `git checkout -b dev`\], switch to `dev` branch ( Make sure your commit message will reflect as "Added new feature"). \[Hint use your knowledge of creating branches and Git commit command\]

* version01.txt should reflect at local repo first followed by Remote repo for review. \[Hint use your knowledge of Git push and git pull commands here\]
    

Add new commit in `dev` branch after adding below mentioned content in Devops/Git/version01.txt: While writing the file make sure you write these lines

* 1st line&gt;&gt; This is the bug fix in development branch
    
* Commit this with message “ Added feature2 in development branch”
    
* 2nd line&gt;&gt; This is gadbad code
    
* Commit this with message “ Added feature3 in development branch"
    
* 3rd line&gt;&gt; This feature will gadbad everything from now.
    
* Commit with message “ Added feature4 in development branch
    

Restore the file to a previous version where the content should be “This is the bug fix in development branch” \[Hint use git revert or reset according to your knowledge\]

---

**Task : Adding a Text File and Creating a New Branch**

1. Add a text file called `version01.txt` inside the `Devops/Git/` directory with the content "This is the first feature of our application."
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ touch version01.txt
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ echo "This is the first feature of our application" > version01.txt
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ cat version01.txt 
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698866241941/c28953f5-4637-4041-b02d-90fb036ad0bf.png align="center")
    
2. Commit the current change to Central repo
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ git add version01.txt 
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ git commit -m "Added new feature"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698866388898/e71d56b4-f35c-43ac-a4b2-e7be7f022c35.png align="center")
    
3. Create a new branch named "dev" from the "master" branch:
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ git checkout -b dev
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698867009071/cbb7d531-c1dc-48e4-b3a3-77fedd97f559.png align="center")
    
4. Commit the changes with the message "Added new feature."
    
    ```plaintext
    
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ echo "This is the bug fix in development branch" > version01.txt 
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ git commit -am "Added feature2 in development branch"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698901511034/a76bed8a-8ade-4ef7-8f97-bc89b10f07f1.png align="center")
    
5. Add the text in the second line and commit it with the defined commit message
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ echo "This is gadbad code" >> version01.txt 
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ git commit -am "Added feature3 in development branch"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698901638226/9b620365-5e0b-4719-8c76-672b69313e23.png align="center")
    
    ```plaintext
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ echo "This feature will gadbad everything from now." >> version01.txt 
    ubuntu@ip-172-31-8-95:~/DevOps/Git$ git commit -am "Added feature4 in development branch"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698901711346/c399373a-10d1-4603-b4fb-fe2724cbb4c6.png align="center")
    
6. Check the content of the file now using cat command
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698901778903/67c37664-ee73-499b-8074-66aad699af72.png align="center")
    

To restore the file to a previous version, you can use `git reset`:

Use the following command to reset the file to a previous version where the content is "This is the bug fix in the development branch":

```plaintext
 ubuntu@ip-172-31-8-95:~/DevOps/Git$ git reset --hard HEAD~3
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698902331404/77b3d1fd-b792-4562-9c53-4d0e0c8c1825.png align="center")

## Conclusion

Here we conclude the Day 10 task from #90DaysOfDevOps