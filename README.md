# **GIT-COMMANDS**

**Add Repository**

-  Initialise a git repository with .git
> **git init**

-  Adding files to the git
> **git add .**

-  Commiting the added files
> **git commit -m "Initialising/First Commit"**

----------

**Advanced**

- To Revert/Recall Changes:
    - IF LOCAL CHANGES, NO COMMIT MADE.
        - These can be in two stages:
          - Staged / Unstaged : Difference between them is have you added them or not.
            If added using `git add` command, then staged, otherwise unstaged.
          - Now for any local changes in staged section, ideally should be brought to unstaged section
            before removing it.
          - Command
          ```
          # particular files
          git reset HEAD <file1> <file2>

          # all files
          git reset HEAD
          ```
        - Once local changes in unstaged section, you can remove these changes:
          - Command
          ```
          git restore <file1> <file2>
          # or
          git checkout <file1> <file2>
          ```
    - IF COMMIT MADE, BUT NOT PUBLISHED
        - If you want to keep the changes just want to do some edit.
          - Command
          ```
          # from hash, if you want to go back to a particular commit use its hash
          git reset --soft 0bfabb11a8ce2b61dbf204ee3bc55ba58df354fd

          # from count from top, replace 2 with count of top commits you want to remove
          git reset --soft HEAD~2
          ```
        - If you dont want to keep the changes just clean.
          - Command
          ```
          # from hash, if you want to go back to a particular commit use its hash
          git reset --hard 0bfabb11a8ce2b61dbf204ee3bc55ba58df354fd

          # from count from top, replace 2 with count of top commits you want to remove
          git reset --hard HEAD~2
          ```

    - IF COMMIT MADE, AND PUBLISHED
        - If there are more people working on it use revert. Which will create a rollback commit aswell.
          - When we do revert changes of those commits removed and get staged for the commit to imply removing these changes.
          - Command
          ```
          # From particular hash to head rollback, to that particular hash comit all above commits will be removed.
          git revert --no-commit 0bfabb11a8ce2b61dbf204ee3bc55ba58df354fd..HEAD

          # If you want to revert by count from top, replace 3 by count number
          git revert --no-commit HEAD~3..HEAD
          ```

- If anything unwanted happened and too much of confusion with commits or reverts or anything:
      - Simple stash the unsaved changes and do `git pull`
      - It will bring your local syste to repository git status.
- To pull changes after commit, therefore always do, `git pull --rebase`, it will bring your commit on top
  of other commits and then do `git push origin`


- Stash: We use stash for saving our local changes so that we can pull or work on different commmits
    - Command
    ```
    # To Stash
    git stash

    # To view a particular stash
    git stash show -p stash@{1}

    # To apply a particular stash
    git stash apply stash@{1}

    # To apply top Stash
    git stash apply

    # To apply and remove top Stash
    git stash pop

    # To drop a particular Stash
    git stash drop stash@{1}

    # To see stash list
    git stash list

    # To clear stash list
    git stash clear
    ```

- Check git logs:
    - Command
    ```
    # Git check all logs, use q to exit, if logs are more than screen size and down button to explore all
    git logs

    # to view top x logs, replace 5 with x number in the below commands.
    git logs -n 5

    # To check log graph and its branches in detailed manner
    git log --graph --oneline --decorate --all
    ```

- To cherry pick a commit:
    - Command
    ```
    # Go to branch from where you want to pick
    git checkout branch_name

    # View its commits
    git log

    # Go to original branch
    git checkout original_branch

    # cherry pick commit
    git cherry-pick commit_id
    ```

----------
**Pull**

-  To pull a branch
> **git checkout <branch_name>**

> **git pull**

----------

**Commit And Push**

-  Checkout to the branch where one will make changes.
> **git checkout <branch_name>**

-  To commit the changes
> **git commit -m "<comment_on_changes>"**

-  To push the changes
> **git push**

----------

**Remote**

Remote's are generally places where git repositories of your interest are situated and you are either interested in pulling or pushing into that git repository from your local machine.

-  Check all remote names already present
> **git remote**

If remote not added, then add remote first.
> **git fetch <remote_name>**

To get all branches
> **git fetch --all**

-  To add a new remote
> **git remote add  <remote_name>  <remote_url>**

-  To remove existing remote
> **git remote remove <remote_name>**

-  To know information about existing remote (e.g. -> remote_url)
> **git remote show <remote_name>**

----------

**Branch**

-  Check all branch names already present
> **git branch**

To get all branches
> **git fetch --all**

-  Create a branch
> **git checkout -b <branch_name>**

> **git push <remote_name> <branch_name>**

-  To Delete a branch

First checkout to some other branch, for now lets say `master` because you cannot delete the branch in which you are already present.  
> **git checkout master**

Delete branch locally(forcefull delete)
> **git branch -D <branch_name>**

Delete branch from remote
> **git push <remote_name> --delete <branch_name>**

----------

**Merge**

-  Merge between branches

First checkout to the branch in which you want to merge the changes(lets say `branch_one`) from another branch(lets say `branch_two`).  
> **git checkout branch_one**

Now lets merge assuming that no conlicts are there.
> **git merge branch_two**

-  Merge into a branch form remote.

First checkout to the branch in which you want to merge the changes(lets say `branch_one`) from remote branch.  
> **git checkout branch_one**

If remote not added, then add remote first.
> **git fetch <remote_name>**

> **git merge <remote_name>/<remote_branch_name>**

----------

**Updating A Fork**

-  Add Upstream

First we will add a remote(forked_repo_clone_url) and name it as `upstream`.  
> **git remote add upstream <repo_clone_url>**

-  Update remote
> **git fetch upstream**

> **git merge upstream/<upstream_branch_name>**

----------

**Miscellaneous**

-  Check present git information
> **git status**

-  To view a commit changes
> **git show commit_hash**
----------
