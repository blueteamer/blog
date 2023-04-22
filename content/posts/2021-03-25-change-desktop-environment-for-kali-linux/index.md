---
title: "Change desktop environment for Kali Linux"
date: "2021-03-25"
tags: 
  - Kali Linux
---

Linux is highly customizable. This is also true for selecting different desktop environments. In this post we will discover how to change a desktop environment on Kali Linux. 

<!--more-->

Installing additional desktop environments on Linux can easily be done via **apt**. I found the initial info on **linuxconfig.org[^fn1]**.

## Installing additional desktop environments for Kali Linux
The default desktop environment for Kali is **xfce**. And it's a pretty cool environment. Lean, lightweight, straightforward and functional. But sometimes you want some extra fancy stuff or try out something different. 

As mentioned before, the installation will be done via **apt**. We will see the installation for KDE and GNOME and also how to remove an existing desktop from your device. 

### Installing the new environment 
So let's start.  
Log into your Kali Linux and start a terminal. We will then update the install package directory and install the environment.

#### KDE
```
sudo apt update 
sudo apt install kali-desktop-kde 
```

#### GNOME 
```
sudo apt update
sudo apt install kali-desktop-gnome
```

#### Selecting the proper Desktop Manager 
Now some installation magic will happen. Until you will be asked which display manager you want to use.  
Select sddm (for KDE) or gnome3 (for Gnome).

Once again some installation magic will fight dragons in the background.  

As soon as you have the regular prompt in the terminal which indicates that the install process has been finished, type

```
reboot
```

to restart the machine.

### Enjoy your new environment 
After the reboot you will be prompted for your credentials. In the lower left corner you can select which desktop environment you want to use.  
Select Plasma (that's the KDE desktop) or GNOME. 

### Removing an existing environment 
As there are some known issues if you have Xfce and KDE installed at the same time, we might get rid of Xfce.  
To do so use those commands

```bash
sudo apt remove kali-desktop-xfce xfce4* lightdm* 
sudo apt autoremove 
```

Hope you enjoyed reading and trying out something new with your Kali machine.  
So long...

[^fn1]: (sic) "How to install KDE deskstop on Kali Linux" | linuxconfig.org, accessed 21 March 2021, [https://linuxconfig.org/how-to-install-kde-dekstop-on-kali-linux](https://linuxconfig.org/how-to-install-kde-dekstop-on-kali-linux)

