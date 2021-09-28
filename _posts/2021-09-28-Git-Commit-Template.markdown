---
title: "Git Commit Template"
author: anantharajuc
categories: [ Git, CLI ]
tags: [ Git, CLI ]
layout: post
date: 2021-09-28 09:00
image: /assets/images/Git.png
---

This post briefly captures the process of setting up a **Git Commit Template** for adding additional details to a *git commit* along with the mandatory one line *commit messages*.

Git will use this file as the default initial message when you commit. The value in creating a custom commit template is that you can use it to remind yourself (or others) of the proper format and style when creating a commit message.

---

#### Introduction

**Git** is software for tracking changes in any set of files, usually used for coordinating work among programmers collaboratively developing source code during software development. Its goals include speed, data integrity, and support for distributed, non-linear workflows.

---

#### Goals

1. Create A Git Commit Template File
2. Configure Global Commit Template

---

#### Minimum Software Requirements

- [Git](https://git-scm.com/)  

---

##### Getting Started 

#### **`Step 1 - Git Commit Template File`** 

Copy the following content/file onto a location on your local machine.

*Reference: template originally written by Tim Pope <https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html>*

<script src="https://gist.github.com/AnanthaRajuC/7c064859b3ef1c046c3070801e512001.js?file=git-commit-template.txt"></script>

---

#### **`Step 2 - Configure Global Commit Template`** 

Issue the following command to configure the **git-commit-template.txt** file as the global commit template

*	**`git config --global commit.template <DRIVE>:\<FILE-PATH>/git-commit-template.txt`**   

Example: **`git config --global commit.template C:\my-files/git-commit-template.txt`**   

---
