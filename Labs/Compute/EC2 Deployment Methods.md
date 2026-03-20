#  AWS Lab – EC2 Deployment Methods

##  Overview
In this lab, I worked with **Amazon EC2** to deploy infrastructure using both the **AWS Management Console** and the **AWS CLI**.  
I created a bastion host and used it to launch and configure a web server instance.

<img width="498" height="377" alt="image" src="https://github.com/user-attachments/assets/8468ba6e-8299-45ad-9e6f-a0df68aea776" />


---

##  What I Did
- Launched an **EC2 bastion host** via AWS Management Console
  <img width="940" height="283" alt="image" src="https://github.com/user-attachments/assets/cb4e5ac0-08e0-46a9-bc46-9e4d12049c89" 
     
  <img width="940" height="257" alt="image" src="https://github.com/user-attachments/assets/e8874927-cbe7-4887-b68b-3f1dc62047eb" />


- Connected securely using **EC2 Instance Connect**

<img width="940" height="399" alt="image" src="https://github.com/user-attachments/assets/4e509c6b-163c-414a-bc9b-6b812b1dc53c" />

<img width="940" height="391" alt="image" src="https://github.com/user-attachments/assets/45cdf049-f285-4148-9507-9381201912d9" />

- Used **AWS CLI** to deploy a second EC2 instance (web server)
  <img width="940" height="435" alt="image" src="https://github.com/user-attachments/assets/c23a28f9-9ea3-49f1-802e-1d8d8dead193" />

- Retrieved dynamic parameters (AMI, subnet, security group) using CLI  
- Configured the instance automatically using a **user data script**
  <img width="940" height="437" alt="image" src="https://github.com/user-attachments/assets/3722723f-f363-4eda-8af7-d953239d7a54" />

- Tested the deployed web server via public DNS
  <img width="940" height="428" alt="image" src="https://github.com/user-attachments/assets/732196db-e2b7-4e63-ab6d-cf66cc48c2b2" />

  <img width="940" height="297" alt="image" src="https://github.com/user-attachments/assets/1b80dd14-dce4-4a62-a60a-707b863b82b2" />


---

##  Tools & Services
- Amazon EC2  
- AWS CLI  
- EC2 Instance Connect  
- AWS Systems Manager (Parameter Store)  
- IAM Roles & Security Groups  

---

##  Key Concepts
- Difference between **manual vs automated deployment**  
- Use of **bastion host** for secure access  
- Dynamic infrastructure setup using **CLI scripts**  
- Automated configuration with **user data (Apache web server setup)**  

---

##  Deployment Approach
1. Created a **bastion host** in a public subnet  
2. Connected to it and used CLI to:
   - Retrieve latest **Amazon Linux AMI**
   - Get **Subnet ID** and **Security Group**
3. Launched a **web server instance** with:
   - Apache installation via user data  
   - HTTP access enabled  
4. Verified deployment using **public DNS**  

---

##  Challenges & Solution
**Problem:**
- Could not connect to EC2 instance
 
- Web page was not accessible
  <img width="940" height="661" alt="image" src="https://github.com/user-attachments/assets/9c3575e4-dccd-4ceb-9920-6f1d72b1d646" />
  

**Solution:**
- Allowed **SSH (port 22)** in the security group
   <img width="940" height="357" alt="image" src="https://github.com/user-attachments/assets/d7458f31-7423-4121-b030-c21bf5515143" />
  <img width="940" height="412" alt="image" src="https://github.com/user-attachments/assets/d0caf489-bfef-431f-b833-914d71ca5da0" />
- Started and enabled Apache:
  ```bash
  sudo systemctl start httpd
  sudo systemctl enable httpd
<img width="940" height="430" alt="image" src="https://github.com/user-attachments/assets/9d6f04d7-1a72-4ce4-a2c9-3a97120806f9" />

  <img width="940" height="295" alt="image" src="https://github.com/user-attachments/assets/461370e5-949d-4765-b1f3-ca2a82dda805" />  
