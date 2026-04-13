# AWS Networking Troubleshooting – Public vs Private IP Addressing (Cloud Support Case Study)

## Project Overview

This project simulated a real-world cloud support scenario involving a Fortune 500 customer experiencing inconsistent internet connectivity between two EC2 instances within the same VPC.

The objective was to investigate, identify, and resolve the issue using structured troubleshooting techniques aligned with AWS networking principles.

---

## Customer Issue

The customer reported the following:

- Two EC2 instances (Instance A and Instance B) deployed in the same subnet
- Identical AWS configurations applied to both instances
- Instance B successfully accessed the internet
- Instance A failed to reach the internet

Additionally, the customer requested guidance on using a public IP range (12.0.0.0/16) for a VPC.

<img width="470" height="303" alt="image" src="https://github.com/user-attachments/assets/2bacaf45-d1f7-4b5c-9ff6-df4d30c1f7fd" />

---

## Investigation Approach

A bottom-up troubleshooting strategy was applied, inspired by the OSI model:

| Layer | Focus Area | AWS Mapping |
|------|-----------|------------|
| Application | Connectivity test | EC2 behavior |
| Session | Access control | EC2 instance |
| Transport | Traffic filtering | Security Groups |
| Network | IP addressing | Subnets, Routing |
| Infrastructure | Environment | VPC |

The investigation focused primarily on IP addressing at the EC2 instance level.

---

## Step-by-Step Investigation

---

### Step 1: Environment Inspection (EC2 Instances)

Both EC2 instances were inspected within the AWS Console to compare configurations and networking attributes.

Key parameters analyzed:
- Public IPv4 address
- Private IPv4 address
- Subnet placement
- 
<img width="470" height="130" alt="image" src="https://github.com/user-attachments/assets/eeb9c9fe-8c1c-4abe-a645-a2d2a3ef5d3b" />


---

### Step 2: IP Address Comparison

A detailed comparison of Instance A and Instance B revealed a critical difference:

- Instance B had a Public IP address
- Instance A had only a Private IP address

This difference directly impacted internet connectivity.



<img width="470" height="270" alt="image" src="https://github.com/user-attachments/assets/af9e147c-0914-4cf6-aedd-2511add43ad1" />

<img width="470" height="255" alt="image" src="https://github.com/user-attachments/assets/16e39e80-7ef5-4cc2-be6e-64ef4767d9ac" />

---

### Step 3: Connectivity Testing via SSH

Secure Shell (SSH) was used to validate connectivity behavior and confirm that:

- Instance B allowed external access and outbound communication
- Instance A could not establish outbound internet connections

<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/8955edd3-3980-417e-a6a6-622cbe250340" />

<img width="470" height="240" alt="image" src="https://github.com/user-attachments/assets/34ebe659-8c06-413b-b154-eaf83794c5bc" />

<img width="470" height="202" alt="image" src="https://github.com/user-attachments/assets/0e8304a1-d4c5-4b40-be02-6e31731f820a" />

<img width="470" height="195" alt="image" src="https://github.com/user-attachments/assets/d14d4638-420c-4e75-b7d7-74d8532c05f4" />
---

### Step 4: Root Cause Identification

The issue was traced to IP addressing:

- Private IP addresses operate only within the VPC
- Internet access requires a public IP or NAT configuration

Instance A lacked a public IP, preventing outbound internet communication.

<img width="470" height="225" alt="image" src="https://github.com/user-attachments/assets/38caed60-f83d-43a7-bcb3-96847257cd28" />
---

### Step 5: Customer Design Review (CIDR Strategy)

The customer's question regarding use of public IP ranges (e.g., 12.0.0.0/16) was analyzed.

Findings:
- Public IP ranges are globally routable
- Using them inside a VPC can cause routing conflicts
- Best practice is to use private ranges defined in RFC1918:
  - 10.0.0.0/8
  - 172.16.0.0/12
  - 192.168.0.0/16

<img width="470" height="355" alt="image" src="https://github.com/user-attachments/assets/066f71ac-5423-4ebe-9037-3c9357dbdf6a" />


---

## Solution Delivered

- Identified missing public IP assignment on Instance A
- Explained difference between public and private IP addressing
- Recommended enabling auto-assign public IP or using a NAT Gateway
- Advised against using public CIDR ranges inside VPC

---

## Outcome

The issue was successfully resolved by:

- Correcting IP assignment for Instance A
- Restoring internet connectivity
- Providing architectural guidance for future VPC design

---

## Key Insights

- Public IP is required for direct internet communication
- Private IPs are restricted to internal VPC communication
- Misconfigured IP addressing is a common root cause in AWS networking issues
- CIDR selection directly impacts network scalability and safety

---

## Skills Demonstrated

- AWS Networking Troubleshooting
- EC2 Connectivity Analysis
- Public vs Private IP Architecture
- OSI Model Application in Cloud
- Customer Communication (Cloud Support Role)
- Root Cause Analysis

---

## Project Type

Cloud Support Engineering Simulation (AWS Incident Scenario)
