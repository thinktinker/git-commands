### A. Steps to initialise a local repository, followed by adding, committing and pushing to a remote repository on Github
-------

1. Create a remote repository on Github.
<br>

2. Set up a local project folder, and initialise the folder to be tracked using the command:
    ```
    git init
    ```
<br>

3. After working on the file(s), check the folder's status for untracked AND/OR modified files:
    ```
    git status
    ```
<br>

4. For any file(s) to be staged in the local project folder, use the command(s):
    ```
    git add file1.extension
    git add file2.extension
    git add folder_name/
    ```
    > **TIP:** 
    > To stage **ALL** local files, use a single command: **`git add .`**

<br>

5. Next, commit the files and/or folders in the local repository for upload to the remote repository Github:
    ```
    git commit -m "meaningful commit message"
    ```
<br>

6.	To check the commit log(s) / commit history, enter the command:
    ```
    git log --oneline
    ```
<br>

7. To confirm the working branch name in the local repository, enter the command:
    ```
    git branch
    ```
    > **TIP:** 
    > In the event the default local branch is named 'master', rename it to 'main': **`git branch -M main`**
    > In doing so, the branch names are consistent between the local and remote repository.


    > **TIP:** 
    > When renaming a branch:
    > * A **lowercase -m option** renames the current branch to branch-name. If a branch with the new name already exists, Git will show an error.
    > * An **uppercase -M option** forcefully renames the branch to branch-name, even if a branch with that name already exists. This option overwrites the existing branch.

<br>

8.	Now, add the remote repository's url to upload the committed work to Github:
    ```
    git remote add origin <remote-repo-url>
    ```
<br>

9.	To confirm, refer to the remote repository url created earlier in step #8 using the command:
    ```
    git remote -v
    ```
<br>

10. Finally, *PUSH* the locally committed files to the remote repository:
    ```
    git push -u origin main
    ```
    > **NOTE:** 
    > The keyword 'origin' refers to the **remote** repository's default branch
    
    > **TIP:** 
    > In the event the remote repository's url is mis-spelt, use the following command to revise the url performed in step #8:
    > **`git remote set-url origin <revised-remote-repo-url>`**

<br>

### B. Pulling changes from remote repository to update local repository
-------

1.	Suppose changes are introduced to the remote repository, where a new branch is created from the main branch:

    > `main` 
    > -> **`<new-branch>`**

<br>

2. In the local working branch, enter the command:
    ```
    git pull
    ```
    > **NOTE:** 
    > The **git pull** command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. 

    > **IMPORTANT:** 
    > The **`git pull`** command is a combination of **`git fetch`** and **`git merge`**. It first fetches changes from a remote repository and then merges them into the current branch in your local repository. 

<br>

3. After pulling the changes , run the following command to check out the branch to work on locally:
    ```
    git checkout <new-branch>
    ```
<br>

4.	For  any changes performed on the new branch, repeat **(A)4** `git add` to stage the changes and **(A)5** `git commit` to commit the changes.
<br>

5.	Finally, push the changes on the working 'new-branch' to the remote repository:
    ```
    git push -u origin <new-branch>
    ```
<br>

### C. Cloning vs Forking an existing repository 
-------

1. **Cloning** creates a local copy of the repository on your machine for personal work. <u>The cloned repository is linked to the original repository for updates</u>. Given an existing repository, one can clone the repository using the following command:
    ```
    git clone <owner-repository-url> . 
    ```
    > **IMPORTANT:** 
    > The (.) sign is appended to the end of the command to download the contents to the root of the working folder. Without the symbol, the repository will be cloned as a self-containing folder.

<br>

2. **Forking** creates a personal copy of the repository in your own GitHub account. <u>Forking is typically used when you want to contribute to someone else’s project and you can make changes independently and submit them</u> as a **<u>pull request</u>** to the original repository. After forking a repository, enter the command to clone and work on the forked repository as your own:
    ```
    git clone https://github.com/<your_username>/<your-forked-repo>.git .  
    ```
<br>

### D. Checking out a new branch and merging a branch
-------

1.	Suppose a remote repository has been cloned and the intention is to <u>leave the original, cloned work untouched whilst working on a new feature</u>. For such a situation, a new branch should be created using the following command:
    ``` 
    git checkout -b <new-local-branch>
    ```
<br>

2. For  any changes performed on the new local branch, repeat **(A)4** `git add` to stage the changes and **(A)5** `git commit` to commit the changes.
<br>

3. To *push* the locally committed files to the remote repository, consider the following options. **Either**:
    1. <u>push the changes as a new **remote** branch:</u>
        ```
        git push -u origin <new-local-branch>
        ```
    2. <u>Or, locally MERGE the new branch onto the main branch before pushing the changes to the remote repository:</u>
        * Check out the **local destination branch** to merge onto. In the example here, we shall refer to 'main' branch as the destination branch to merge onto:
            ```
            git checkout main
            ```
        * Next, run the following command to merge the source branch (new-local-branch) to the destination branch ('main') locally:
            ```
            git merge <new-branch>
            ```
        * Finally, push the merged changes on main to the remote repository:
            ```
            git push
            ```
            > **TIP:** 
            > When you run git push -u origin branch-name the first time, the option (-u or --set-upstream) will set the specified branch as the default upstream branch for future pushes from your current local branch.
            > Therefore, Git remembers the remote and branch and <u>you only need to use **git push** for subsequent pushes</u>. Git will automatically push to the previously set upstream branch without needing to specify the origin or branch-name again.

<br>

4. After merging, you can delete the branch that is no longer needed using the following command:
    ```
    git branch -D branch-name
    ```
    > **TIP:** 
    > * An **uppercase -D option** forcefully deletes a branch, regardless of its merge status. This option should be used with caution, as it can remove unmerged work.
    > * A **lowercase -d option** deletes a branch only if it is fully merged with the current branch or its upstream branch. If there are unmerged changes, Git will prevent the deletion to avoid data loss.