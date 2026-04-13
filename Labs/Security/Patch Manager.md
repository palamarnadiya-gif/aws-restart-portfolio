# Systems Hardening with Patch Manager via AWS Systems Manager

## Overview
In this lab, I used Patch Manager (a feature of AWS Systems Manager) to automate patching and maintain security compliance across multiple EC2 instances.

I worked with:
- Default patch baselines for Linux systems  
- Custom patch baselines for Windows systems  
- Patch groups for targeted updates  
- Compliance reporting to verify results  

---

## Scenario
I acted as a Cloud Support Engineer at AWS.

The goal was to help a company:
- Automate patch management  
- Improve security compliance  
- Ensure systems remained consistently updated  

---

## Objectives
I successfully:
- Patched Linux instances using default baselines  
- Created a custom patch baseline for Windows  
- Used patch groups to manage targeted patching  
- Verified patch compliance across all instances  

---

## Environment
The lab environment included:
- 3 Linux EC2 instances  
- 3 Windows EC2 instances  
- Preconfigured IAM roles and AWS Systems Manager setup  

---

## Task 1: Patch Linux Instances (Default Baseline)

### What I did
I used the default patch baseline provided by AWS Systems Manager to patch Linux instances.

<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/259b4614-7b33-4074-ada1-2058e1555b9f" />


<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/f94041ab-b2b7-4154-986d-d030e20d7813" />

<img width="470" height="220" alt="image" src="https://github.com/user-attachments/assets/ec83ee2c-049b-46ba-be6a-b58abbdbe595" />

### Steps completed
1. Opened Systems Manager in the AWS Console  
2. Navigated to Patch Manager  
3. Selected **Patch now**

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/0ed0646d-00d2-4d8b-874b-f6d3f09f3b97" />

### Configuration used
- Operation: Scan and install  
- Reboot option: If needed  
- Target selection: Instances tagged with  
  - Key: `Patch Group`  
  - Value: `LinuxProd`

<img width="470" height="540" alt="image" src="https://github.com/user-attachments/assets/f5e28d47-d7e0-4889-9b0e-d81d09673213" />

### Result
All Linux instances were successfully patched using the default baseline.

<img width="470" height="350" alt="image" src="https://github.com/user-attachments/assets/54b6335a-c2ed-4a3b-9ffb-2917c0346a38" />

<img width="470" height="340" alt="image" src="https://github.com/user-attachments/assets/c28363fe-f574-4a23-80a3-c44bc9c0be52" />
<img width="470" height="560" alt="image" src="https://github.com/user-attachments/assets/5525496d-0674-4a41-afe9-1720533218f0" />

---

## Task 2: Create Custom Patch Baseline (Windows)

### What I did
I created a custom patch baseline for Windows systems to control update approval rules.

<img width="470" height="550" alt="image" src="https://github.com/user-attachments/assets/ebad5733-3da7-46cb-b16e-5df9feed7304" />


### Steps completed
1. Opened Patch Manager → Patch baselines  
2. Created a new patch baseline  

### Configuration used
- Name: `WindowsServerSecurityUpdates`  
- Operating system: Windows  
- Approval rules:
  - Critical security updates (auto-approved after 3 days)
  - Important security updates (auto-approved after 3 days)
  - 
    <img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/61ed894a-232a-4fdd-baf5-748299d4c365" />


### Patch group assignment
- I assigned the patch group: `WindowsProd`
- 
  <img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/93943399-efa3-4b61-93f4-9b0dee35d8db" />



### Result
A controlled patching policy was successfully created for Windows instances.

<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/f168e4da-1555-419a-8b59-c9c14605c291" />
---

## Task 3: Patch Windows Instances

### What I did
I applied patching to Windows instances using the custom patch baseline and patch groups.

### Steps completed
1. Tagged Windows instances with:
   - Key: `Patch Group`  
   - Value: `WindowsProd`

2. Ran Patch Manager:
   - Operation: Scan and install  
   - Target: `WindowsProd` instances  

### Result
All Windows instances were successfully patched using the custom baseline.

---

## Task 4: Verify Compliance

### What I did
I verified patch compliance across all instances using Patch Manager dashboards.

### Steps completed
1. Opened Patch Manager dashboard  
2. Checked compliance summary  

### Result
All instances (Linux and Windows) were marked as:
- **Compliant**

I also reviewed:
- Installed patches per instance  
- Last patch execution times  

---

## Key Takeaways
- I automated OS patching using Patch Manager  
- I used default baselines for Linux systems  
- I created custom baselines for Windows security control  
- I used patch groups for scalable management  
- I confirmed full compliance across all instances  
