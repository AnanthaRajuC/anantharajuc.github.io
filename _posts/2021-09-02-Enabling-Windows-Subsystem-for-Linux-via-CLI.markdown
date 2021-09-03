---
title: "Enabling Windows Subsystem for Linux on Windows 10 with Ubuntu via CLI"
author: anantharajuc
categories: [ WSL, Operating System ]
tags: [ WSL, Operating System ]
layout: post
date: 2021-09-02 20:00
image: /assets/images/wsl.png
---

The **Windows Subsystem for Linux** lets developers run a **GNU/Linux** environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.

This post documents the process of enabling and manually installing Windows Subsystem for Linux on the **Windows 10** OS platform via CLI as described by Ubuntu [https://ubuntu.com/wsl](https://ubuntu.com/wsl).

Alternatively, check out this post on [Enabling Windows Subsystem for Linux on Windows 10 with Ubuntu via Settings GUI]({{ site.baseurl }}/Enabling-Windows-Subsystem-for-Linux-via-Settings-GUI/)  

---

#### Minimum Requirements

- Windows 10 Operating System 
- Windows PowerShell (*Run as administrator*)
---

#### Enable WSL

##### Enable WSL 1

```shell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

![Enable WSL 1]({{ site.baseurl }}/assets/images/wsl-cli/1-enable-wsl-1.PNG)   

##### Enable WSL 2

```shell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

![Enable WSL 2]({{ site.baseurl }}/assets/images/wsl-cli/2-enable-wsl-2.PNG)  

##### `Restart Computer`

#### Download and Install the WSL 2 Linux kernel from Microsoft

- [x86_64 - https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) for Intel and AMD devices.  
- [arm64 - https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi) for Snapdragon and other ARM devices.  

#### Set WSL 2 as the default WSL environment.

```shell
wsl.exe --set-default-version 2
```

![Enable WSL 2]({{ site.baseurl }}/assets/images/wsl-cli/3-set-swl-2-as-default.PNG) 

##### Installation of Linux distribution of your choice from Microsoft Store

![Ubuntu - Search]({{ site.baseurl }}/assets/images/wsl/12.PNG)  

![Ubuntu - Installation]({{ site.baseurl }}/assets/images/wsl/13.PNG)  

![Ubuntu - Launch]({{ site.baseurl }}/assets/images/wsl/14.PNG)  

Create a user account and password for your new Linux distribution. [*Details*](https://docs.microsoft.com/en-us/windows/wsl/user-support)  

![Ubuntu - Account]({{ site.baseurl }}/assets/images/wsl/17.PNG)  

This process concludes the installation and set up of a Linux distribution that is completely integrated with your Windows operating system!

---