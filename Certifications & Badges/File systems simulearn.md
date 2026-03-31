#  Cloud File Systems Lab – Amazon EFS
<img width="470" height="113" alt="image" src="https://github.com/user-attachments/assets/715e0b5e-ce5d-4fa5-b251-83a0a942faef" />

##  Project Overview
A pet modeling agency needed a scalable way to share client photos across multiple branch offices without managing physical storage.

This project demonstrates how to use **Amazon Elastic File System (EFS)** to create a shared, cloud-based file system accessible from multiple EC2 instances.

---

##  Objectives
- Deploy a shared file system using Amazon EFS  
- Configure mount targets for EC2 access  
- Ensure secure communication using security groups  
<img width="313" height="142" alt="image" src="https://github.com/user-attachments/assets/a9756438-cd68-4cd7-8c20-5378f1a1bf8e" />
---

##  Implementation
1. Created an **Amazon EFS file system**
2. Configured **mount targets** inside a VPC  
3. Connected **EC2 instances** to the file system  
4. Mounted EFS to store and access client photos  

---

##  Key Concepts
- **Amazon EFS** provides scalable, shared storage across multiple instances  
- Supports **high availability** across availability zones  
- Eliminates need for manual storage management  

---

##  Security
> An EC2 instance must belong to at least one security group.

- Security groups act as **virtual firewalls**
- Control **inbound and outbound traffic**
- Must allow communication between EC2 and EFS  
<img width="470" height="202" alt="image" src="https://github.com/user-attachments/assets/42c2b5f9-4a64-41aa-857a-81d661bb40e3" />
<img width="470" height="202" alt="image" src="https://github.com/user-attachments/assets/76267ed0-3d12-4be4-980b-ed0e8d600f00" />
<img width="470" height="202" alt="image" src="https://github.com/user-attachments/assets/dd17ff44-9202-4c76-b58d-78e1a7aa19df" />

<img width="470" height="308" alt="image" src="https://github.com/user-attachments/assets/c238d7a1-3b53-4a15-a5c5-1d77c7907762" />
<img width="470" height="237" alt="image" src="https://github.com/user-attachments/assets/b659aea4-3e8a-4743-86fe-89dba881e5c6" />
<img width="470" height="168" alt="image" src="https://github.com/user-attachments/assets/f1c9c9f1-bae9-4717-9439-1f3e3beb7cd5" />
<img width="470" height="212" alt="image" src="https://github.com/user-attachments/assets/536891f9-2fb7-41c9-a4a3-47f1c356fb3a" />
<img width="470" height="223" alt="image" src="https://github.com/user-attachments/assets/369d44af-dee7-4a76-986c-13a964c8e885" />
<img width="470" height="198" alt="image" src="https://github.com/user-attachments/assets/10fe9c43-9a26-4b63-972c-d6c54aa5e785" />

---

##  Result
The agency can now:
- Share files across locations  
- Scale storage automatically  
- Reduce infrastructure complexity  
<img width="470" height="180" alt="image" src="https://github.com/user-attachments/assets/5337e187-d372-43e6-a514-4a62eab50624" />
<img width="470" height="202" alt="image" src="https://github.com/user-attachments/assets/004463eb-3f50-4d5a-94a8-bd1ca2a2c2a9" />
<img width="470" height="227" alt="image" src="https://github.com/user-attachments/assets/fcac7b22-c12c-4b5c-8e8c-5ccc6bbbfac0" />
<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/31245651-244f-4894-a858-6ff09273e331" />
<img width="470" height="187" alt="image" src="https://github.com/user-attachments/assets/29cc055b-6973-488c-b784-0af533c79c84" />

---

##  Key Takeaway
Cloud file systems like EFS enable **simple, scalable, and secure data sharing** without physical infrastructure.

---




