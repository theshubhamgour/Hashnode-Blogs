---
title: "Day #11 : Advance Git & GitHub for DevOps Engineers: Part-2"
datePublished: Tue Nov 14 2023 02:34:19 GMT+0000 (Coordinated Universal Time)
cuid: cloxpzn3g000409jy8qar25xg
slug: day-11-advance-git-github-for-devops-engineers-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/zwsHjakE_iI/upload/03adfc704865f3a0df3e3238b5d12c6c.jpeg
tags: github, git, devops

---

## Git Stash:

Git stash is a command that allows you to temporarily save changes you have made in your working directory, without committing them. This is useful when you need to switch to a different branch to work on something else, but you don't want to commit the changes you've made in your current branch yet.

To use Git stash, you first create a new branch and make some changes to it. Then you can use the command git stash to save those changes. This will remove the changes from your working directory and record them in a new stash. You can apply these changes later. git stash list command shows the list of stashed changes.

You can also use git stash drop to delete a stash and git stash clear to delete all the stashes.

## Cherry-pick:

Git cherry-pick is a command that allows you to select specific commits from one branch and apply them to another. This can be useful when you want to selectively apply changes that were made in one branch to another.

To use git cherry-pick, you first create two new branches and make some commits to them. Then you use git cherry-pick &lt;commit\_hash&gt; command to select the specific commits from one branch and apply them to the other.

## Resolving Conflicts:

Conflicts can occur when you merge or rebase branches that have diverged, and you need to manually resolve the conflicts before git can proceed with the merge/rebase. git status command shows the files that have conflicts, git diff command shows the difference between the conflicting versions and git add command is used to add the resolved files.

# [Task-01](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day11/README.md#task-01)

* Create a new branch and make some changes to it.
    
* Use git stash to save the changes without committing them.
    
* Switch to a different branch, make some changes and commit them.
    
* Use git stash pop to bring the changes back and apply them on top of the new commits.
    
* Create a new branch and make some changes to it:
    
    ```plaintext
    git checkout -b new-branch
    # Make your changes
    git add .
    git commit -m "Changes in new-branch"
    ```
    
* Use git stash to save the changes without committing them:
    
    ```plaintext
    git stash
    ```
    
* Switch to a different branch, make some changes, and commit them:
    
    ```plaintext
    git checkout different-branch
    # Make your changes
    git add .
    git commit -m "Changes in different-branch"
    ```
    
* Use git stash pop to bring the changes back and apply them on top of the new commits:
    
    ```plaintext
    git stash pop
    ```
    

# [Task-02](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day11/README.md#task-02)

* In version01.txt of development branch add below lines after “This is the bug fix in development branch” that you added in Day10 and reverted to this commit.
    
* Line2&gt;&gt; After bug fixing, this is the new feature with minor alteration”
    
    Commit this with message “ Added feature2.1 in development branch”
    
* Line3&gt;&gt; This is the advancement of previous feature
    
    Commit this with message “ Added feature2.2 in development branch”
    
* Line4&gt;&gt; Feature 2 is completed and ready for release
    
    Commit this with message “ Feature2 completed”
    
* All these commits messages should be reflected in Production branch too which will come out from Master branch (Hint: try rebase).
    

1. In version01.txt of development branch, add the specified lines:
    
    ```plaintext
    git checkout development
    # Edit version01.txt as specified
    git add version01.txt
    git commit -m "Added feature2.1 in development branch"
    ```
    
2. Add Line3 and commit:
    
    ```plaintext
    # Edit version01.txt as specified
    git add version01.txt
    git commit -m "Added feature2.2 in development branch"
    ```
    
3. Add Line4 and commit:
    
    ```plaintext
    # Edit version01.txt as specified
    git add version01.txt
    git commit -m "Feature2 completed"
    ```
    
4. Reflect these commits in the Production branch using rebase:
    
    ```plaintext
    git checkout production
    git rebase development
    ```
    

# [Task-03](https://github.com/theshubhamgour/90DaysOfDevOps/blob/master/2023/day11/README.md#task-03)

* In Production branch Cherry pick Commit “Added feature2.2 in development branch” and added below lines in it:
    
* Line to be added after Line3&gt;&gt; This is the advancement of previous feature
    
* Line4&gt;&gt;Added few more changes to make it more optimized.
    
* Commit: Optimized the feature
    

* After adding the lines and committing "Optimized the feature," let's continue:
    
    ```plaintext
    # Continue from the previous steps
    ```
    
* Now, you need to rebase the Production branch to reflect the changes made in the Development branch:
    
    ```plaintext
    git checkout production
    git rebase development
    ```
    
    If there are conflicts, resolve them and continue the rebase process.
    
* Once the rebase is completed, you may need to force-push the changes to the remote repository (be cautious with force-push as it rewrites history):
    
    ```plaintext
    git push origin production --force
    ```
    

This ensures that the Production branch reflects the changes from the Development branch, including the cherry-picked commit and the additional optimizations. If you encounter conflicts during the rebase, Git will guide you through resolving them.

Remember to exercise caution when force-pushing, especially if the branch is shared with others. If others are working with the Production branch, it's better to coordinate and communicate the changes to avoid conflicts.