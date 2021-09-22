---
title: "Enabling Windows Subsystem for Linux on Windows 10 with Ubuntu via CLI"
author: anantharajuc
categories: [ WSL, Operating System, Installation ]
tags: [ WSL, Operating System, Installation ]
layout: post
date: 2021-09-02 20:00
image: /assets/images/wsl.png
---

This post documents the process of enabling and manually installing Windows Subsystem for Linux on the **Windows 10** OS platform via CLI as described by Ubuntu [https://ubuntu.com/wsl](https://ubuntu.com/wsl).

Alternatively, check out this post on [Enabling Windows Subsystem for Linux on Windows 10 with Ubuntu via Settings GUI]({{ site.baseurl }}/Enabling-Windows-Subsystem-for-Linux-via-Settings-GUI/)  

---

#### Introduction

**Windows Subsystem for Linux** lets developers run a **GNU/Linux** environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.

**Ubuntu** is a Linux distribution based on Debian and composed mostly of free and open-source software.

---

#### Goals  

1. Enable WSL 
	1.1 Enable WSL 1  
	1.2 Enable WSL 2  
	1.3 Restart Computer  
2. Download and Install the WSL 2 Linux kernel from Microsoft  
3. Set WSL 2 as the default WSL environment  
4. Installation of Linux distribution of your choice from Microsoft Store  
	4.1 Search for Ubuntu Distribution
	4.2 Install the Ubuntu Distribution
	4.3 Launch the newly installed Ubuntu Distribution
	4.4 Setup an Account
	
---

#### Minimum Requirements

- Windows 10 Operating System 
- Windows PowerShell (**Run as administrator**)

---

#### **`Step 1 - Enable WSL`** 

##### **`Step 1.1 - Enable WSL 1`** 

```shell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

![Enable WSL 1]({{ site.baseurl }}/assets/images/wsl-cli/1-enable-wsl-1.PNG)   

---

##### **`Step 1.2 - Enable WSL 2`** 

```shell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

![Enable WSL 2]({{ site.baseurl }}/assets/images/wsl-cli/2-enable-wsl-2.PNG)  

---

##### **`Step 1.3 - Restart Computer`** 

---

#### **`Step 2 - Download and Install the WSL 2 Linux kernel from Microsoft`** 

- [x86_64 - https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) for Intel and AMD devices.  
- [arm64 - https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi) for Snapdragon and other ARM devices.  

---

#### **`Step 3 - Set WSL 2 as the default WSL environment`** 

```shell
wsl.exe --set-default-version 2
```

![Enable WSL 2]({{ site.baseurl }}/assets/images/wsl-cli/3-set-swl-2-as-default.PNG) 

---

#### **`Step 4 - Installation of Linux distribution of your choice from Microsoft Store`** 

##### **`Step 4.1 - Search for Ubuntu Distribution`** 

![Ubuntu - Search]({{ site.baseurl }}/assets/images/wsl/12.PNG)  

---

##### **`Step 4.2 - Install the Ubuntu Distribution`** 

![Ubuntu - Installation]({{ site.baseurl }}/assets/images/wsl/13.PNG)  

---

##### **`Step 4.3 - Launch the newly installed Ubuntu Distribution`** 

![Ubuntu - Launch]({{ site.baseurl }}/assets/images/wsl/14.PNG)  

---

##### **`Step 4.4 - Setup an Account`** 

Create a user account and password for your new Linux distribution. [*Details*](https://docs.microsoft.com/en-us/windows/wsl/user-support)  

![Ubuntu - Account]({{ site.baseurl }}/assets/images/wsl/17.PNG)  

---

##### **`Conclusion`** 

This process concludes the installation and set up of a Linux distribution that is completely integrated with your Windows operating system!

---