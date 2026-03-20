#  AWS Lab – Static Website on Amazon S3

##  Overview
In this lab, I deployed a static website using **Amazon S3** and configured access using **AWS CLI and IAM**.  
The goal was to create a simple, scalable web hosting solution without using traditional servers.
<img width="470" height="219" alt="image" src="https://github.com/user-attachments/assets/39ab71a6-37a0-4ea4-984b-b7425fa7eb54" />

---

##  What I Did
- Created an **S3 bucket** using AWS CLI
  
  <img width="470" height="181" alt="image" src="https://github.com/user-attachments/assets/ca30a742-9389-4a24-a208-645177eee7ea" />

  <img width="470" height="188" alt="image" src="https://github.com/user-attachments/assets/e8b6a0ff-5012-4651-b2b3-09066f60f646" />


- Configured the bucket for **static website hosting**
  <img width="470" height="193" alt="image" src="https://github.com/user-attachments/assets/f55941b9-f298-4fc4-b5b8-5d97e242d1b4" />

  <img width="470" height="183" alt="image" src="https://github.com/user-attachments/assets/31d72f73-9efe-4184-b9f8-ed0a9c6f658d" />


- Created an **IAM user** and assigned S3 access permissions
  <img width="470" height="205" alt="image" src="https://github.com/user-attachments/assets/e17e69bc-d2aa-4d25-b08b-2a04e89de3ef" />
  
<img width="470" height="164" alt="image" src="https://github.com/user-attachments/assets/73ed982a-f391-4f6b-91e1-596a02ebd001" />

- Uploaded website files (HTML, CSS, images) to S3
- <img width="470" height="143" alt="image" src="https://github.com/user-attachments/assets/b80d5c9c-b7ee-4365-a204-8e6e7c1dae03" />

<img width="470" height="202" alt="image" src="https://github.com/user-attachments/assets/9874c3f7-d9e7-4dcb-a1fd-b692df314b0d" />


- Enabled **public access** for website hosting  
- Verified the website via the S3 endpoint
  
  <img width="470" height="203" alt="image" src="https://github.com/user-attachments/assets/cdb42aa3-733f-4898-b208-89f75d31fdb8" />
  <img width="470" height="144" alt="image" src="https://github.com/user-attachments/assets/9fe65d6f-c5e9-48ee-8e3d-d2b94b794b9e" />
  <img width="470" height="173" alt="image" src="https://github.com/user-attachments/assets/726c68d5-8b6f-475e-944b-361d1c4a32df" />
<img width="470" height="220" alt="image" src="https://github.com/user-attachments/assets/538f62dc-3370-43b4-9768-9891c0ae3009" />




---

##  Tools & Services
- Amazon S3  
- AWS CLI  
- IAM (Identity and Access Management)  
- Amazon EC2 (via Session Manager)  

---

##  Key Learning
- How to securely configure **IAM users and policies**  
- How **S3 static website hosting** works  
- Managing permissions using **ACLs and security settings**  

---

##  Automation
I created a bash script to simplify updates:

```bash
#!/bin/bash
aws s3 cp /home/ec2-user/sysops-activity-files/static-website/ s3://<my-bucket>/ --recursive --acl public-read
