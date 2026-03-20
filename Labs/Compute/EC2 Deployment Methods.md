#  AWS Lab – EC2 Deployment Methods

##  Overview
In this lab, I worked with **Amazon EC2** to deploy infrastructure using both the **AWS Management Console** and the **AWS CLI**.  
I created a bastion host and used it to launch and configure a web server instance.

<img width="498" height="377" alt="image" src="https://github.com/user-attachments/assets/8468ba6e-8299-45ad-9e6f-a0df68aea776" />


---

##  What I Did
- Launched an **EC2 bastion host** via AWS Management Console  
- Connected securely using **EC2 Instance Connect**  
- Used **AWS CLI** to deploy a second EC2 instance (web server)  
- Retrieved dynamic parameters (AMI, subnet, security group) using CLI  
- Configured the instance automatically using a **user data script**  
- Tested the deployed web server via public DNS  

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

**Solution:**
- Allowed **SSH (port 22)** in the security group  
- Started and enabled Apache:
  ```bash
  sudo systemctl start httpd
  sudo systemctl enable httpd
