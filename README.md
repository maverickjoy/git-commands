# **GIT-COMMANDS**

**Add Repository**

-  Initialise a git repository with .git
> **git init**

-  Adding files to the git
> **git add .**

-  Commiting the added files
> **git commit -m "Initialising/First Commit"**

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

-  Create a branch
> **git checkout -b <branch_name>****
> **git push <remote_name> <branch_name>**

-  To Delete a branch

First checkout to some other branch, for now lets say master because you cannot delete the branch in which you are already present.  
> **git checkout master**

Delete branch locally(forcefull delete)
> **git branch -D <branch_name>**

Delete branch from remote
> **git push <remote_name> --delete <branch_name>**

----------

**Merge**

-  Merge between branches

First checkout to the branch in which you want to merge the changes(lets say branch_one) from another branch(lets say branch_two).  
> **git checkout branch_one**

Now lets merge assuming that no conlicts are there.
> **git merge branch_two**

-  Merge into a branch form remote.

First checkout to the branch in which you want to merge the changes(lets say branch_one) from remote branch.  
> **git checkout branch_one**

If remote not added, then add remote first.
> **git fetch <remote_name>**
> **git merge <remote_name>/<remote_branch_name>**

----------

**Updating A Fork**

-  Add Upstream

First we will add a remote(forked_repo_clone_url) and name it as upstream.  
> **git remote add upstream <repo_clone_url>**

-  Update remote
> **git fetch upstream**
> **git merge upstream/<upstream_branch_name>**

----------

**Miscellaneous**

-  Check present git information
> **git status**
