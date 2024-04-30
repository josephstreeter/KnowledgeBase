# Git
---

## Terminology
The following will cover a number of terms that will be encountered thoughout the use of Git and related services. The relationship of these terms is somewhat circular, so you may have to read them all and then read them again to understand how they relate to each other. 

- **Index** - A staging area where changes are stored before being committed to the ***working tree.***
- **Working Tree** - The directory, including all its files and sub-directories that make up a repository. The top level of a working tree can be identified by the existence of a .git directory.
- **Commit** - A snapshot of the working tree at the time the commut was created. When a commit is created, the state of ***HEAD*** becomes that commit's parent. It is this parent relationship that is the basis for the concept of "source control."
- **HEAD** - Defines what is currently checked out. HEAD symbolically refers to a ***branch*** that is checked out. If a specific ***commit*** is checked out (Detached HEAD), HEAD referes to that ***commit*** only. 
- **Repositoy** - A repository is a collection or ***commits*** and defines which one is the ***HEAD***.
- **Branch** - A name for a ***commit*** and it's parentage that defines history. 
- **Tag** - Similar to a branch, it names a particular commit and can have it's own description.
- **Master/Main** - A branch that represents the mainline of development for a repository. Typically known as either ***master*** or ***main***, may also be named ***trunk***. 

# Concept
Below is an explanation of 

A working tree is created by initializing a directory (git init) or by cloing an exiting repository (git clone "path/to/repository"). Work is then done with the files in the working tree to create a feature or resolve a bug.

At a signigicant point in the work, add your changes to the ***index*** (git add "file name"). Once all of the changes to create the feature or resolve the bug added to the ***index***, the changes are commited to the repository (git commit -m "commit message"). 

## Workflow
Generally, the workflow follows the following steps:
- Get the latest copy of main/master 
``` 
git pull 
```
- Create an issue/feature branch and switch to that branch
``` 
git branch <name>
git switch <name>
```
- Make whatever changes you intend to make. Stage changes an make commits as needed. 
```
git add *
git commit -m "<message describing change>"
```
- Push changes to the origin branch. You must create the origin branch if it doesn't already exist. 
```
git push

# or

git push --set-upstream origin
```
- Create a Pull Request in GitHub or ADO. Approval of this PR will merge the changes with main/master.

## Resolving Merge Conflicts
- Edit each of the conflict files to retain the code you want to retain.
- Stage the updated files and create a commit
```
git add * 
git commit -m 'commit message'
```
## Resolving Errors
#### Divergent Branch Error

***Describe the error***
```
git switch <feature branch>
git rebase main

# If main/master is not protected, you can then merge into that branch. Otherwise, create a PR to merge the changes into main/master.
git switch main
git merge feature


```


## Snippets
### Alias
```
$ git config –global alias.stash ‘stash --all’
$ git config –global alias.bb !script.sh
```
### Configs
```
$ git config --global user.name First I Last
$ git config --global user.email first.last@gmail.com
```
When creating a new branch from the CLI, you may see the following message:
```
$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint:   git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint:   git branch -m <name>
Initialized empty Git repository in /home/hades/Documents/repos/AzureTerraform/.git/
$ git config --global intit.defaultBranch main
```
### Conditional Configs
Separate config for git based on where the files are located. 
```
# Configuration for "work" projects
[include “gitdir:~/projects/work/”]
path = ~/projects/work/.gitconfig
```
```
# Configuration for "personal" projects
[include “gitdir:~/projects/personal/”]
path = ~/projects/personal/.gitconfig
```
Below are the contents of the two config files specified above. 
```
# Contents of "work" configuration file
cat ./work/.gitconfig
[user]
Email = first.last@work.com
[commit]
gpgsign = true

# Contents of "personal" configuration file
cat ./personal/.gitconfig
[user]
Email = first.last@gmail.com
[commit]
gpgsign = false
```
### Logs
```
$ git log --oneline
$ git log -S files -p
```
### Diff
```
$ git diff
$ git diff --word-diff
```
### Branches
```
$ git branch
$ git branch --column
$ git config --global column.ui auto
$ git config --global branch.sort -committerdate
```
### Commits
```
$ git commit -m "Commit message"
$ git commit -a -m "Commit message"
$ git --amend 
```
Createing commits signed by GPG
```
$ git config gpg.format ssh
$ git config user.signingkey ~/.ssh/key.pub
```
### Rebase
```
$ git rebase -i HEAD~3 
```
Interactive Rebase
> [!WARNING]
> Do NOT use interactive rebase on commits that have already been pushed to remote repository
```
$ git rebase feature_branch
```
### Maintenance
```
$ git maintenance start
```
### Recover lost commit
```
$ git reflog * copy the commit hash before the action that deleted
$ git branch <branch name> <commit hash>  * branch name = new branch name, commit hash = past commit hash from previous step
```
### Recover lost branch
```
$ git reflog * copy the commit hash before the action that deleted
$ git branch <branch name> <commit hash>  * branch name = branch name that was deleted, commit hash = past commit hash from previous step
```
### Workflow
```
$ git clone <repo>
$ git branch <branch name>
$ git switch <branch name>
<do stuff>
$ git add *
$ git commit -m “<commit message>”
$ git push --set-upsteam origin <branch name>
$ git switch main
$ git merge <branch name>
```

## SSH
VS Code works best with SSH for cloning. 
### Config File
The following config file will allow you to specify a specific SSH key for authenticating to Azure DevOps:
```
Host vs-ssh.visualstudio.com
    HostName vs-ssh.visualstudio.com
    IdentityFile ~/.ssh/id_rsa_ado
    HostkeyAlgorithms +ssh-rsa
    PubkeyAcceptedAlgorithms +ssh-rsa
    IdentitiesOnly yes
```
## References
[The gitflow workflow - in less than 5 mins](https://www.youtube.com/watch?v=1SXpE08hvGs)
[Learn Git Rebase in 6 minutes // explained with live animations!](https://youtu.be/f1wnYdLEpgI?si=SXW3BsP7Yqn_AIEd)
[Git MERGE vs REBASE: The Definitive Guide](https://youtu.be/zOnwgxiC0OA?si=lgOj1H4bT9dzbK5j)
[Resolve Git MERGE CONFLICTS: The Definitive Guide](https://youtu.be/Sqsz1-o7nXk?si=acwzXMaLEvkYE-do)

# Notes

### Workflow path and getting out of trouble
```
git branch feature > git switch feature > (make changes) > git add * > git commit -m 'commit message' > git push > git switch main > git merge feature
```
```
if merge confict 
-> (edit confict file) -> git add * -> git commit -m 'commit message'
```
```
if divergent branch error
-> git switch feature -> git rebase main -> git switch main -> git merge feature
```
