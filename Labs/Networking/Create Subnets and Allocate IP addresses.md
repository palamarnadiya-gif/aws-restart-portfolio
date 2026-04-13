# AWS VPC Design and Subnetting – IP Allocation Case Study

## Project Overview

This project focused on designing and implementing a scalable Amazon VPC architecture based on specific customer requirements related to IP address allocation and subnet sizing.

The solution involved CIDR planning, subnet creation, and ensuring efficient distribution of IP space for both public and private use cases.

---

## Customer Requirement

A startup customer requested assistance with:

- Creating a VPC using a private 192.x.x.x IP range
- Supporting approximately 15,000 private IP addresses
- Allocating at least 50 IP addresses for a public subnet
- Receiving guidance on AWS VPC setup and subnet design

---

## Design Strategy

To meet the requirements, the following approach was applied:

- Selected RFC1918 private IP range: 192.168.0.0
- Chose CIDR block: /18 (16,384 IP addresses)
- Designed subnet structure:
  - Public subnet: /26 (64 IP addresses)
  - Remaining IP space reserved for future private subnets

---

## Final Architecture

- VPC: 192.168.0.0/18
- Public Subnet: 192.168.1.0/26
- Private IP allocation capacity: ~16,000 addresses
- Public subnet capacity: 64 addresses (satisfying 50+ requirement)

---

## Step-by-Step Implementation

---

### Step 1: Requirement Analysis

Customer requirements were translated into technical specifications:

- Minimum ~15,000 IPs required
- Public subnet must support at least 50 IPs
- Must use private IP range (RFC1918 compliant)

<img width="470" height="300" alt="image" src="https://github.com/user-attachments/assets/b1a19f5e-10b9-4962-924e-c81fd7123212" />

---

### Step 2: CIDR Block Selection

A suitable CIDR block was calculated:

- /18 subnet chosen to provide 16,384 total IP addresses
- Falls within private IP range (192.168.x.x)

---

### Step 3: VPC Creation

A new VPC was created using:

- IPv4 CIDR block: 192.168.0.0/18
- DNS settings enabled
- Default tenancy

<img width="470" height="530" alt="image" src="https://github.com/user-attachments/assets/e80d2a78-f140-40c2-ad89-b0f4ce36c244" />

<img width="470" height="208" alt="image" src="https://github.com/user-attachments/assets/0c051abb-e4a0-44de-a025-342ac14c0a29" />

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/6a86d1c4-70d8-466b-a361-c0681931d90c" />

---

### Step 4: Public Subnet Design

A public subnet was created with:

- CIDR block: 192.168.1.0/26
- Capacity: 64 IP addresses

This satisfied the requirement of at least 50 IPs.

---

### Step 5: VPC Configuration Validation

The VPC configuration was reviewed to ensure:

- Correct CIDR allocation
- Subnet properly aligned within VPC range
- No overlapping IP ranges

<img width="470" height="135" alt="image" src="https://github.com/user-attachments/assets/d3e0e808-31a1-4f0b-8dc7-48411a2fb5cb" />

---

### Step 6: Customer Walkthrough Preparation

A simplified guide was prepared for the customer explaining:

- How to create a VPC
- How to select CIDR blocks
- How to design subnets based on requirements

---

## Solution Delivered

- Designed VPC with sufficient IP capacity
- Allocated subnet meeting public IP requirements
- Ensured compliance with private IP standards
- Provided reusable setup guidance for customer

---

## Outcome

The customer successfully:

- Deployed a scalable VPC architecture
- Understood CIDR and subnetting principles
- Gained the ability to extend the network in the future

---

## Key Insights

- CIDR selection directly impacts scalability
- Private IP ranges (RFC1918) must be used in VPC design
- Subnet sizing should align with workload requirements
- Over-allocation provides flexibility for future growth

---

## Skills Demonstrated

- AWS VPC Architecture Design
- CIDR and Subnet Planning
- IP Address Management
- Cloud Network Design Strategy
- Customer-Facing Technical Guidance

---

## Project Type

Cloud Architecture & Support Simulation (AWS Networking Design)
