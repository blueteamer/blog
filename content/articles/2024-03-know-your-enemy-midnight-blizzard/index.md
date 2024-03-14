---
draft: false
toc: false
title: 'Know your Enemy: Midnight Blizzard'
description: 'An overview and some facts about the russian group formerly known as NOBELLIUM.'
date: 2024-03-14
usePageBundles: true
categories: ['article'] 
tags: ['midnight blizzard','apt29','cozy bear','nobellium'] 
---
 
 
Midnight Blizzard, also known as APT29 and Cozy Bear, is a nation-state threat group powered by the russian foreign intelligence service (SRV)[^fn1]. This threat actor employs diverse tactics, techniques, and procedures (TTPs) to infiltrate target networks, compromising both organizations and individuals. Midnight Blizzard's arsenal includes phishing campaigns, password spray attacks, abuse of trusted relationships (MSP/CSP/Vendors), and exploitation of vulnerabilities in various software and services. 
 
[^fn1]: Similar to the German BND. 

<!--more-->
***

## Tactics, Techniques, and Procedures (TTPs)

Midnight Blizzard's TTPs encompass a wide array of methods aimed at infiltrating target networks and achieving their objectives:

- Password spray attacks
- Use of malicious attachments or links in phishing campaigns
- Abuse of trusted CSP/MSP relationships
- Delivery of malicious payloads via ISO files (html dropper in email attachment)
- Compromise of legitimate email addresses for phishing attacks
- Abuse of target's trusted relationships (supplier and partners)
- Exploitation of delegated administrative privileges (DAP)
- Modification of Azure Active Directory (AAD) for persistence and access
- Acquisition of domains using domain seasoning
- Use of dedicated infrastructure for anonymization
- Leveraging of legitimate services for hosting malicious content (DropBox)
- Implementation of supply chain compromises (Solarwind)
- Use of stolen Azure AD session tokens for initial access (private devices accessing company resources)
- Use of stolen AD FS keys for forging SAML tokens
- Exfiltration of data over C2 channels
- Acquisition of additional credentials for accessing email data
- Manipulation of existing privileged applications for exfiltration

## Known malware and vulnerabilities 

Midnight Blizzard is known for using the following malware, tools and vulnerabilities to gain access to the victim's environment. This list is by far not complete. 

### Malware
- BoomBox - A malicious downloader
- EnvyScout - A Stage 1 malicious payload
- FoggyWeb - Malware for targeting and extracting data from AD FS servers
- GoldFinder - A custom HTTP tracer tool
- GoldMax - A Stage 2 command-and-control (C2) backdoor
- Sibot - Malware used for persisting on a targeted system
- NativeZone - A malicious loader used to load malicious content
- VaporRage - Malicious downloaders dropped during initial access
- CCleaner - Malicious payload disguised as 'legit' software 


### Vulnerabilities
- VMware Workspace One Access (CVE-2020-4006)
- Citrix Application Delivery Controller (CVE-2019-19781)
- Pulse Secure Pulse Connect Secure (CVE-2019-11510)
- Synacor Zimbra Collaboration Suite (CVE-2019-9670)
- Fortinet FortiOS (CVE-2018-13379)

## Mitigation Strategies

To mitigate the risk posed by Midnight Blizzard and safeguard against their malicious activities, organizations can implement the following mitigation strategies:

- Security Awareness Training: Educate employees about the dangers of phishing attacks and the importance of exercising caution when interacting with emails containing attachments or links.
- Multi-Factor Authentication (MFA): Implement MFA to add an extra layer of security to user accounts, making it more difficult for threat actors to gain unauthorized access.
- Patch Management: Regularly update software and services to address known vulnerabilities and reduce the likelihood of exploitation by threat actors.
- Network Segmentation: Segment networks to limit the lateral movement of threat actors within the network, thereby containing potential breaches and minimizing the impact of their activities.
- Monitoring and Detection: Deploy advanced threat detection systems capable of identifying and responding to suspicious activities indicative of Midnight Blizzard's TTPs.
- Conditional Access Policies: Restrict access to company resources by using tailored policies. 


## Sources
- [Microsoft: "Microsoft Defender for Threat Intelligence - Intel Profiles: Midnight Blizzard"](https://ti.defender.microsoft.com/intel-profiles/d825313b053efea45228ff1f4cb17c8b5433dcd2f86353e28be2d484ce874616/tradeCraft)
- [Mandiant: "Backchannel Diplomacy: APT29’s Rapidly Evolving Diplomatic Phishing Operations"](https://www.mandiant.com/resources/blog/apt29-evolving-diplomatic-phishing)
- [Polish Government: "Espionage campaign linked to Russian intelligence services"](https://www.gov.pl/web/baza-wiedzy/espionage-campaign-linked-to-russian-intelligence-services)



  
