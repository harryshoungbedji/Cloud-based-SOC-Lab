# Cloud-based-SOC-Lab
### Cloud-based SOC lab on AWS with Splunk SIEM, Claude powered threat detection, and live attack simulation using Kali Linux.

-----------------------------------------------------------------------------------------------------------------------

## Objective
Built a cloud security lab on AWS with three isolated networks: a management network hosting Splunk and the AI analysis agent, a private victim network, and an untrusted attacker network running Kali Linux. The lab ingests logs into Splunk, uses an AI agent powered by Claude to analyze events and summarize suspicious activity, and supports live attack simulation for detection and response testing.

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

## Setup
- Created an AWS VPC with CIDR 10.0.0.0/16.
- Created a public management subnet for Splunk.
- Created a private subnet for the victim host.
- Attached an Internet Gateway to provide internet access for the public subnet.
- Added a NAT Gateway for private subnet outbound access when needed.
- Enabled VPC Flow Logs for traffic visibility.
-Launched Splunk in the public subnet.
- Launched the victim in the private subnet with no public IP.
- Managed the victim using Session Manager or tightly scoped SSH.
- Configured Splunk to listen on port 9997 for forwarded logs and port 8000 for the web UI.
- Added the AI analysis agent after log ingestion was confirmed stable.
