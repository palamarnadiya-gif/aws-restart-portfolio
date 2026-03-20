#  AWS Lab – EC2 LAMP Instance Deployment & Troubleshooting

##  Overview
In this lab, I deployed an **Amazon EC2 instance** configured with a **LAMP stack** (Linux, Apache, MariaDB, PHP) to host a Café Web Application.  
I used the **AWS CLI** to automate the instance creation and troubleshoot common deployment issues.

---

##  Objectives
- Launch an EC2 instance using AWS CLI  
- Troubleshoot AWS CLI commands and EC2 settings  
- Deploy a LAMP stack and verify web server functionality  

---

##  Tools & Services
- Amazon EC2  
- AWS CLI  
- EC2 Instance Connect  
- AWS Systems Manager Parameter Store  
- IAM Roles & Security Groups  
- nmap (for port scanning and troubleshooting)  

---

##  What I Did
1. Connected to the **CLI Host EC2 instance** using EC2 Instance Connect
   <img width="940" height="295" alt="image" src="https://github.com/user-attachments/assets/0d3da463-8bdd-41f4-b162-6ec28b929da1" />
   <img width="940" height="407" alt="image" src="https://github.com/user-attachments/assets/f83f44ab-b528-477c-a783-b7d19e3849d4" />

2. Configured the **AWS CLI** with provided credentials
   <img width="940" height="263" alt="image" src="https://github.com/user-attachments/assets/6c304566-dfbf-4172-bc7b-7a5cdf4d76b1" />

3. Analyzed and ran a **shell script** to launch the EC2 LAMP instance
   <img width="940" height="337" alt="image" src="https://github.com/user-attachments/assets/2359fcf7-2f47-4706-938a-7794e0d94a78" />

    
4. Identified and fixed script issues:
   - Invalid AMI ID  
   - Missing or closed ports for web server access
     <img width="940" height="443" alt="image" src="https://github.com/user-attachments/assets/2b7568f8-071a-4834-99d7-b2082992bb8e" />

5. Verified the **Apache web server, PHP, and MariaDB** installation using logs and browser tests
    <img width="940" height="434" alt="image" src="https://github.com/user-attachments/assets/b9018f1a-4bce-4f9a-b42a-7f29946e092c" />

7. Confirmed the **Café Web Application** was functional:
   - Home page accessible  
   - Menu ordering system working  
   - Order history captured in the database  

---

##  Challenges & Solutions
**Problem 1:** Script failed due to invalid AMI ID  
**Solution:** Updated script with the correct AMI ID from Parameter Store  

**Problem 2:** Web page not loading after instance launch  
**Solution:**  
- Opened **TCP port 80** in the security group  
- Started and enabled Apache service:
  ```bash
  sudo systemctl start httpd
  sudo systemctl enable httpd
