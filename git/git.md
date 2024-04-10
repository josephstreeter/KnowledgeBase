# Git
- [Home](../README.md)

---

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
$ git config gpg.format ssh
$ git config user.signingkey ~/.ssh/key.pub
$ git --amend 
```
### Rebase
```
$ git rebase feature_branch
$ git rebase -i HEAD~3 * Do NOT use interactive rebase on commits that have already been pushed to remote repository
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
