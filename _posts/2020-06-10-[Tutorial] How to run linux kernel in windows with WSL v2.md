---
layout:     post
title:      [Tutorial] How to run linux kernel in windows with WSL v2
subtitle:   Data Science Linux Environement Setup in Windows10  
date:       2020-06-10
author:     Mr.X
header-img: img/post-bg-wsl.jpg
catalog: true
tags:
    - tutorial
    - wsl
    - windows10
    - linux
    - english
---

# DataScience in windows 10

Dear Data Scientist, 

Do you still suffer from the "chaos evil" Windows operating system as your first dev place ?
- **git** doesn't work as what I expected...
- **ssh** connection failed and Putty looks stupid....
- **conda** works well at first but pip might get destroyed right after update...
- **Tensorflow** seems friendly to Windows, a lot pretrained models in tensorhub can be used only in Linux kernel....
- Or just get **tired of windows** ? 

Here is some Good News:
- **WSL2** is totally different from the first version. It has a full capacity linux kernel. 
- Many available Linux Kernels: SUSE / Debian / ubuntu / etc... 

Here, I've got a full tutorial for how to use Windows Subsystem Linux version 2 (WSL2) with VS code 

Linux on Windows, here we go !

Good luck !

## Table of Content

- [DataScience in windows 10](#datascience-in-windows-10)
  - [Table of Content](#table-of-content)
  - [What is this WSL ?](#what-is-this-wsl-)
  - [Tutorial 1 : Get your WSL2 and install Linux distribution](#tutorial-1--get-your-wsl2-and-install-linux-distribution)
    - [1. Update Windows 10](#1-update-windows-10)
    - [2. Install and Set WSL-2](#2-install-and-set-wsl-2)
    - [3. Install Linux Distribution from Microsoft Store](#3-install-linux-distribution-from-microsoft-store)
  - [Tutorial 2 : Set up Data Science Environment in WSL2](#tutorial-2--set-up-data-science-environment-in-wsl2)
    - [1. Configuration for WSL](#1-configuration-for-wsl)
    - [2. Configuration for Windows 10](#2-configuration-for-windows-10)
      - [Download VS code in Windows 10](#download-vs-code-in-windows-10)
      - [Configure Extension for WSL in VS code](#configure-extension-for-wsl-in-vs-code)
  - [Tutorial 3 : Best Terminal (Option)](#tutorial-3--best-terminal-option)
  - [Tutorial 4 : Work with git and ssh (Option)](#tutorial-4--work-with-git-and-ssh-option)
  - [TODO list](#todo-list)
  - [Some Links](#some-links)


## What is this WSL ?
> wikipedia : [WSL](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux)  


![Image of WSL](img/WSL-2-Architecture.jpg)

Intuitively, the WSL2 is a lightweight Linux Vitual Machine based on the Hypervisor, same as Windows. 

Advantages is: 
- Almost full featured Linux
- Shared RAM and ROM, 
- CUDA available 

Disadvantage is : 
- Linux Distro can only stay at your Disk-C...(you might need a big "C:\\")

(I don't know much about operating system, tell me if I say something wrong xD)

## Tutorial 1 : Get your WSL2 and install Linux distribution

**IMPORTANT** : 
* Windows 10 s can't have a WSL !!!! Buy a pro version key, pls (or hack it...)
* If you have already had a WSL version 1, this tutor does work for your case ! 

### 1. Update Windows 10

Check Windows version
```
Open Run :  win + R 
type : winver  
select : OK
```
![Image of Windows_version](img/win_version.PNG)

if Windows 10 version is lower than version 2004, Build 19041.
- Use [Get Windows Update Assitant](https://www.microsoft.com/software-download/windows10)


### 2. Install and Set WSL-2

Go to windows setup, and turn on the Developer Mode 

![Image of dev_mode](img/dev_mode.PNG)

It will take a couple of time.  Don't worry! 

After that: 

Open PowerShell as Admin 

- Run following command to enbale WSL

```PowerShell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

- Run followeing commande to enable Virual Machine Platform for WSL-2

```PowerShell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

PS : you may need to **restart** your machine for several times, it's ok !

- Run following commande to Set WSL 2 as default 

```PowerShell
wsl --set-default-version 2
```

### 3. Install Linux Distribution from Microsoft Store

Choice what u want and install it! 

![MS store](img/win_store.PNG)


**PS** : Then, Initialize the distro,  if u want some helps:
- [ create a user account and password for your new Linux distribution.](https://docs.microsoft.com/en-us/windows/wsl/user-support)

When Linux Distro installed successfully, you will see it:

![ubuntu](img/ubuntu.PNG)

## Tutorial 2 : Set up Data Science Environment in WSL2

### 1. Configuration for WSL

Run following to install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) and useful libraries

```bash
$ wget  https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
$ bash Miniconda3-latest-Linux-x86_64.sh

# install jupyter and commun packages
$ conda install jupyter
$ pip install urllib requests pandas scikit-learn matplotlib seaborn plotly tensorflow 
```


### 2. Configuration for Windows 10
#### Download VS code in Windows 10
- [download VS Code](https://code.visualstudio.com/)

#### Configure Extension for WSL in VS code 
Install Some Extensions:
- Remote - WSL
- Anaconda Extension Pack (Optional)
- GitHub (Optional)
- .NET Install Tool (Optional)

With the Remote-WSL extension, we can get into the Linux SubSystem and work on it!  

Click Here and connect to your WSL2 in a New Windows

![VS code](img/Remote_WSL.PNG)

If connection goes well, you will see

![VS code](img/Remote_WSL2.PNG)

Then re-install those Extensions in your WSL

![VS code](img/VS_code.PNG)

**Congratulations, your Linux Env is ready for you !**

## Tutorial 3 : Best Terminal (Option)

As for 


## Tutorial 4 : Work with git and ssh (Option)
todo


## TODO list

- [x] Install WSL
- [x] Configuration WSL and Windows10
- [ ] Windows Terminal (Preview)
- [ ] git and ssh


## Some Links

- [Microsoft WSL2 FAQ](https://docs.microsoft.com/en-us/windows/wsl/wsl2-faq)
- [Microsoft : Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
- [conda managing environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
- [windows terminal schemes](https://docs.microsoft.com/en-us/windows/terminal/customize-settings/color-schemes)
- [CUDA in WSL](https://developer.nvidia.com/cuda/wsl)