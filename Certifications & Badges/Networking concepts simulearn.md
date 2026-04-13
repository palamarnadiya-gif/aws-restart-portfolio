# AWS VPC Secure Networking Architecture – Cloud Engineering Case Study

## Project Overview

This project demonstrated the design and implementation of a secure AWS network architecture for a simulated banking environment. The objective was to control traffic flow between internal resources and the internet using AWS VPC components.

The solution was implemented in a live AWS Management Console environment using AWS SimuLearn, following real-world cloud engineering practices.


---

## Business Requirement

A fictional banking organization required a secure cloud network where:
- Internal database systems were isolated from direct public exposure
- Controlled internet access was enabled for specific subnets
- Traffic rules were strictly managed using security groups and routing policies

---

## Architecture Delivered

The following AWS components were configured:

- Virtual Private Cloud (VPC)
- Public and Private Subnets
- Internet Gateway (IGW)
- Route Tables
- Security Groups (Inbound Rules)
- MySQL database access over port 3306

---

## Step-by-Step Implementation

---

### Step 1: VPC Exploration and Network Baseline

The existing VPC environment was reviewed to understand CIDR ranges, subnet segmentation, and default routing behavior.

<img width="470" height="230" alt="image" src="https://github.com/user-attachments/assets/30db718e-9b44-46d4-85a8-4ec41c97bb7c" />

---

### Step 2: Internet Gateway Configuration

An Internet Gateway was created and attached to the VPC to enable outbound internet connectivity for public resources.

<img width="470" height="198" alt="image" src="https://github.com/user-attachments/assets/807d44bb-d596-4c21-9f47-3b4d24744e5b" />

<img width="193" height="241" alt="image" src="https://github.com/user-attachments/assets/bab9b71f-a118-4b0b-baa0-7e5a7639575f" />



---

### Step 3: Route Table Configuration

A custom route table was created and associated with the public subnet. A default route (0.0.0.0/0) was configured to direct traffic through the Internet Gateway.

<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/63ef09b8-bc7d-4685-9ed4-199dfea1abf5" />

<img width="470" height="207" alt="image" src="https://github.com/user-attachments/assets/6012fca3-e670-4f10-aa1e-9b96175be841" />


---

### Step 4: Subnet Association

The public subnet was explicitly associated with the updated route table to ensure correct routing behavior.

<img width="470" height="207" alt="image" src="https://github.com/user-attachments/assets/624a1de4-eec5-4ec5-80ee-ce5dc61f2cb9" />

<img width="470" height="161" alt="image" src="https://github.com/user-attachments/assets/2ea81d55-b4b4-4481-b7ce-21757dc067e6" />

---

### Step 5: Security Group Configuration

Inbound rules were configured to control access to resources inside the VPC.

Rules included:
- SSH (22) restricted access
- HTTP/HTTPS allowed where required
- MySQL (3306) enabled for controlled database access


<img width="470" height="164" alt="image" src="https://github.com/user-attachments/assets/fe2424ef-6f50-4bc5-b245-6c70f9b294a4" />

<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/96f58d98-9360-4fca-9dcc-d8496ce1edb6" />

<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/e1c8fccf-16a7-449d-a6c7-51eb42589c24" />

<img width="470" height="207" alt="image" src="https://github.com/user-attachments/assets/da0c34e6-5b80-48a4-95bb-ca70be1da8e1" />

---

### Step 6: Database Access Configuration (DIY Task)

Security group rules were updated to allow inbound traffic on port 3306 to enable controlled access to the database server.


<img width="470" height="189" alt="image" src="https://github.com/user-attachments/assets/15e72e07-6b92-414c-b67c-647a6cf079d8" />


---

## Outcome

The final architecture successfully:
- Enabled secure internet access via IGW
- Controlled routing using custom route tables
- Restricted database exposure using security groups
- Followed AWS best practices for network segmentation
<img width="470" height="213" alt="image" src="https://github.com/user-attachments/assets/878065fb-4b99-4169-ab8f-babc11d7c61e" />
---

## Skills Demonstrated

- AWS VPC Architecture Design
- Network Segmentation Strategy
- Internet Gateway Configuration
- Route Table Engineering
- Security Group Hardening
- Cloud Security Best Practices

---

## Project Type

Cloud Engineering Simulation (AWS SimuLearn)
<img width="940" height="165" alt="image" src="https://github.com/user-attachments/assets/54979fd5-ac61-444a-8f69-cfd28e179457" />
