# AWS Lab – Build RDS Database and Connect Web Application

## Overview
In this lab, a relational database was deployed using Amazon RDS and integrated with a web application running on an EC2 instance. The setup demonstrated high availability, secure connectivity, and real-time database interaction.

## Objectives
- Launched a highly available Amazon RDS instance (Multi-AZ)
- Configured secure database access from a web server
- Connected a web application to the database
- Verified real-time data interaction

## Architecture
Initial state:
- EC2 instance hosted both application and database
- 
  <img width="940" height="446" alt="image" src="https://github.com/user-attachments/assets/ae5beb6b-5ec6-4288-9efb-7ed17a029614" />

Final state:
- Database migrated to Amazon RDS (Multi-AZ)
- Application remained on EC2
- Secure communication via security groups
- 
  <img width="940" height="460" alt="image" src="https://github.com/user-attachments/assets/995b836a-7949-4606-8179-4fce739cc1e5" />

## Implementation

### Task 1: Security Group Configuration
Created a database security group allowing MySQL (3306) access from the web server security group.

<img width="940" height="430" alt="image" src="https://github.com/user-attachments/assets/0a342bb3-48aa-4d3b-890e-4ba2c11a3cd9" />

<img width="940" height="353" alt="image" src="https://github.com/user-attachments/assets/203a097d-b785-4c7a-b004-a675e5f78160" />



### Task 2: DB Subnet Group
Configured private subnets in two Availability Zones for high availability.

<img width="940" height="917" alt="image" src="https://github.com/user-attachments/assets/f0a6a562-fe1d-47fe-8efd-41584ab35bb2" />

<img width="940" height="325" alt="image" src="https://github.com/user-attachments/assets/b3203fc4-3d5b-4ce3-85ad-633141b2acc0" />

### Task 3: RDS Instance Deployment
Launched a MySQL RDS instance with:
- Multi-AZ deployment
- db.t3.medium instance class
- Custom database credentials

<img width="472" height="2811" alt="image" src="https://github.com/user-attachments/assets/f851c1fa-ddc9-46a7-92e8-b9069a2d623d" />

<img width="940" height="369" alt="image" src="https://github.com/user-attachments/assets/09616193-1bf6-47c3-bb7b-53ac1278320c" />

<img width="940" height="354" alt="image" src="https://github.com/user-attachments/assets/976c0688-f284-409f-9fcf-4c4de4057e0e" />

### Task 4: Application Integration
Connected the web application to RDS using endpoint and credentials. Verified functionality through an address book application.

<img width="940" height="328" alt="image" src="https://github.com/user-attachments/assets/80bfe0b1-66fb-4b0a-acf3-08738815a5a8" />
<img width="940" height="346" alt="image" src="https://github.com/user-attachments/assets/5a4eee6f-0d12-49f8-bdd9-dd08c1a4cc2e" />


## Result
- Fully functional RDS-backed web application
- Secure and scalable architecture
- High availability with Multi-AZ deployment

## Key Takeaways
- RDS simplifies database management and scaling
- Multi-AZ improves reliability and fault tolerance
- Security groups are critical for controlled access
