# Cloud-based-SOC-Lab
### Cloud-based SOC lab on AWS with Splunk SIEM, Claude powered threat detection, and live attack simulation using Kali Linux.

-----------------------------------------------------------------------------------------------------------------------

## Objective
Hands-on cloud security lab built on AWS — three segmented networks where an Admin network (Splunk SIEM) monitors all traffic, an Untrusted network simulates attacks, and a Private network acts as the target. An AI agent installed on the Admin network collects, analyzes, and summarizes logs with severity-based recommendations using the Anthropic Claude API.

## Tools / Tech Stack
| Tool | Purpose |
|---|---|
| AWS VPC | Network isolation and routing |
| AWS EC2 | Virtual machines |
| AWS NAT Gateway | Private subnet internet access |
| AWS Network ACLs | Subnet-level firewall rules |
| AWS Security Groups | Instance-level firewall rules |
| AWS IAM | Role-based access control |
| Splunk Enterprise 10.2.2 | SIEM — log ingestion and search |
| Splunk Universal Forwarder | Log shipping from Victim to Splunk |
| Kali Linux | Attacker VM — Hydra, Nmap, Metasploit |
| Ubuntu 24.04 LTS | Splunk VM and Victim VM OS |
| Python 3 | AI agent scripting |
| Anthropic Claude API | AI-powered log analysis |
| Hydra | SSH brute force simulation |
| Nmap | Network scanning simulation |
