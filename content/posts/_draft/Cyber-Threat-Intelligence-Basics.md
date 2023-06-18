---
title: "Introducing the Cyber Threat Intelligence lifecycle"
date: 2023-05-10T16:55:53+02:00
tags: 
- Cyber Threat Intelligence 
draft: true
---


Processing data and signals in the context of cyber threat intelligence follows a fundamental principle. This is called the lifecycle of intelligence. 
<!--more-->

## Lifecycle of intelligence 

Like other lifecycles, the intelligence lifecycle builds up a loop with several steps. 

{{< mermaid >}}
flowchart LR 
    A(Planning </br> and </br> Direction) --> B(Collection)
    B --> C(Processing)
    C --> D(Analysis </br> and </br> Production)
    D --> E(Dissemination)
    E --> F(Utilization)
    F --> A
{{< /mermaid >}}

### Planning and Direction 

During the planning and direction phase, the CTI team will define the **Primary Intelligence Requirement** and other Intelligence Requirements. 

What does that mean? Before you can work on a solution or start researching, you need to know the problem or the question to answer. The **intelligence requirement** is this question. 

The priority will help to focus on the most critical goal in case of limited resources. 

Additionally, the team will have a look at its collection-gathering capabilities. Which other groups and sources can we use to gather data? 

Of course, there are other things to consider during the planning phase - most of them heading toward management topics. We won't go there for the moment. 

- define intelligence requirements (including primary intel requirement)
- prioritize the requirements to tackle resource shortage 
- check out data-gathering capabilities 
- define what data sources will be used 
- collect all the "what I want to know" from all stakeholders involved 

### Collection 

The next step is gathering data to work with. These data can come from a lot of different sources. Other feeds, OSINT or own investigations of customers' environments can be a good starting point. 

In the best-case scenario, you can do the gathering automatically. But the manual collection of data is also typical for more minor engagements. 

- collect data from data sources (vuln management, incident response, monitoring team, IT operations, DFIR)
- get data grouped for each requirement defined in step one (1). 

### Processing 

As the data collection will come from a lot of different sources, the data needs to be standardized by any kind. 

First step is to store all the data in a structured format. This enables us to transform the data into an actual usable state. 

- collected data needs to be transformed in a structured format for further access 
- e.g. database or other structured form 
- data will be mapped on correlating points to see patterns and references 
- raw data will be converted in a way we can work with and all entries are in the same format 

### Analysis and Production 

Following the guidance of the question defined in the first step, the analyst uses the data to prepare an answer and g

- this steps outcome is a analysis product (e.g. report, dashboard, tile card, what-ever-floats-your-boat) 
- data will be processed, analyzed, interpreted and enriched 
- data will be prepared to be presented in an analysis product 
- data will be double-checked if accurate or not 
- keep in mind who's the audience - there is no one-size-fits-all solution 

### Dissemination (Presentation and spreading the information)
The analyst will write a report in which the 

- provide the outcome in an easy to understand way and medium 
- this can be a written report, a dashboard a verbal report, etc... 


### Utilization (make actionable items) 
- based on the reported information, there will be action items for who-ever-is-affected
- e.g. networking team will need to update firewall rules 
- e.g. client team will need to roll-out patches 







# Cyber Threat Intelligence 

## Introduction 
#todo 

### Common definition 
Cyber Threat Intelligence is all about processing signals, data and information to provide an easy to understand summary about a threat. A decision maker will use this summary to take further action in terms of mitigation, prevention or detection of the threat. 

In short: Threat Intelligence consists of the translation of complex data to easy understandable information so someone can base a decision on this intel. 

### Main Goal 
Cyber Threat Intelligence always aims to provide information to make a decision on a specific situation. 


## Processing Threat Intelligence 

### Transformation of data  
There is a widly known depiction of the transformation of data. The image used is a pyramid which is based on data, refined on information and finalized on knowledge. Upon knowledge there is wisdom. 

**Data:** Consists of log events, tool reports and scan results. Things like hashes, domains, IPs, URLs, etc... 

**Information:** Derives from patterns found in data, calculated KPIs, TTPs. Can be the result of human based analysis of data or AI conducted searches for defined patterns. 

**Knowledge:** The result of the analysis of data and information. The facts on which 'wisdom' is based. 

**Wisdom:** The conclusion based on the facts provided as 'knowledge'. This will finally lead to the decision how to cope with a specific threat. 

The process of tranforming data to information starts with the collection of data from the low level tools we use. Hashes, dumps, domains, IPs, etc... will be stored in a managable way. In a Microsoft Cloud environment, we can reference i. e. event logs and access them via Sentinel. Additionally you can ingest other sources like Firewall logs or manually created tables to make associations between IoCs.  

