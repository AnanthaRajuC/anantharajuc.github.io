---
title: "Git : Distributed Version Control System"
author: anantharajuc
categories: [ Git, CLI ]
tags: [ Git, CLI ]
layout: post
date: 2019-02-10 07:30
image: /assets/images/Git.png
---

This post documents some of the most essential and common [Git](https://git-scm.com/) commands for version control.

Refer https://github.com/AnanthaRajuC/Git-Feature-Branch-Workflow for **Git Feature Branch Workflow** example with all relevant git commands.

Refer https://github.com/AnanthaRajuC/Gitflow-Workflow for **Gitflow Workflow** example with all relevant git commands.

---

#### Introduction

**Git** is software for tracking changes in any set of files, usually used for coordinating work among programmers collaboratively developing source code during software development. Its goals include speed, data integrity, and support for distributed, non-linear workflows. 

Local repository consists of three **trees** maintained by git.  

1. **Working Directory** - holds the actual files.  
2. **Index** - staging area.  
3. **HEAD** - points to the last commit.  

---

#### Minimum Software Requirements

- [Git](https://git-scm.com/)

---

#### Initialization

*	**`git init`**  
Initializes a new git repository

--- 

*	**`git clone /path/to/repository`**  
creates a working copy of a local repository

--- 

*	**`git clone username@host:/path/to/repository`**  
creates a working copy of a remote repository

---

#### Local workflow

*	**`git add <filename>`**  
add a single changed file to staging area (**Index**)

--- 

*	**`git add *`**  
add all changed files to staging area (**Index**)

--- 

*	**`git commit -m "Commit message"`**  
commits the changed files in staging area to **HEAD**

---

#### Remote

*	**`git remote set-url origin https://github.com/user/new-repo.git`**   
Change the URI (URL) for a remote Git repository

--- 

*	**`git remote show origin`**   
Find the URL of the remote repository.

--- 

*	**`git remote -v`**   
List all currently configured remote repositories

---

#### Pulling and Pushing changes

*	**`git pull`**   
update your local repository to the newest remote commit.

--- 

*	**`git push origin <branch>`**  
push the changes to your remote repository.

--- 

*	**`git remote add origin <server>`**  
If you have not cloned an existing repository and want to connect your repository to a remote server.

---

#### Branching

1. **Branches** are used to develop features isolated from each other.
2. **main/master** branch is the **default** branch in a repository.
3. other branches are used for development and merged back to the main/master branch upon completion.

*	**`git checkout -b feature_x`**  
create a new branch named **feature_x** and switch to it using

--- 

*	**`git checkout master`**  
switch back to master branch

--- 

*	**`git push origin <branch>`**  
push from local to remote **branch**

--- 

*	**`git push --all origin`**  
Push all branches to your remote repository

##### Deleting a branch

*	**`git push -d origin <branch name>`**  
Remove a remote branch from the server

--- 

*	**`git branch -d <branch name>`**  
Delete local branch

---

#### Tagging

*	**`git tag 1.0.0 1b2e1d63ff`**   
create a new tag named <a href="https://semver.org/" target="_blank" >1.0.0</a> where 1b2e1d63ff stands for the first 10 characters of the commit id you want to reference with your tag

--- 

*	**`git tag -a 'Version_1_0' -m 'Simple UI' HEAD`**   
Create Tag - Tag operation allows giving meaningful names to a specific version in the repository.

--- 

*	**`git push origin tag Version_1_0`**   
push the tag into the remote repository

--- 

*	**`git tag -l`**   
view all the available tags

---

#### Undo all working dir changes including new files

Delete all changes from working directory including new untracked files.

*	**`git reset --hard`**   
Removes staged and working directory changes

--- 

*	**`git clean -nfd`**   
To see what will be deleted before-hand, without actually deleting it, use the **-n** flag (this is basically a test-run). When you are ready to actually delete, then remove the **-n** flag

--- 

*	**`git clean -f -d`**   
Remove untracked

--- 

*	**`git clean -f -x -d`**   
**CAUTION:** as above but removes ignored files like config.

--- 

*	**`git clean -fxd :/`**   
**CAUTION:** as above, but cleans untracked and ignored files through the entire repo (without :/, the operation affects only the current directory)
 
--- 

**Reference:** https://stackoverflow.com/questions/1090309/git-undo-all-working-dir-changes-including-new-files

---

#### Log

*	**`git log`**   
displays repository commit history

--- 

*	**`git log --author=bob`**   
displays only the commits of a certain author

--- 

*	**`git log --pretty=oneline`**   
displays a very compressed log where each commit is one line

--- 

*	**`git log --graph --oneline --decorate --all`**   
displays an ASCII art tree of all the **branches**, decorated with the names of **tags** and **branches**

--- 

*	**`git log --name-status`**   
displays only which files have changed

--- 

*	**`git log --pretty="- %s" > CHANGELOG.md`**   
save changelog to file.

--- 

*	**`git log --oneline --decorate`**   
output with one commit per line.

--- 

*	**`git log --pretty="%C(Yellow)%h  %C(reset)%ad (%C(Green)%cr%C(reset))%x09 %C(Cyan)%an: %C(reset)%s"`**   

--- 

*	**`git log --all --decorate --oneline --graph`**   

--- 

*	**`git log --pretty="- %s"`**   

---

#### Others

*	**`git log --help`**   
opens a local git-log manual (html) page

--- 

*	**`gitk`**   
opens a built-in git GUI desktop application

--- 

*	**`git diff file.file_type`**  
See changes to a specific file using git

---

#### Examples

*	**`git log --oneline -5 --author cbeams --before "Fri Mar 26 2009"`**   

---

#### Additional Reading

<a href="https://guides.github.com/introduction/flow/" target="_blank" >Understanding the GitHub flow</a>

--- 

#### Resources

- <a href="https://github.com/k88hudson/git-flight-rules" target="_blank" >Flight rules for Git </a>- a guide for programmers using Git about what to do when things go wrong
- <a href="https://chris.beams.io/posts/git-commit/" target="_blank" >How to Write a Git Commit Message</a>
- <a href="https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html" target="_blank" >A Note About Git Commit Messages</a>
- <a href="https://nvie.com/posts/a-successful-git-branching-model/" target="_blank" >Pro Git</a> by <a href="http://scottchacon.com/about.html" target="_blank" >Scott Chacon</a> and Ben Straub is available to read online for free and download (PDF, EPUB, MOBI).
- <a href="https://chris.beams.io/posts/git-commit/" target="_blank" >How to Write a Git Commit Message</a>
- <a href="https://www.conventionalcommits.org/en/v1.0.0/" target="_blank" >Conventional Commits - A specification for adding human and machine readable meaning to commit messages</a>

--- 
