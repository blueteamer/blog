---
draft: false
toc: true
title: 'The clear and present danger of Octo Tempest'
description: 'This article will cover an overview and common TTPs of the APT group Octo Tempest. '
date: 2024-03-13
usePageBundles: true
categories: ['article'] 
tags: ['octo tempest','muddled libra','scattered swine','star fraud','unc3944','scattered spider','social engineering','ransomware','black cat'] 
---
 
 
Octo Tempest is a financially motivated collective of native English-speaking threat actors known for conducting extensive social engineering campaigns and employing advanced TTPs to compromise organizations globally. Their activities include extortion, encryption, and destruction, targeting industries such as telecommunications, technology, hospitality, and financial services. 

To defend against Octo Tempest, organizations must implement robust security measures, including continuous monitoring, privilege alignment, and user education. Here, we delve into the tactics, techniques, and procedures (TTPs) employed by Octo Tempest, shedding light on their modus operandi and providing insights into their evolving threat landscape.
 
<!--more-->
***
 
## Summary of Octo Tempest's Operations

Octo Tempest's activities span multiple industries, initially targeting sectors such as software automation, outsourcing, and telecommunications. However, their scope has since expanded to include technology, business process outsourcing, hospitality, and financial industries, showcasing their adaptability and persistence. Microsoft as well as Unit 42 researchers have traced their activities from mid-2022 to early 2024, witnessing a shift from structured attacks on business process outsourcing firms to a ransomware affiliate model with extortion as their primary objective.

## Fluid Tactics and Adaptable Techniques

At the core of Octo Tempest's operations lies their agility in adapting tactics to suit their target environments. Social engineering remains their primary modus operandi, often targeting IT help support desks to gain initial access. They exhibit a mastery of various techniques, including:

- NSOCKS and TrueSocks Proxy Services: Octo Tempest employs proxy services to obfuscate their activities and evade detection.
- Email Rule Manipulation: By creating rules to forward emails from specific security vendors, they monitor communications and impede investigations.
- Custom Virtual Machine Deployment: They deploy custom virtual machines within targeted environments, leveraging them for persistence and stealth.
- Utilization of Rootkit Tools: Octo Tempest employs open-source rootkit tools like bedevil (bdvl) to target VMware vCenter servers and gain unauthorized access.
- Anonymizing Proxy Services: Heavy reliance on anonymizing proxy services helps conceal their identity and geographic location.
- Social engineering attacks targeting technical administrators.
- SMS phishing campaigns to lure employees into visiting fake login portals.
- Compromising security personnel accounts to disable security products and evade detection.
- Leveraging publicly available security tools to establish persistence within victim organizations.
- Using advanced techniques such as Golden SAML to maintain access to endpoints.
- Data theft, extortion, and ransomware deployment as their primary objectives.

Furthermore, Octo Tempest demonstrates a sophisticated understanding of English, enabling them to conduct social engineering attacks with fluency. They've even leveraged AI to spoof victims' voices, showcasing a nuanced approach to deception. 

## Procedure and Approach

Octo Tempest exhibits a methodical approach to their attacks, leveraging an extensive toolkit that ranges from social engineering to niche penetration testing and legitimate systems management software. Their flexibility in pivoting between attack vectors and modifying tactics in response to defensive measures makes them a formidable adversary. 

The threat group was observed in quickly reacting to defenders actions in terms of laterally moving between compromised devices to prevent a lock out. Though dwell times have been known to be quite long with weeks or months between network compromise and agitation, Octo Tempest tends to act way quicker and getting domain dominance within 3h in one case. 

## The Attack Chain Unveiled

Mapping their operations onto the MITRE ATT&CK framework reveals a comprehensive attack chain:

- Reconnaissance: Octo Tempest demonstrates an intimate knowledge of targeted organizations, IR adn administration processes, leveraging illicit data brokers[^fn1] [^fn2] and previous breaches for intelligence gathering.
- Initial Access: They employ smishing and helpdesk social engineering to gain initial entry, often bypassing multi-factor authentication (MFA) through convincing tactics.
- Persistence: The group maintains access through a plethora of remote monitoring and management tools, ensuring a backdoor into the environment.
- Defense Evasion: Octo Tempest adeptly evades security controls, disabling antivirus, and firewalls, and using anonymizing services to obscure their activities.
- Credential Access: Once inside, they exploit compromised credentials, utilizing tools like Mimikatz and Raccoon Stealer for privilege escalation.
- Lateral Movement: Remote Desktop Protocol (RDP) connections from compromised computers facilitate lateral movement within the target environment.
- Collection and Exfiltration: The group targets sensitive data across various repositories, staging and exfiltrating it using legitimate file transfer sites and tools.

[^fn1]: [United Health data breach in 2023](https://eu.usatoday.com/story/news/health/2024/03/05/unitedhealth-cyberattack-disrupts-records-billing-security/72849687007/) 
[^fn2]: [Two massive healthcare data breaches just exposed more than half of France's population](https://www.itpro.com/security/data-breaches/two-massive-healthcare-data-breaches-just-exposed-more-than-half-of-frances-population)

## Impact and Mitigations

The impact of Octo Tempest's attacks ranges from data theft to operational disruption and encryption of critical data. To mitigate their threat, organizations are advised to implement multi-factor authentication (MFA), comprehensive user awareness training, and strict access controls. Leveraging modern security architectures and solutions, such as Next-Generation Firewalls (NGFW) and eXtended Detection and Response (XDR), can further bolster defenses against such sophisticated adversaries.

## Mitigations
To defend against Octo Tempest, organizations should consider the following mitigation strategies:

- Implement robust identity and access management policies, including multifactor authentication and privileged identity management.
- Segment Azure landing zones and tightly control access to critical workloads.
- Deploy Conditional Access policies to enforce security controls and authentication methods.
- Develop and maintain a user education strategy to raise awareness of common cyber threats.
- Use out-of-band communication channels to mitigate risks associated with threat actor communication.
- Utilize threat detection tools such as Microsoft Defender to identify and respond to malicious activity promptly.

In conclusion, understanding the tactics, techniques, and procedures of threat groups like Octo Tempest is crucial for developing effective cybersecurity strategies. By staying vigilant and employing proactive defense measures, organizations can better safeguard their digital assets against evolving cyber threats. 

## IoC and artefacts 
- 104.247.82[.]11
- 105.101.56[.]49
- 105.158.12[.]236
- 134.209.48[.]68
- 137.220.61[.]53
- 138.68.27[.]0
- 146.190.44[.]66
- 149.28.125[.]96
- 157.245.4[.]113
- 159.223.208[.]47
- 159.223.238[.]0
- 162.19.135[.]215
- 164.92.234[.]104
- 165.22.201[.]77
- 167.99.221[.]10
- 172.96.11[.]245
- 185.56.80[.]28
- 188.166.92[.]55
- 193.149.129[.]177
- 207.148.0[.]54
- 213.226.123[.]104
- 35.175.153[.]217
- 45.156.85[.]140
- 45.32.221[.]250
- 64.227.30[.]114
- 79.137.196[.]160
- 92.99.114[.]231

## Sources 
- [Octo Tempest crosses boundaries to facilitate extortion, encryption, and destruction](https://www.microsoft.com/en-us/security/blog/2023/10/25/octo-tempest-crosses-boundaries-to-facilitate-extortion-encryption-and-destruction/)
- [Octo Tempest Threat Actor Profile](https://thecyberwire.com/podcasts/microsoft-threat-intelligence/5/notes)
- [Threat Group Assessment: Muddled Libra](https://unit42.paloaltonetworks.com/muddled-libra/)