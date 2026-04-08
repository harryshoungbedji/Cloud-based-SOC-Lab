# Cloud-based SOC Lab

Cloud-based SOC lab on AWS featuring Splunk Enterprise, Claude-powered threat detection, and live attack simulation using Kali Linux.

## Objective

Build a cloud security lab on AWS with separate networks for security operations, a private victim environment, and an isolated attacker environment. The lab uses Splunk to ingest and search logs, and an AI agent powered by Claude to analyze events, summarize suspicious activity, and provide severity-based recommendations.

## Architecture

- Public management subnet:
  - Hosts Splunk Enterprise
  - Accessible only from approved admin IPs
- Private victim subnet:
  - Hosts the target system
  - No public IP
- Isolated attacker subnet:
  - Hosts Kali Linux
  - Used for controlled attack simulation
- NAT Gateway:
  - Provides outbound internet access for private subnet systems when needed
- VPC Flow Logs:
  - Captures network traffic visibility for analysis and detection

## Tools / Tech Stack

| Tool | Purpose |
|---|---|
| AWS VPC | Network isolation and routing |
| AWS EC2 | Virtual machines |
| AWS NAT Gateway | Private subnet internet access |
| AWS Network ACLs | Subnet-level traffic filtering |
| AWS Security Groups | Instance-level traffic filtering |
| AWS IAM | Role-based access control |
| Splunk Enterprise 10.2.2 | SIEM for log ingestion, search, and analysis |
| Splunk Universal Forwarder | Log shipping from victim to Splunk |
| Kali Linux | Untrusted attacker VM for simulation |
| Ubuntu 24.04 LTS | OS for Splunk and victim systems |
| Python 3 | AI agent scripting |
| Anthropic Claude API | AI-assisted log analysis |
| Hydra | SSH brute-force simulation |
| Nmap | Network scanning simulation |

## Deployment Steps

1. Create the VPC and subnets.
2. Add the Internet Gateway.
3. Add a NAT Gateway if the private instance needs outbound internet access.
4. Enable VPC Flow Logs.
5. Launch Splunk in the public subnet.
6. Launch the victim in the private subnet.
7. Use Session Manager or tightly scoped SSH for the victim.
8. Configure Splunk to receive data on port 9997 and access the web UI on port 8000.
9. Add the AI analysis agent after log ingestion is validated and stable.

## Ports

- 8000: Splunk Web UI
- 9997: Splunk forwarding input
- 22: SSH, restricted to trusted admin access only

Splunk commonly uses port 8000 for the web interface and 9997 for forwarded data [web:2].

## Security Notes

- Restrict Splunk Web to admin IP.
- Keep the victim instance private with no public IP.
- Prefer AWS Systems Manager Session Manager over SSH for private instances.
- Use security groups and route tables to enforce separation between trusted and untrusted networks.


## AI Analysis Workflow

1. Logs arrive in Splunk from the victim.
2. The AI agent queries Splunk for recent events.
3. Claude summarizes suspicious activity.
4. The agent assigns a severity level.
5. The agent outputs recommendations for response and tuning.

## Attack Simulation

- Nmap for host discovery and port scanning
- Hydra for SSH brute-force testing
- Controlled activity only inside the lab environment

