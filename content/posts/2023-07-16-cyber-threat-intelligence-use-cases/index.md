---
title: "Cyber Threat Intelligence Use Cases" 
date: "2023-07-16"
description: "Common use cases for implementing Threat Intelligence feeds. " 
featured: false 
draft: false 
toc: true 
# menu: main
usePageBundles: true 
categories: ["security operations"]
tags: ["threat-intel", "sentinel"]

---



Introducing some common use-cases for implementing Threat Intelligence.  

<!--more-->

## Key take-aways  
- CTI is the process of collecting, analysing and sharing info to face threats 
- Needs to be implemented as a process 
- Take a Use-case-centric approach 
- Make sure to know what you want 
- Examples of threat intelligence use cases  

## What is Threat Intelligence 
Cyber Threat Intelligence inherits the term Intelligence from the military. There, intelligence means the process of information gathering, processing, sharing and leveraging to fulfil a specific task. 

Cyber Threat Intelligence has a similar meaning: information will be collected, analysed, processed and distributed to enhance security measures. 

Cyber Threat Intelligence comes in different kinds of mediums. It can be an IOC, an analysis of a former incident or a PDF report about trends and forecasts about Threat Actors' intentions, tactics and patterns. 

## Implementation of Cyber Threat Intelligence

CTI is not a product on which one can pull a switch to turn it on. It is instead a process. 

The first tasks to accomplish and focus on are: 
- Requirements analysis (know what you want to achieve)
- Analysis of the environment and contextual position of the company (e.g.):  
	- What appliances are in use? 
	- What application might be vulnerable? 
	- What industry am I in? 
	- How does that affect my risk exposure?
- Derive actionable tasks to improve security posture 

## The pyramid of pain 

A standard categorisation of Cyber Threat Intelligence is the Pyramid of Pain. It describes given intel in three areas: 

### Tactical Intelligence 
   Tactical intelligence involves IOC with a short lifespan and is used for quick threat hunting, triage and incident response. So typically, that info will be needed in the day-to-day operations. 
   
### Operational Intelligence 
   You can consider information like Threat Actor profiles, analysis of incidents or detailed explanations of tactics, techniques and procedures. 
   
   This information will help an analyst better understand threat actors to improve detection. However, the management can also leverage this information to decide which parts of the environment might have security gaps and need to be covered. 
   
### Strategical Intelligence 
   The information provided in the context of strategic intelligence often comes as quarterly or annual reports and should help to make long-term decisions. 
   
   This intel is also used to carve awareness training and provide an overall education on the ongoing and current threat landscape. 

## Common use cases for Cyber Threat Intelligence 

### Threat hunting 
Threat hunting might be the most common use case for cyber threat intelligence data: Use them in detections. 

Take a list of confirmed malicious IPs and compare it against a list of IPs from your firewall, and you will see many findings. Therefore, those detections' quality needs proper fine-tuning to avoid unnecessary f/p. Also, the detection quality is directly dependent on the quality of the CTI data. 


### Incident enrichment 
Information from CTI feeds is used to support CSOC analysts with the proper context to decide whether an incident is a f/p or an imminent threat. 

#### Use Sentinel Playbooks 
If you are using Microsoft Sentinel, this can be implemented by using playbooks. 

In the playbook, the logic can process the entities out of the incident and enrich the incident by automatically adding contextual data from CTI data. 

#### Quicker response or even automation 
With that extra information provided to the analyst, the incident will be processed faster and more confidently. 

In the long run, it is possible to automate the incident response based on the additional information provided by the CTI data source. As there is more information available, the automation can be scoped way more granular. 


### Risk and vulnerability management 
As mentioned before, CTI data is not only IOC. It can also contain valuable reports about former or trending threats. That data includes current vulnerabilities as well. 

#### Make the best out of Notebooks  
Jypiter Notebooks or Sentinel Notebooks can help to combine the dynamic collection of data with a consistent look and feel for a report. 

Both can query the environment for known vulnerabilities. Combined with the likelihood of exploitation (CTI data), Notebooks can provide the vulnerability management stakeholder with helpful information to focus on which assets to patch first. 


### Educate C-Level about the current threat landscape 
The threat landscape is an ever-changing topic but also is affected by trends. These trends might be of interest for future investments to improve the security posture. 

#### Manual work needed  
Usually, this kind of intel will be provided as a manually curated report tailored to the company's specific needs. The report considers the industry, locations, security maturity of the company, and other topics relevant to the audience. 

#### Explore Sentinel Workbooks  
The goal is to improve the knowledge about the current threat landscape to make proper decisions in terms of security strategies. 

Depending on the information that needs to be shared with the audience, it can be helpful to have a look at Sentinel Workbooks for presenting combined data from the own environment and CTI.  


## Conclusion 
Unfortunately, cyber threat intelligence is a broad term. Hence, it is essential to prioritise the requirements and determine the goals that must be accomplished. 

After that, using CTI data - depending on the tasks - can be a valuable helper to improve the overall security posture. 

The only thing you should consider is that implementing CTI for security reasons is a circular process which needs continuous improvement. 