---
title: "Gitflow and Git commands juxtaposition"
author: anantharajuc
categories: [ Git ]
layout: post
date: 2021-05-01 16:00
image: /assets/images/Git.png
---

A juxtoposition of commands used in the Gitflow strategy using a plugin vs plain vanilla git commands.

## 1. Initialize

##### gitflow

*	**`git flow init`**  

##### git

*	**`git init`**  
*	**`git commit --allow-empty -m "Initial commit"`**  
*	**`git checkout -b develop master`**  



## 2. Connect to the remote repository

##### gitflow

*	_N/A_  

##### git

*	**`git remote add origin git@github.com:MYACCOUNT/MYREPO`**  

---

## 3. Features

### 3.1 Create a feature branch

##### gitflow

*	**`git flow feature start MYFEATURE`**  

##### git

*	**`git checkout -b feature/MYFEATURE develop`**  

### 3.2 Share a feature branch

##### gitflow

*	**`git flow feature publish MYFEATURE`**  

##### git

*	**`git checkout feature/MYFEATURE`**  
*	**`git push origin feature/MYFEATURE`**  

### 3.3 Get latest for a feature branch

##### gitflow

*	**`git flow feature pull origin MYFEATURE`**  

##### git

*	**`git checkout feature/MYFEATURE`**  
*	**`git pull --rebase origin feature/MYFEATURE`**  

### 3.4 Finalize a feature branch

##### gitflow

*	**`git flow feature finish MYFEATURE`**  

##### git

*	**`git checkout develop`**  
*	**`git merge --no-ff feature/MYFEATURE`**  
*	**`git branch -d feature/MYFEATURE`**  

### 3.5 Push the merged feature branch

##### gitflow

*	_N/A_  

##### git

*	**`git push origin develop`**  
*	**`git push origin :feature/MYFEATURE`**  _(if pushed)_  

---

## 4. Releases

### 4.1 Create a release branch

##### gitflow

*	**`git flow release start 1.2.0`**  

##### git

*	**`git checkout -b release/1.2.0 develop`**  

### 4.2 Share a release branch

##### gitflow

*	**`git flow release publish 1.2.0`**  

##### git

*	**`git checkout release/1.2.0`**  
*	**`git push origin release/1.2.0`**  

### 4.3 Get latest for a release branch

##### gitflow

*	_N/A_  

##### git

*	**`git checkout release/1.2.0`**  
*	**`git pull --rebase origin release/1.2.0`** 

### 4.4 Finalize a release branch

##### gitflow

*	**`git flow release finish 1.2.0`**  

##### git

*	**`git checkout master`**  
*	**`git merge --no-ff release/1.2.0`**  
*	**`git tag -a 1.2.0`**  
*	**`git checkout develop`**  
*	**`git merge --no-ff release/1.2.0`**  
*	**`git branch -d release/1.2.0`**  

### 4.5 Push the merged feature branch

##### gitflow

*	_N/A_  

##### git

*	**`git push origin master`**   
*	**`git push origin develop`**   
*	**`git push origin --tags`**  
*	**`git push origin :release/1.2.0`** _(if pushed)_  

---

## 5. Hotfixes

### 5.1 Create a hotfix branch

##### gitflow

*	**`git flow hotfix start 1.2.1 [commit]`**  

##### git

*	**`git checkout -b hotfix/1.2.1 [commit]`**  

### 5.2 Finalize a hotfix branch

##### gitflow

*	**`git flow hotfix finish 1.2.1`**  

##### git

*	**`git checkout master`**  
*	**`git merge --no-ff hotfix/1.2.1`**  
*	**`git tag -a 1.2.1`**  
*	**`git checkout develop`**  
*	**`git merge --no-ff hotfix/1.2.1`**  
*	**`git branch -d hotfix/1.2.1`**  

### 5.3 Push the merged hotfix branch

##### gitflow

*	_N/A_  

##### git

*	**`git push origin master`**  
*	**`git push origin develop`**  
*	**`git push origin --tags`**  
*	**`git push origin :hotfix/1.2.1`**  _(if pushed)_      

---