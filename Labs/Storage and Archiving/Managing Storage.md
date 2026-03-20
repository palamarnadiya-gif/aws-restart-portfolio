# Managing Storage Lab Portfolio

## Overview
In this lab, I managed data on **Amazon EBS** volumes using the **AWS CLI**. I created snapshots, automated snapshot retention with Python, and synced local files to **Amazon S3** with versioning enabled to recover deleted files.

## Objectives Achieved
- Created and maintained snapshots for EC2 instances.  
- Synced files from EBS volumes to an S3 bucket.  
- Used S3 versioning to retrieve deleted files.
  <img width="940" height="595" alt="image" src="https://github.com/user-attachments/assets/0c720f8c-4789-445d-a339-f3fad7caf270" />


## Key Tasks Completed

### 1. Created and Configured Resources
- Created an **S3 bucket** for file synchronization.  
- Attached **S3BucketAccess IAM role** to the Processor EC2 instance.
  <img width="940" height="380" alt="image" src="https://github.com/user-attachments/assets/7c0e059e-835c-47e9-b4dd-2b72258ea99b" />
  <img width="940" height="374" alt="image" src="https://github.com/user-attachments/assets/22d0eae7-6337-4ee1-8b12-616345e0a21b" />
  <img width="940" height="252" alt="image" src="https://github.com/user-attachments/assets/285ed9df-a3f8-40b2-8c59-bdc045a7488c" />
  <img width="940" height="415" alt="image" src="https://github.com/user-attachments/assets/2a310eb0-0aab-4753-a9b1-614250b05173" />

### 2. Managed EBS Snapshots
- Connected to the **Command Host** instance via EC2 Instance Connect.  
- Identified EBS volume of the Processor instance and took an initial snapshot.  
- Scheduled recurring snapshots using **cron**.  
- Ran a **Python script** to retain only the last two snapshots, successfully deleting older snapshots.
  <img width="940" height="402" alt="image" src="https://github.com/user-attachments/assets/241f43b0-71c4-4c8b-954e-8ec1ac5f44cd" />
  <img width="940" height="407" alt="image" src="https://github.com/user-attachments/assets/80c6a7bf-d8f1-4a71-9ad5-e154157bc8a9" />
  <img width="940" height="274" alt="image" src="https://github.com/user-attachments/assets/87476835-0450-4654-b5e4-a5d1638c4880" />
  <img width="940" height="502" alt="image" src="https://github.com/user-attachments/assets/ab524750-4baa-433b-ba0b-4616f4025066" />
  <img width="940" height="395" alt="image" src="https://github.com/user-attachments/assets/c858b5ef-b9bb-4ec8-8b3d-228c003f02d8" />
  <img width="940" height="543" alt="image" src="https://github.com/user-attachments/assets/5533f780-6ea9-43cb-9529-3e741e070b17" />
<img width="940" height="364" alt="image" src="https://github.com/user-attachments/assets/8fb0b632-830f-4f18-861a-c94a1be47333" />
<img width="940" height="714" alt="image" src="https://github.com/user-attachments/assets/4c799fa1-7d30-427d-8159-393648cc580e" />


### 3. Challenge: File Synchronization with Amazon S3
- Connected to the **Processor** instance and downloaded sample files.  
- Activated **versioning** on the S3 bucket.  
- Synced local files to S3 using `aws s3 sync`.  
- Deleted a local file and synchronized changes to S3 with the `--delete` option.  
- Restored the deleted file from S3 using versioning commands and re-synced it.

## Conclusion
Successfully completed all objectives:
- Automated snapshot management for EC2 volumes  
- Synchronized local directories to S3  
- Retrieved deleted files using S3 versioning  

## References
- [Amazon EBS Documentation](https://aws.amazon.com/ebs/)  
- [AWS CLI S3 Commands](https://docs.aws.amazon.com/cli/latest/reference/s3/index.html)  
- [Connect to Your Linux Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)
