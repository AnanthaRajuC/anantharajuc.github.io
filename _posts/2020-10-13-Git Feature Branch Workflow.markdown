---
title: "Git Feature Branch Workflow"
author: anantharajuc
categories: [ Git ]
layout: post
date: 2020-10-13 13:30
image: /assets/images/Git.png
---

The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the master branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the master branch will never contain broken code, which is a huge advantage for continuous integration environments.

---

##### STEP 1/4: clone a remote git repository  

*	**`git clone <remote-repository-url>`**  
clone a remote repository to a local system.  
example: **`git clone https://github.com/username/repository.git`**  

---

##### STEP 2/4: create a branch

1. **`git checkout -b branchName`**  
create and switch to a branch called branchName  

2. **`git push -u origin branchName`**  
links local branchName with remote corresponding branch  
push local branch to remote repository for the first time (first time only)  

---

##### STEP 3/4: merge branchName with master branch

1. **`git check out master`**  
point local environment to master branch  

2. **`git pull`**  
ensure local copy of our master branch has all latest changes from remote repository  

3. **`git merge branchName`**  
merge branch changes from branchName with current branch. In this case, master branch  

---

##### STEP 4/4: now local master is up-to-date

1. **`git push`**  
push local master to remote master

---