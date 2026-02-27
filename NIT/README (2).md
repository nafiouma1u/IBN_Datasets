---
task_categories:
- translation
- text-generation
language:
- en
size_categories:
- 1K<n<10K
tags:
- network-configurations
- IBN
- computer-networks
---

# Dataset Card for NIT Dataset

The Network Intent Translations (NIT) dataset is specialized for translating descriptive networking scenarios into low-level deployable configurations. The NIT is intended for network intent translations in Intent-Based Networking (IBN). The dataset includes network configuration tasks in natural language (network intents) and their corresponding low-level configurations for Juniper EX3300 switches with JUNOS Base OS boot [12.3R12-S12]. 


## Dataset Details
The NIT dataset covers various networking tasks implemented on the Juniper EX3300 switch. The distribution of the commands used to implement the networking tasks is as follows:

- set commands:  582 
- show commands:  249 
- delete commands:  73 
- other commands:  96 

### Set Commands Topics
- ethernet-switching-options 
- vlans
- interfaces 
- protocols 
- system 
- virtual-chassis 
- routing-options 
- poe  
- snmp 
- igmp-snooping 
- chassis


### Show Commands Topics
- configuration 
- lldp 
- virtual-chassis 
- ethernet-switching 
- ospf  
- vlans  
- dhcp  
- poe
- spanning-tree 
- as-path
- cli  
- arp  
- log
- system 
- chassis 
- | (pipe) 
- ethernet-switching-options
- sflow 
- ip-source-guard 
- igmp 
- igmp-snooping 
- version

### Delete Commands Topics
- ethernet-switching-options 
- protocols 
- system 
- virtual-chassis 
- interfaces 
- vlans 
- snmp 

### Other Commands 
- clear [19]
- status [2]
- save [3]
- ping [4]
- run [4]
- start [6]
- request [29]
- load [3]
- commit [15]
- replace [4]
- rollback [4]
- monitor [3]

## Dataset Structure
Each entry in the dataset is a JSON object with three elements: question, context, and answer. The question represents the network intent in natural language, the context contains the generic form of the commands required to achieve the intent, and the answer includes the low-level command-line configurations necessary to fulfill the network intent, along with any parameters provided in the question field (if applicable). 
Example from the dataset:
- "question": "enable the device connected to port ge-0/0/7 to have a static IP address in Juniper ex3300 switch"
- "context": "set ethernet-switching-options secure-access-port interface <interface-name> dhcp-trusted"
- "answer": "Use the following command in the configuration mode:\nset ethernet-switching-options secure-access-port interface ge-0/0/7 dhcp-trusted\ncommit"
  



## Uses
### Direct Use
The NIT dataset can be utilized for parameter-efficient fine-tuning (PEFT) of large language models (LLMs) to translate network intent into low-level, deployable command-line configurations

### Out-of-Scope Use

The dataset focuses solely on translating high-level network intent into command-line configurations. It does not aim to verify the accuracy of parameter values within the prompts or address any conflict detection or resolution. However, all parameter values in the dataset are valid for their respective tasks.


## Dataset Creation

The NIT dataset was manually created using configuration manuals and the expertise of a network engineer. It includes various ways of requesting the same configuration task to reflect different user behaviors. The dataset contains three types of prompts (questions): Type 1 prompts include all the required parameters for the low-level configurations, Type 2 prompts include some of the required parameters, and Type 3 prompts contain no parameters. The completions (answers) include the operating mode of the required commands, the commands themselves, and a commit when necessary. The completions use the parameters provided in the prompts, or <parameter-name> if the prompt does not include a value for a specific parameter.

## Dataset Paper:

NIT: A dataset for network intent translation: https://www.sciencedirect.com/science/article/pii/S2352340925005694?via%3Dihub

## Dataset Card Authors 
- Ala’ A. Samarneh. Researchgate: https://www.researchgate.net/profile/Alaa-Smarneh

- Dr. Omar Al-Jarrah. Researchgate: https://www.researchgate.net/profile/Omar-Al-Jarrah

- Dr. Ahmad Al-Hammouri. Researchgate: https://www.researchgate.net/profile/Ahmad-Al-Hammouri