---
title: "Installing OnionShare on Kali Linux"
date: "2021-09-22"
tags: 
  - Kali Linux
  - OnionShare 
---
---
title: "How to change display resolution in Kali Linux"
date: "2021-07-13"
description: "Read how to change the display resolution for kali linux. " 
featured: false 
draft: false 
toc: true 
# menu: main
usePageBundles: true 
categories: ["unrelated stuff"]
tags: ["linux", "onionshare"]

---

OnionShare is a file sharing solution with a heavy focus on privacy. You might have heard of it in combination with news articles related to whistleblower and dataleaks. 

<!--more-->

## OnionShare on Kali Linux 
I expected OnionShare to be installed on Kali Linux out of the box; but it is not. To have OnionShare work properly, we need to install **snapd[^fn1]** and **OnionShare[^fn2]**. 

This write-up is a summary of the two mentioned resources, which describe the installation of **snapd** and **OnionShare**. 

[^fn1]: Installing snapd on Kali Linux [kali.org](https://www.kali.org/docs/tools/snap/)

[^fn2]: Install OnionShare on Debian [snapcraft.io](https://snapcraft.io/install/onionshare/debian)

### Installing snapd via apt

```
sudo apt update 
sudo apt install -y snapd
```

Now we have to enable snapd as service, so we don't have to start the service manually after each and every reboot. 

```
sudo systemctl enable --now snapd apparmor
```

**Note |** The documentation of Kali Linux recommends a reboot or at least a logout to have everything run properly.

```
reboot
```

### Installing OnionShare
Next, we're going to install the required binaries.

```
sudo snap install core
sudo snap install onionshare
```

![](images/2021-09-22_20h38_10-1024x753.png)

That's it. And now: Happy sharing!


 

