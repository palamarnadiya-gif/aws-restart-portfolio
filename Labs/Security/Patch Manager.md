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

### Steps completed
1. Opened Systems Manager in the AWS Console  
2. Navigated to Patch Manager  
3. Selected **Patch now**

### Configuration used
- Operation: Scan and install  
- Reboot option: If needed  
- Target selection: Instances tagged with  
  - Key: `Patch Group`  
  - Value: `LinuxProd`

### Result
All Linux instances were successfully patched using the default baseline.

---

## Task 2: Create Custom Patch Baseline (Windows)

### What I did
I created a custom patch baseline for Windows systems to control update approval rules.

### Steps completed
1. Opened Patch Manager → Patch baselines  
2. Created a new patch baseline  

### Configuration used
- Name: `WindowsServerSecurityUpdates`  
- Operating system: Windows  
- Approval rules:
  - Critical security updates (auto-approved after 3 days)
  - Important security updates (auto-approved after 3 days)

### Patch group assignment
- I assigned the patch group: `WindowsProd`

### Result
A controlled patching policy was successfully created for Windows instances.

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
