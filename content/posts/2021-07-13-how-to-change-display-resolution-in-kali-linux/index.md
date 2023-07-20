---
title: "How to change display resolution in Kali Linux"
date: "2021-07-13"
description: "Read how to change the display resolution for kali linux. " 
featured: false 
draft: false 
toc: true 
# menu: main
usePageBundles: true 
categories:
  - "unrelated stuff"
tags:
  - linux 
  - troubleshooting

---



When you install Kali Linux as a Hyper-V VM the default display resolution is 1024x786. This is too small to work on. 
I found some good info on how to do change the display resolution for Kali on YouTube[^fn1] and decided to summarize the steps here for your convenience. 

<!--more-->

## Change the resolution
The steps are fairly easy: 
- modify the grub configuration file 
- update grub 
- restart the device 


We have to make a modification to a config for grub and restart the machine.  
Therefore go to your Kali Linux machine and open a terminal.

### Modify the grub configuration file 
Open a terminal on your linux device and open the grub configuration file in nano or any other editor of your choice. 

```bash
sudo nano /etc/default/grub 
```

Now have a look for this line 
```vim
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

It is possible that there are more parameters after "quiet". But this is the line we need to modify.  
So change this line as follows:

```vim
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=hyperv_fb:1920x1080"
```

**Info** | In my case I switched the resolution to 1920x1080. I haven't tested any higher resolutions. So, can't tell if it's working with higher numbers.  
Let me know if you have any experience with that.

Save the modification with nano's shortcuts **Ctrl+X** and confirm with **y**.

### Send the updated config to grup 
After we made the modification of the grub config file, we need to tell grub about these changes. Do that with the statement here: 

```bash
sudo update-grub
```

### Restart your device 
In the last step, we do a restart of the Kali Linux machine. The new settings should apply and you'll now have way more place on your desktop.

Enjoy.

[^fn1]: [Change Kali Linux screen resolution on Hyper-V Virtual Machine](https://www.youtube.com/watch?v=N8K9qnd5NT8) (Youtube: HERESJAKEN)
