
###### Git practical pdf: <a href="./GitHub Practical.pdf">Github Practical.pdf</a>

# Git Commands

### 1. Init
The git init command creates a new Git repository on your local machine. 
```
git init
```

### 2. Clone
Git clone command retrieve an entire repository from a hosted location via URL.
```
git clone {repository link}
```

### 3. Status
Git status command show the modified, deleted or newly created file of current directory for next stage.
```
git status
```

### 4. Add
Git add command add the untrackable or changed file into staging area.

```
# for all file
git add .

# specific file
git add {file name}
```

### 5. Commit
Git commit commit your staged content as a new commit snapshot.

``` 
git commit -m "message"
```

If you want to commit file without ``` git add ``` command then use below command  
**Note:** Here only trackable file will commit if you have create new file then this command is not usefull.
```
git commit -a -m "message"
```

If you want to change commit messsage use
```
git commit --amend
```

It will change the top(HEAD) commit's message but if you want to change the any commit's message then use ``` rebase ``` which you will learn further.

### 6. Reset
Git reset command use to unsatge or drop commits of current branch.

###### **It has three flag**
- hard
- mixed(default)
- soft

**i. --hard:** It will resets the current branch commit, and also deletes all changes in the working directory and staging area. 
```
git reset --hard {commit's hash where you want to go}
```

**ii. --mixed:** It will resets the current branch commit, and also unsatge all changes in the working directory and staging area. 
```
git reset --mixed {commit's hash where you want to go}
```

**iii. --soft:** It will resets the current branch commit, but all staged changes remaining as it is. 
```
git reset --soft {commit's hash where you want to go}
```

### 7. Fetch 
Git fetch downloads all history from the remote tracking branches.
```
git fetch
```

### 8. Merge
Git merge command merge current branch with target branch.
```
git merge {target branch}
```

### 9. Pull
Git pull command is fetch the history from remote branch and merge it into current branch. it's combination of ```fetch``` and ```merge```.
```
git pull {alias} {target branch}
```

### 10. Push
Git push command push the commited file from local repository to remote repository's branch.
```
git push {alias} {target branch}
```

### 11. Branch
Git branch command use for create new branch in repository and show the all branch of repository.
```
# show all branches
git branch

# create new branch
git branch {new branch name}
```

### 12. Checkout
Git checkout use for switch branch or reach out particular node of git tree.
```
git checkout {branch name}
```

We can create new branch and switch on it using ```checkout```.
```
git checkout -b {branch name}
```

### 13. Stash
Git stash command is locally stores all the most recent changes in a workspace and resets the state of the workspace to the prior commit state.

```
git stash
```
We can see the stash list using ```log```
```
git stash log
```

It's save in stack and we can take it easily from stack using ```apply```
```
# apply all changes
git stash apply 

# apply particular stash changes
git stash apply {stash number}
```
**Note:** you can't run ```git stash apply``` command couple of times.

We can drop all stash from stash's stack using ```clear``` that we can't get back our changes.
```
# drop all stash
git stash clear

# drop particular stash
git stash drop {stash number}
```
In ```stash pop``` first apply changes of particular stash in directory and remove from stack.
```
git stash pop {stash number}
```

### 14. Restore
Git restore command helps to unstage or even discard uncommitted local changes.
```
git restore

# unstage particular file
git restore --staged {file name}
```

### 15. Rebase
Git rebase command take all commit of target branch and add inside current branch as it is.
It is the process of moving or combining a sequence of commits to a new base commit.
```
git rebase {target branch}
```

Rebase also use for change commit message, commit's sequences and merge commit.

**There are three flag when we use interactive rebase using ```-i``` flag.**

- pick: change the sequence of commit.
- reword: change the message of commit.
- squash: merge the commit with it's parent's commit.

### 16. Revert
The git revert command is a forward-moving undo operation that offers a safe method of undoing changes.
```
git revert
```

### 17. Cherry-pick
Cherry-picking in Git stands for applying some commit from one branch into another branch. we can retrieve any commit from any branch and put it on current branch.
```
git cherry-pick {commit hash}
```
### 18. Log
Git log is a utility tool to review and read a history of everything that happens to a repository. 
```
git log
git log --oneline
git log --oneline --graph --all

# show the commits that changed file, even across renames
git log --follow {file}
```

### 19. Reflog
Git keeps track of updates to the tip of branches using a mechanism called reference logs. we can see it using ```reflog```
```
git reflog
```

### 20. Tag
Tag is specific name of specific point that if we want to go that point then we can easily switch there via tag and once tag create it will not changes after commits.

Tag use for release version of your repository. it's **immutable**. we can create and remove it but not change it.
```
git tag {tag-name}
git push --tags
```

### 21. Diff
Git diff command show the difference between two branches or commits.
```
git diff {branch-1} {branch-2}
git diff {commit-1} {commit-2}
```

### Extra Notes
When you do by mistake merge two branches and if you want to unmerge those branches then you should use ```reset``` command to undo merged commit.
```
git reset --merge HEAD~1
```

***But*** if you have merge commit on remote server then you can't use above command beacuse git will tell you first pull repo from remote server and then push the code on remote branch so it will not work for that you have to ```checkout``` previous commit  and use ```push --force``` command to forcely push on remote server.
***Note: It's very dangerous for branch network.***
```
git push --force {branch-name}
```
