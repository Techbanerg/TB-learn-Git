# Git Commands for Developers and DevOps
================================================================================

We all know “Necessity is the mother of all inventions”. And similarly Git was also invented to fulfill certain necessities that the developers faced before Git. So, let us take a step back to learn all about Version Control Systems (VCS) and how Git came into existence.Version Control is the management of changes to documents, computer programs, large websites and other collection of information.

## There are two types of VCS: 

1. Centralized Version Control System (CVCS)
2. Distributed Version Control System (DVCS)

## Centralized VCS
* Centralized version control system (CVCS) uses a central server to store all files and enables team collaboration. It works on a single repository to which users can directly access a central server.Even though it seems pretty convenient to maintain a single repository, it has some major drawbacks. 
Some of them are:

* It is not locally available; meaning you always need to be connected to a network to perform any action.
* Since everything is centralized, in any case of the central server getting crashed or corrupted will result in losing the entire data of the project.

## Distributed VCS
* These systems do not necessarily rely on a central server to store all the versions of a project file.In Distributed VCS, every contributor has a local copy or “clone” of the main repository i.e. everyone maintains a local repository of their own which contains all the files and metadata present in the main repository.Every programmer maintains a local repository on its own, which is actually the copy or clone of the central repository on their hard drive. They can commit and update their local repository without any interference. 
* They can update their local repositories with new data from the central server by an operation called “pull” and affect changes to the main repository by an operation called “push” from their local repository.

The act of cloning an entire repository into your workstation to get a local repository gives you the following advantages:
1. All operations (except push & pull) are very fast because the tool only needs to access the hard drive, not a remote server. Hence, you do not always need an internet connection.
2. Committing new change-sets can be done locally without manipulating the data on the main repository. Once you have a group of change-sets ready, you can push them all at once.
3. Since every contributor has a full copy of the project repository, they can share changes with one another if they want to get some feedback before affecting changes in the main repository.
4. If the central server gets crashed at any point of time, the lost data can be easily recovered from any one of the contributor’s local repositories.

## Advanced Commands

### Git Rebasing:
* Rebasing is the process of moving or combining a sequence of commits to a new base commit. Rebase is one of two Git utilities that specializes in integrating changes from one branch onto another.Rebasing is often used as an alternative to merging.
* Rebasing a branch updates one branch with another by applying the commits of one branch on top of the commits of another branch.For example, if working on a feature branch that is out of date with a dev branch, rebasing the feature branch onto dev will allow all the new commits from dev to be included in feature.

### Git Log:
* To Identify good and bad commits
### Git Reset:
* The first method is a simple way to throw away few recent commits, it re-writes the commit history, so only use it when your changes are not pushed to the server yet (or when you are 100% sure about what you are doing).
* Git reset should generally be considered a 'local' undo method. A reset should be used when undoing changes to a private branch. This safely isolates the removal of commits from other branches that may be in use by other developers. Problems arise when a reset is executed on a shared branch and that branch is then pushed remotely with git push. Git will block the push in this scenario complaining that the branch being pushed is out of date from the remote branch as it is missing commits.

* The preferred method of undoing shared history is git revert. A revert is safer than a reset because it will not remove any commits from a shared history. A revert will retain the commits you want to undo and create a new commit that inverts the undesired commit. This method is safer for shared remote collaboration because a remote developer can then pull the branch and receive the new revert commit which undoes the undesired commit.

### Git Revert:
Let's assume we are back to our original commit history example. The history that includes the 872fa7e commit. This time let's try a revert 'undo'. If we execute git revert HEAD, Git will create a new commit with the inverse of the last commit. 

### Git Bisect:
This command uses a binary search algorithm to find which commit in your project’s history introduced a bug. You use it by first telling it a "bad" commit that is known to contain the bug, and a "good" commit that is known to be before the bug was introduced.Then git bisect picks a commit between those two endpoints and asks you whether the selected commit is "good" or "bad". It  continues narrowing down the range until it finds the exact commit that introduced the change. 
### Git Cherry-pick:
Git cherry-pick is a powerful command that enables arbitrary Git commits to be picked by reference and appended to the current working HEAD. Cherry picking is the act of picking a commit from a branch and applying it to another.
### Git Amend:
 The git commit --amend command is a convenient way to modify the most recent commit. It lets you combine staged changes with the previous commit instead of creating an entirely new commit. It can also be used to simply edit the previous commit message without  changing its snapshot. But, amending does not just alter the most recent commit, it replaces it entirely, meaning the amended commit     will be a new entity with its own ref.



### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snap-shotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes in that branch |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Checking-out Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |

| Command | Description |
| ------- | ----------- |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |

| Command | Description |
| ------- | ----------- |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |

| Command | Description |
| ------- | ----------- |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |
| `git push origin --delete [branch name]` | Delete a remote branch |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --one line` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging |


| Command | Description |
| ------- | ----------- |
|`git rebase feature dev` | commits on dev branch on to feature |
|`git rebase --continue` | To Continue after merge conflict |
|`git rebase --abort` | To Abort after merge conflict |
|`git rebase -i HEAD~5`| Interactive rebase
|`git commit --amend`| 
|`git log` | To see the commits 

| Command | Description |
| ------- | ----------- |
|`git reset HEAD~2` |  Discard last two commits |
|`git reset 1a45gf02`| Reset to SHA |
|`git revert --no-commit HEAD~3`| Revert the changes specified by the fourth last commit in HEAD |
|`git revert HEAD~3`| Revert the changes specified by the fourth last commit in HEAD and create a new commit with the reverted changes.|
|`git bisect start`| Git bisect is like a wizard to find the commit that broke your code. |
|`git bisect bad <SHA>`| git bisect checked out an old commit for us |
|`git bisect good SHA>`| Let the git bisect wizard know of a good commit |
|`git bisect reset` | To end your git bisect wizard, simply type git bisect reset |
|`git cherry-pick commitSha`|  it creates a new commit with a new SHA.
|`git cherry-pick <SHA> --no-commit`| picked a commit from one branch, and pasted to another |
|`git cherry-pick -x <commit-hash>`| it creates a new commit with a new SHA. |
|`git cherry-pick d467740 de906d4` | cherry pick more than one commit in one go, you can add their commit IDs separated by a space|
|`git cherry-pick --continue`| picking gets halted because of conflicts |
|`git cherry-pick --abort`| If you want to bail of this step |

## Links
* https://www.atlassian.com/git/tutorials/undoing-changes
* https://www.previousnext.com.au/blog/intro-cherry-picking-git