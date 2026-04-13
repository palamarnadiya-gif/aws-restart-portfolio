# AWS VPC Multi-Tier Network Architecture (Public + Private Subnets with Bastion & NAT)

## Project Overview

A secure multi-tier AWS network architecture was designed and implemented to simulate an enterprise banking environment. The architecture enabled controlled internet access, secure private subnet isolation, and administrative access via a bastion host.

The solution was built using Amazon VPC, EC2, Internet Gateway, NAT Gateway, route tables, and security groups in a live AWS Management Console environment.

<img width="470" height="270" alt="image" src="https://github.com/user-attachments/assets/2d68bc8c-7964-449b-af17-0963d664df21" />

---

## Business Requirement

A financial organization required a secure cloud network with the following constraints:
- Public-facing resources must be isolated in a public subnet
- Internal systems must remain private and inaccessible from the internet
- Outbound internet access must be available for private resources without exposing them
- Administrative access must be controlled through a bastion server

---

## Final Architecture Delivered

The following components were implemented:

- Custom VPC (10.0.0.0/16)
- Public Subnet (10.0.0.0/24)
- Private Subnet (10.0.2.0/23)
- Internet Gateway (IGW)
- NAT Gateway with Elastic IP
- Public Route Table (IGW routing)
- Private Route Table (NAT routing)
- Bastion Host (public subnet EC2)
- Private EC2 Instance (internal subnet)

---

## Step-by-Step Implementation

---

### Step 1: VPC Creation and Network Foundation

A new VPC was created with a custom CIDR block to establish a logically isolated network environment. DNS hostnames were enabled to support EC2 name resolution.

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/b016535e-120b-4e2b-8a9f-52d25b0e4fc6" />


<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/9436f1bc-2bc5-4606-8cc7-c5b9ae19ed92" />

---

### Step 2: Public Subnet Configuration

A public subnet was created and configured to automatically assign public IPv4 addresses to EC2 instances.

<img width="470" height="175" alt="image" src="https://github.com/user-attachments/assets/cd0ed6b1-e48c-4721-8d0e-efc8164a3e2a" />

<img width="470" height="150" alt="image" src="https://github.com/user-attachments/assets/24fdb875-61bc-41d0-9348-b1bdd43cf39d" />

---

### Step 3: Private Subnet Configuration

A private subnet was created for internal-only resources. This subnet was designed to remain isolated from direct internet access.

<img width="470" height="190" alt="image" src="https://github.com/user-attachments/assets/d60711e4-a81d-4c2b-a652-3f781e7ac6a3" />


---

### Step 4: Internet Gateway Deployment

An Internet Gateway was created and attached to the VPC to enable internet connectivity for resources in the public subnet.

<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/2c652125-6c4a-4ed4-99e3-eb2af2339670" />

<img width="470" height="150" alt="image" src="https://github.com/user-attachments/assets/b820cc5b-449e-4524-a305-d10e4b3df4c6" />
<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/27e5569b-8704-4eb7-baa8-85e5b31fd84d" />
<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/2bd0c18d-2ff5-48ea-b4cc-074c91164728" />

---

### Step 5: Public Route Table Configuration

A dedicated route table was created for the public subnet and configured with a default route (0.0.0.0/0) pointing to the Internet Gateway.

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/6ad3635a-b669-4102-b980-357707f362cd" />

<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/4db36677-dcb9-4951-8251-044c3cd5549f" />
<img width="470" height="130" alt="image" src="https://github.com/user-attachments/assets/1b6bc33f-d708-4546-9532-231edc1464a3" />

---

### Step 6: Subnet Association with Public Routing

The public subnet was explicitly associated with the public route table, enabling external internet access.

<img width="470" height="170" alt="image" src="https://github.com/user-attachments/assets/82a69e72-4044-46fb-8b10-34ce2dc52b0c" />
<img width="470" height="205" alt="image" src="https://github.com/user-attachments/assets/056c1082-9c68-4893-9c95-7e2a7f5865a5" />


---

### Step 7: Bastion Host Deployment

An EC2 instance was launched in the public subnet to act as a bastion server for secure administrative access into private resources.

Key configuration:
- Amazon Linux 2023 AMI
- t3.micro instance type
- Security group allowing SSH access

<img width="470" height="90" alt="image" src="https://github.com/user-attachments/assets/f8cb89b6-aec5-4fb1-86de-5ee3deded50a" />

<img width="470" height="130" alt="image" src="https://github.com/user-attachments/assets/faa81af8-a4a6-47b8-965b-de9ca1ecf971" />

---

### Step 8: NAT Gateway Deployment

A NAT Gateway was created in the public subnet and associated with an Elastic IP to enable outbound internet access for private subnet resources.

<img width="470" height="150" alt="image" src="https://github.com/user-attachments/assets/d33008f5-4c0f-471a-85b1-d4b8c9e32a40" />

<img width="470" height="360" alt="image" src="https://github.com/user-attachments/assets/0a000f65-870d-4371-ba57-9a3f1ae0fdd4" />

---

### Step 9: Private Route Table Configuration

The private route table was updated to route all outbound internet traffic (0.0.0.0/0) through the NAT Gateway.

<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/ad5f8df7-3781-4009-9552-c19a450d52ae" />

<img width="470" height="140" alt="image" src="https://github.com/user-attachments/assets/494ecdb5-08fb-42fa-828a-7c6507d0a3cb" />

---

### Step 10: Bastion-Based Private Access

A secure SSH connection flow was established:
- User connected to Bastion Host (public subnet)
- Bastion Host used to access private EC2 instance via internal IP

---

## Outcome

The architecture successfully achieved:

- Secure separation of public and private workloads
- Controlled internet access via NAT Gateway
- Secure administrative access via Bastion Host
- Proper routing segmentation using multiple route tables
- Industry-aligned AWS VPC best practices

---

## Skills Demonstrated

- AWS VPC Design and Architecture
- Multi-subnet Network Segmentation
- Internet Gateway Configuration
- NAT Gateway Implementation
- Route Table Engineering
- Bastion Host Security Pattern
- Secure SSH Access in Private Networks

---

## Project Type

Cloud Infrastructure Lab Simulation (AWS Training / Hands-on Architecture)
