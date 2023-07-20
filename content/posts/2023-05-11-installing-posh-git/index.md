---
title: "Installing Posh-Git" 
date: "2023-05-10"
description: "Learn how to implement posh-git in your daily console." 
featured: false 
draft: false 
toc: true 
# menu: main
usePageBundles: true 
categories: ["unrelated stuff"]
tags: ["posh-git", "customization"]

---

If you are heavily using powershell and git, you might also want to have a look at **posh-git**. 
<!--more-->

## Prerequisites 
- min. PowerShell Core 6.0 or PowerShell 5.x 
- min. Git version 2.28.0.windows.1
- PowerShellGet 

### Check PowerShell version 
You can check the PowerShell version by using the following variable: 
```PowerShell
$PSVersionTable 
```

Output: 
```PowerShell
Name                           Value
----                           -----
PSVersion                      5.1.22621.963
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.22621.963
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

### Check if Git is installed 
Try to call the git command in a shell session. 
```PowerShell
git --version
```

If git is already installed, the output wil look something like this: 
```Powershell
git version 2.40.1.windows.1
```

In case git is not installed, the command will result in an error. If this happens, install git with **winget**: 
```powershell
winget install git.git
```

### Install PowerShellGet 
This is a PowerShell module, that will help you install additional PowerShell modules. 
```powershell
Install-Module powershellget -force 
```

It is possible that you might need to change the execution policy for PowerShell first. In our example we will do this change for the current user, only. 
```powershell 
Set-ExecutionPolicy remotesigned -Scope currentuser -Confirm
```

## Install Posh-Git 

### Install posh-git via powershellget
```powershell
powershellget\install-module posh-git -scope currentuser -force 
```

The next step is updating the package 
```powershell
powershellget\update-module posh-git 
```

Now, we can load the module with 
```powershell
Import-Module posh-git
```

As soon as you navigate to a folder with a git-managed repository on your device, the prompt will change and notify you about the current status of the repo. 

*In this example: One file was added, one was modified.*

```powershell
D:\github\blog [main ≡ +1 ~1 -0 !]>
```

### Persist the loading of posh-git 
Right now you need to call ```Import-Module posh-git``` each time you start a new PowerShell session to use posh-git. That's... not efficient. 

Posh-Git provides a function for that. 

```powershell
Add-PoshGitToProfile -CurrentUser
```

## Conclusion 
Enjoy! 


## Source 
[GitHub "Posh-Git"](https://github.com/dahlbyk/posh-git)



