---
title: "2023 04 20 Use Remnux on Windows With Wsl"
date: 2023-04-19
draft: false
tags: 
- REMnux
- Lab
- Malware Analysis
---

In case you frequently need to investigate suspicious files or you need more context about such files, you should take a look at REMnux[^fn1]. It is a linux distribution specifically used for malware analysis and digital forensics. 

We are going to have a look at how REMnux can be installed on a Windows 10 device. The goal is to extend the analysis capabilities of a Windows 10 detonation chamber. 

[^fn1]: You can find more information about REMnux and how to use it on [remnux.org](https://remnux.org) 


## Prepare Windows for REMnux installation  
Since Window 10 we have the WSL feature available. The Windows Subsystem for Linux (WSL) is a virtualization solution to let Windows host Linux distributions. This offers you a nice amount of additional tools to the tip of your fingeres while still sitting in a Windows environment.

WSL is a Windows feature that needs to be activated first. 

### Setting up WSL on Windows 
As the Windows Subsystem for Linux is a Windows feature, it is pretty easy to enable the feature via the feature context menu.

- Activate Windows Subsystem for Linux on Windows Host System
- Install **Kernel Update Package[^fn2]** on Host System

[^fn2]: Additional information on how to install the "Kernel Update Package" for WSL [https://learn.microsoft.com/en-us/windows/wsl/install-manual](https://learn.microsoft.com/en-us/windows/wsl/install-manual)

### Install Ubuntu 20.04 on WSL 
We need to install Ubuntu 20.04 in order to use the REMnux tool set. There are still some dependencies which will not work properly with the latest version of Ubuntu. Nevertheless, you should install the latest security updates for the 20.04 release.

In a powershell/terminal console type: 

```
wsl --install -d Ubuntu-20.04 
```

### First run 
- select a user name and a password
- the password is used for elevated activities (root context)

### Update distro 
```
sudo apt update 
sudo apt upgrade 
```

### Install Python2
In case Python2 is not available in the instance, install it via "apt install"

```
sudo apt install python2-minimal 
```

## Install REMnux toolset 
REMnux provides an installer on their web site. 
- Download the installer[^fn4] 
- make the script generally available 
- make the script executable 
- call the script explicitly with **--mode=addon** 

[^fn4]: [https://remnux.org/remnux-cli](https://remnux.org/remnux-cli)

```
# Download REMnux Installer 
wget https://remnux.org/remnux-cli

# rename and relocate script to bin 
mv remnux-cli /usr/local/bin/remnux 

# make the script executable 
chmod +x /usr/local/bin/remux 

# execute installer as root 
sudo remnux install --mode=addon 
```

## Conclusion 
Installing REMnux on Windows Subsystem for Linux is fairly simple and provides a huge set of tools to do forensics and malware analysis. 

I'll try to write about some of those tools in future posts. In the meanwhile: Stay tuned. 

So long... 



