
# AWS EC2 Static vs Dynamic IP Addressing – Cloud Support Case Study

## Project Overview

This project focused on diagnosing and resolving a real-world cloud networking issue involving dynamic IP behavior in Amazon EC2. The objective was to ensure consistent external accessibility by implementing a static IP solution.

The investigation and resolution were performed in a live AWS environment using standard cloud support troubleshooting methodologies.

---

## Customer Issue

The customer reported the following:

- An EC2 instance (Public Instance) changed its public IP address after every stop/start cycle
- Dependent systems failed due to reliance on a fixed IP address
- A static IP solution was required to maintain service stability
  
<img width="470" height="310" alt="image" src="https://github.com/user-attachments/assets/a10b763d-927c-4470-80e5-23882dfa0f62" />

---

## Investigation Approach

A structured troubleshooting method was applied:

1. Replicate the issue in a controlled environment
2. Analyze IP behavior during instance lifecycle changes
3. Identify root cause
4. Implement a persistent IP solution

---

## Step-by-Step Investigation

---

### Step 1: EC2 Instance Deployment

A new EC2 instance was launched in a public subnet to replicate the customer's configuration.

Key configuration:
- Amazon Linux 2 AMI
- t3.micro instance
- Auto-assigned public IP enabled
  
<img width="470" height="314" alt="image" src="https://github.com/user-attachments/assets/10d73b3f-6e98-4108-803e-2b334fdef46d" />

---

### Step 2: Initial IP Address Observation

The instance networking configuration was inspected.

Findings:
- Public IPv4 address assigned automatically
- Private IPv4 address assigned internally within VPC

<img width="470" height="142" alt="image" src="https://github.com/user-attachments/assets/442446b2-1691-42b7-8c63-77628cade144" />


---

### Step 3: Stop/Start Behavior Analysis

The instance was stopped and restarted to observe IP changes.

Observations:
- Public IP address changed after restart
- Private IP address remained unchanged

Conclusion:
- Public IP was dynamically assigned
- Private IP was persistent within the VPC

<img width="470" height="152" alt="image" src="https://github.com/user-attachments/assets/9cc92e0b-6eed-48c7-a421-0b3ad7221b90" />

<img width="470" height="265" alt="image" src="https://github.com/user-attachments/assets/058e04fc-956e-422e-b827-b10b4a6e9853" />

<img width="470" height="243" alt="image" src="https://github.com/user-attachments/assets/3697c40b-de02-455e-afbd-5251bb98ac78" />

---

### Step 4: Root Cause Identification

The issue was identified as default AWS behavior:

- Auto-assigned public IPs are dynamic
- They are released when the instance is stopped
- A new IP is assigned on restart

This behavior caused instability for services relying on fixed endpoints.

<img width="470" height="235" alt="image" src="https://github.com/user-attachments/assets/293265b7-83fb-4a90-a3ba-b1511b27ffed" />


---

### Step 5: Elastic IP Allocation

An Elastic IP (EIP) was allocated to provide a persistent public IP address.

Key characteristics:
- Static public IP
- Retained across stop/start cycles
- Manually associated with EC2 instance

<img width="470" height="255" alt="image" src="https://github.com/user-attachments/assets/08c78b70-0427-4393-b7a0-42a7b5824443" />

<img width="470" height="220" alt="image" src="https://github.com/user-attachments/assets/9d9b59bd-55cf-4c49-a68e-1fb363f903dd" />

---

### Step 6: Elastic IP Association

The Elastic IP was associated with the EC2 instance.

Result:
- Elastic IP replaced the dynamic public IP
- Instance maintained the same public IP across restarts

<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/cef841ff-f274-4039-8e1a-323386836449" />

<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/744a94c7-93d9-428c-aecf-8aeee31946a6" />

---

### Step 7: Validation

The instance was stopped and restarted again.

Outcome:
- Public IP remained unchanged
- Connectivity stability restored

<img width="470" height="245" alt="image" src="https://github.com/user-attachments/assets/2146129f-1602-4a43-92ac-8d8b73a31005" />

<img width="470" height="245" alt="image" src="https://github.com/user-attachments/assets/e30093b0-1249-414e-895d-b973f44f06ed" />

<img width="470" height="220" alt="image" src="https://github.com/user-attachments/assets/a5150564-3cbb-4b2d-a8dc-7af4d566382a" />

---

## Solution Delivered

- Identified dynamic public IP as root cause
- Implemented Elastic IP for persistence
- Ensured consistent external access to EC2 instance

---

## Outcome

The architecture was successfully stabilized:

- Static public IP maintained across lifecycle events
- Dependent services restored
- Customer requirement for fixed IP fully satisfied

---

## Key Insights

- Default EC2 public IPs are dynamic
- Private IPs remain constant within a VPC
- Elastic IPs provide persistent public addressing
- Static IPs are critical for production systems with external dependencies

---

## Skills Demonstrated

- AWS EC2 Networking
- Elastic IP Configuration
- Cloud Troubleshooting Methodology
- Root Cause Analysis
- Infrastructure Stability Design
- Customer-Facing Problem Solving

---

## Project Type

Cloud Support Engineering Simulation (AWS Networking Incident)
