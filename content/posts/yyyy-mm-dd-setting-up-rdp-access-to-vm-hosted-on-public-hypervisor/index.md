---
title: "Setting Up Rdp Access to Vm Hosted on Public Hypervisor"
date: 2023-06-18T07:49:48+02:00
draft: true
---




[ClientDevice] (device directly in front of you)

[Hypervisor] (public facing) 156.100.100.101

[VM] (running on interal network on HyperVisor | 10.0.0.23)


Right now, I RDP to the HyperVisor and - again - open RDP on the HyperVisor to access my VM. 

I want to access my VM directly from my ClientDevice, without loggin in to my HyperVisor. 

How to do that? 

Configure portforwarding on the HyperVisor. 
RDP will be opened on the ClientDevice against the HyperVisor with a dedicated port. RDP request is forwarded on the HyperVisor to the VM. User logs in to the VM. VM can be used on the ClientDevice directly without logging in to the HyperVisor. 

Configure portforwarding on the HyperVisor. 

1. Login in to your HyperVisor 
1. Open a PowerShell as Admin 
1. You need four info 
    1. local IP (the public IP of the HyperVisor)
    1. Port for RDP that will be used from external (can be any non-used port of your favor)
    1. IP of the VM 
    1. RDP port used on the VM (default 3389) 
1. Test if the RDP port used from external is already in use 
Test-NetConnection -Computername localhost -Port 39393 
Result will show you if port is already in use. In this case, choose a different one. 
1. Configure portforwarding for your chosen port 
netsh interface portproxy add v4tov4 listenaddress=<your public facing IP of the HyperVisor> listenport=<the port you have chosen to connect to RDP> connectaddress=<IP of the VM> connectport=<RDP port on VM - default 3389>
1. Add firewall rule to access the forwarded rule from external 
netsh advfirewall firewall add rule name="a good name for the rule so you know what it is for" protocol=TCP dir=in localip=<your public facing IP of the HyperVisor> localport=<the port you have chosen to connect to RDP> action=allow 
1. Test the connection from your ClientDevice 
Test-NetConnection -Computername <your public facing IP of the HyperVisor> -Port <the port you have chosen to connect to RDP> 

mstsc /v <your public facing IP of the HyperVisor>:<the port you have chosen to connect to RDP> 

This will lead you to the sign-in window of the VM running on your HyperVisor. 

This is a quick and dirty solution for accessing a lab VM hosted on a HyperVisor. 