{{< alert >}}
**Note:** To process our data, we need them to be stored in a structured way with metadata. Also, the data needs to be accessible, refinable and, best case immutable. 

Examples for such data can be **Log files**, **Outcome from scan tools** or **low level reports**. 
{{< /alert >}}


### Intelligence Life Cycle 
The processing of Threat Intelligence data follows a theoretical life cycle. This life cycle consists of six (6) steps and repeats after the last step. 



The steps and tasks mentioned here are very theoretical and might not apply in every single case or company. 

#### Planning and Direction 
- define intelligence requirements (including primary intel requirement)
- prioritize the requirements to tackle resource shortage 
- check out data gathering capabilities 
- define what data sources will be used 
- collect all the "what I want to know" from all stakeholders involved 

During the planning and direction phase the CTI team will define the **Primary Intelligence Requirement** as well as other Intelligence Requirements. The priority will help to focus on the most important goal in case of limited resources. 

Additionally the team will have a look a its collection gathering capabilities. Which other teams and sources can we use to gather data. 

#### Collection 
- collect data from data sources (vuln management, incident response, monitoring team, it operations, DFIR)
- get data grouped for each requirement defined in step one (1). 

#### Processing 
- collected data needs to be transformed in a structured format for further access 
- e.g. database or other structured form 
- data will be mapped on correlating points to see patterns and references 
- raw data will be converted in a way we can work with and all entries are in the same format 

#### Analysis and Production 
- this steps outcome is a analysis product (e.g. report, dashboard, tile card, what-ever-floats-your-boat) 
- data will be processed, analyzed, interpreted and enriched 
- data will be prepared to be presented in an analysis product 
- data will be double-checked if accurate or not 
- keep in mind who's the audience - there is no one-size-fits-all solution 

#### Dissemination (Presentation and spreading the information)
- provide the outcome in an easy to understand way and medium 
- this can be a written report, a dashboard a verbal report, etc... 


#### Utilization (make actionable items) 
- based on the reported information, there will be action items for who-ever-is-affected
- e.g. networking team will need to update firewall rules 
- e.g. client team will need to roll-out patches 

## An Example 

### Define your goal | Primary Intelligence Requirement 

### Get information tailored to your PIR 

### Refine and enrich your information 

### Make a conclusion based on your data 

### Write a report 

### Derive actions based on the report 

### Repeat 










## Introduction to Cyber Threat Intelligence 

### Definition of Cyber Threat Intelligence 

### Who benefits from Cyber Threat Intelligence programs

### 

## Introduction to Cyber Threat Intelligence 
I have read so many definitions of what Cyber Threat Intelligence is. Beginning with very academical definitions to analogies of military jargon (the most stupid in my eyes). 

From all theoretical content I've seen, this one is the most suitable - as far as you might ask me: 
> Threat Intelligence is the translation of different kinds of data into an easy to understand and digestable format enriched with related information and a proper conclusion out of the data analysis. The main goal is to make complex data easy and fast to understand by decision makers to mitigate threats. 

## What's the benefits of Cyber Threat Intelligence 
Cyber Threat Intelligence operations have one goal: Make threats easy to understand. In a practical approach this means decisions to mitigate a specific threat or prepare for upcoming threats. These threats can root from vulnerabilites, misconfigurations, user-behavior, etc... 

An important aspect of implementing Cyber Threat Intelligence teams is to know what you want to achieve. To make this clear, the first stept is to define 



## The Cyber Threat Intelligence Life Cycle



## Information flow of Cyber Threat Intelligence 
### Overview 
- Incident happened 
- SOC Analysts 
- Incident Response 
- Digital Forensics 
- Indicator of Compromise 
- Threat attribution 
- Identify TTPs 
- Build up threat detection 

{{< mermaid >}}
flowchart TD
    A[Incident] --> B[SOC] 
    B --> C[Incident Response]
    C --> D[Digital Forensics]
    D --> E[Malware Analysis]
    E --> F[Indicator of Compromise]
    F --> G[Threat Intel]
    G --> H[Attribution, TTP, IoC]
    H --> I[Threat Detection]
    I --> A
{{< /mermaid >}}

### Description 
- Incident happended 
- SOC detects the incident and performs first remediations 
- DFIR mitigates the impact and unhinges artefacts 
- Malware analysis processes the artefacts and creates a file with IoCs 
- Threat Intelligence attributes additional information and associates the incident with known threat actors 
- Threat Intelligence provides a report with the description of the initial incident with data from SOC, the findings by DFIR, the analysis of Malware analysis, the attributions by CTI and the conclusion of any potential associates with the incident. 
- Threat detection creates rules to improve security posture 









