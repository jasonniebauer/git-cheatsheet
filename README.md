# Git Cheatsheet

## Table of Contents
- [Basic Workflow](#basic-workflow)
- [Repositories](#repositories)
  - [Default Settings](#default-settings)  
  - [Global Configuration](#global-configuration)
  - [Optional Configuration](#optional-configuration)
- [Undo](#undo)
- [Working with Branches](#working-with-branches)
- [Collaborating](#collaborating)

## Basic Workflow

## Repositories

### Default Settings
Use the command below to view *all* Git settings.
```sh
git config --list
```

View specific settings by using one of the following options below.

| Option   | Description                              |
|:---------|:-----------------------------------------|
| --system | Settings for every user on the machine.  |
| --global | Settings for every one of your projects. |
| --local  | Settings for one specific project.       |

Default settings for all of your projects will be ouput using the following command.
```sh
git config --list --global
```

**[⬆ back to top](#table-of-contents)**

### Global Configuration
Most of Git's settings should be left as is. However, there are two you should set on every machine: your name and your email address. These are recorded in commit logs to identify the content's author.

**Set your name**
```sh
git config --global user.name "John Doe"
```

**Set your email address**
```sh
git config --global user.email "example@email.com"
```
**[⬆ back to top](#table-of-contents)**

### Optional Configuration
Setup commit color helpers
```sh
$ git config --global color.ui true
```

Set the default editor
```sh
$ git config --global core.editor nano
```

Setup Git Ignore file
```sh
$ git config --global core.excludesfile ~/.gitignore_global
```

Setup Aliases (git st = git status)
```sh
$ git config --global alias.st status
```

**[⬆ back to top](#table-of-contents)**

## Undo

## Working with Branchs

## Collaborating

---

### Excludes
Place excludes in .git/info/exclude
- Exclude directory **experiments/**
- Exclude file **test.mp4** 
- Exclude all mp4 files __*.mp4__
- Exclude log files inside log directory __logs/*.log__

Add Files to Ignore
```sh
$ nano ~/.gitignore_global
```
**[⬆ back to top](#table-of-contents)**

### Help
```sh
$ git help <command>
```

### Initialization
Initialize Git Repository in Directory
```sh
$ git init
```

### Show Remote Repositories
```sh
$ git remote -v
```

### Adding a Remote Repository
```sh
$ git remote add <name> <address>
```
Example
```sh
$ git remote add origin <Github repo url>
```

### Remove a Remote Repository
```sh
$ git remote rm <name>
```

### Push to Remote
Origin: remote repository name, master: local branch to push
```sh
$ git push -u <name> <branch>
```
Example
```sh
$ git push -u origin master
```

### Clone a Repository
```sh
$ git clone <repository-url>
```

### Clone Repository and Rename
```sh
$ git clone <repository-url> <new-name>
```

### Status
```sh
$ git status
```

### Add Files to Staging Area
Add the list of files
```sh
$ git add <list of files>
```

Add all files
```sh
$ git add -a
```

Add all txt files in current directory
```sh
$ git add *.txt
```

Add all txt files in sepcific directory
```sh
$ git add /docs*.txt
```

Add all files in specific directory
```sh
$ git add /docs*
```

Add all txt files in the whole project
```sh
$ git add "*.txt"
```

### Skip Staging Area and Commit
Add changes from all tracked files and commit
```sh
$ git commit -a -m "commit message"
```
Shorthand for adding all and commit
```sh
$ git commit -am "commit message"
```

### Remove Files
Remove a file that is being tracked
```sh
$ git rm <file>
```

Remove just tracking
```sh
$ git rm --cached <file-name>
```

### Commit Files
Commit all staged files
```sh
$ git commit m "your message here"
```

### Undoing a Commit
Undo last commit, put changes into staging
(HEAD^ means move to the last commit before 'HEAD')
```sh
$ git reset --soft HEAD^
```
Undo last commit and all changes
```sh
$ git reset --hard HEAD^
```
Under last two commits and all changes
```sh
$ git reset --hard HEAD^^
```

### Adding to a Commit
Add another file or change to the previous commit and override commit message
```sh
$ git commit --amend -m "new commit message"
```

### Push Files to Repository
Push files to master branch
```sh
$ git push
```

Push files to another branch
```sh
$ git push origin <branch-name>
```

### Create Branches
Create a feature branch
```sh
$ git branch <feature-name>
```

Create a feature branch and check it out
```sh
$ git checkout -b <feature-name>
```

Create an orphan branch
```sh
$ git checkout --orphan gh-pages
```

Link Local Branch to the Remote Branch
```sh
$ git push origin <branch-name>
```

### Check which Branch you are on
```sh
$ git branch
```

### List all Remote Branches
```sh
$ git branch -r
```

### Remote Show
Shows remote branches and whether they are tracked or not, local branches and which branches they merge with, and local branches configured for git push and whether they are out of date or not.
```sh
$ git remote show <remote-name>
```

### Switching to a Branch
```sh
$ git checkout <branch-name>
```

### Check the Git Log
```sh
$ git log
```

View single line per log
```sh
$ git log --online
```

Exit Git log
```sh
$ q
```

### Merge Branches
Merge feature branch into master
```sh
$ git merge <feature-branch>
```

### Remove Branches
Delete a local branch (clean up)
```sh
$ git branch -d <branch-name>
```

Remove a remote branch (*Use Caution*)
```sh
$ git push origin :<branch-name>
```
After removing the remote, remove locally
```sh
$ git branch -d <branch-name>
```
Confirm removal of the local remote
```sh
$ git branch -D <branch-name>
```

### Clean Up Deleted Remote Branches
```sh
$ git remote prune origin
```

### Viewing Unstaged Differences
View unstaged differences since last commit
```sh
$ git diff
```

View parent of latest commit
```sh
$ git diff HEAD^
```

View grandparent of latest commit
```sh
$ git diff HEAD^^
```

View diff 5 commits ago
```sh
$ git diff HEAD~5
```

View second most recent commit vs most recent
```sh
$ git diff HEAD^..HEAD
```

View difference between two branches
```sh
$ git diff master <branch-name to compare against>
```

View time-based differences
```sh
$ git diff --since=1.week.ago --until=1.minute.ago
```

View diff with log
```sh
$git log -p
```

View who made changes
```sh
$ git blame <file-name> --date short
```

### Viewing Staged Differences
View staged differences since last commit
```sh
$ git diff --staged
```

###Discard Changes
Unstage a file (head refers to last commit)
```sh
$ git reset HEAD <file name>
```

Remove all changes to a file since the last commit
```sh
$ git checkout -- <file name>
```

### Remove all changes to multiple files in the last commit
Chain files together in a single command
```sh
$ git checkout -- <file 1 name> <file 2 name>
```

### Tagging
Tags are references to a commit (often used for release versioning)

List all tags
```sh
$ git tags
```

Checkout code at commit
```sh
$ git checkout <tag-name>
```

Add a new tag
```sh
$ git tag -a <tag-name> -m "<tag-description>"
```
Example
```sh
$ git tag -a v0.0.1 -m "version 0.0.1"
```

Push Tags
```sh
$ git push --tags
```

### Pull
Pulls changes to local and automatically merges
```sh
$ git pull
```

### Fetch
Pulls changes to local, but does not automatically merge
```sh
$ git fetch
```

### Keep a Fork Up-to-date
1. Add remote from the original repository in your forked repository:
```
$ git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git
$ git fetch upstream
```
2. Update your fork from the original repository to stay up-to-date with the original repository's changes:
```
$ git pull upstream master
```

### Rebase
Rebase moves all changes in master that are not in our working files to a temporay area, and then run all commits in the temporary area one at a time.
```sh
$ git rebase
```

### Local Branch Rebase
Switch branches
```sh
$ git checkout <branch-name>
```
First, run master commits and then run our branch commits
```sh
$ git rebase master
```
If all goes well, checkout and merge to master
```sh
$ git merge <branch-name>
```

### Rebase Conflicts
After fixing conflict, continue rebase
```sh
$ git rebase --continue
```
If you prefer to skip the conflict patch
```sh
$ git rebase --skip
```
Or to checkout original branch and stop rebasing
```sh
$ git rebase --abort
```
