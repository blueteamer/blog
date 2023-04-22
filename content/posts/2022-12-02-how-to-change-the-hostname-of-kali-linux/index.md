---
title: "How to Change the Hostname of Kali Linux"
date: 2022-12-02T00:00:00+01:00
draft: false
tags: 
- Kali linux
- Linux 
---

Changing the device hostname under Kali Linux is pretty straightforward. Read here how to do that. 

<!--more-->

### Some assumptions 
Let's assume the current device name is **attackbox**, and we want it to be changed to **thedestroyer**. 

### How to do it 
Switch to a terminal on your Linux device and type the following statements. 

```
hostname
```
*hostname* will show you the current hostname of the device. In our case, it should be **attackbox**. 

Next, open the files **hostname** and **hosts** and exchange the value **attackbox** with **thedestroyer**. 

```
sudo nano /etc/hostname 
sudo nano /etc/hosts
```

Finally, reboot the device with 
```
sudo reboot
```

That's it. Done. 
So long... 

