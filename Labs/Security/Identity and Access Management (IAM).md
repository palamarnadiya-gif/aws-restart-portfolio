# Introduction to AWS Identity and Access Management (IAM) 

## Lab Overview
I worked with AWS Identity and Access Management (IAM) to understand how access control is managed in AWS. I explored how users, groups, and policies interact to control permissions for AWS services such as Amazon S3 and Amazon EC2.

IAM is used to manage:
- IAM users and their credentials (passwords, access keys, MFA)
- IAM groups for shared permissions
- IAM roles for delegated access
- IAM policies that define allowed or denied actions

  <img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/3696898b-7670-4420-8191-bd86b5578272" />


IAM ensures secure and controlled access to AWS resources.

---

## Objectives (Completed)
I successfully:
- Created and applied an IAM password policy
- Explored existing IAM users and groups
- Inspected IAM policies attached to groups
- Added users to groups with specific permissions
- Used IAM sign-in URL for authentication testing
- Verified how permissions affect AWS service access

---

## Task 1: IAM Password Policy Configuration
I updated the account-level password policy to enforce stronger security standards.

<img width="470" height="170" alt="image" src="https://github.com/user-attachments/assets/f46ff31c-9eea-4b1d-8006-88bffeb46101" />

### Actions performed:
- Navigated to IAM → Account settings
- Updated password policy:
  - Minimum password length set to **10 characters**
  - Enabled complexity requirements (mixed character types)
  - Password expiration set to **90 days**
  - Password reuse prevention set to **5 previous passwords**
    
   <img width="470" height="320" alt="image" src="https://github.com/user-attachments/assets/2fb5aafb-86aa-47c0-a816-8273d72fa092" />


### Result:
The updated policy applied to all IAM users in the account, strengthening overall security.

<img width="470" height="180" alt="image" src="https://github.com/user-attachments/assets/49f8fcce-2b1b-45b6-a074-eb621e6d3647" />

---

## Task 2: IAM Users and Groups Exploration
I reviewed existing IAM users and groups and analyzed how permissions were structured.

### IAM Users:
- user-1
- user-2
- user-3
  <img width="460" height="535" alt="image" src="https://github.com/user-attachments/assets/42f9dcbd-8bf0-4585-b2d6-f5b141671851" />


### IAM Groups:
- EC2-Admin
- EC2-Support
- S3-Support

  <img width="470" height="404" alt="image" src="https://github.com/user-attachments/assets/9fb97db1-fd1a-4be4-84ca-4d2f5c5fd86b" />

<img width="470" height="380" alt="image" src="https://github.com/user-attachments/assets/a665f94f-b187-4620-a60d-68b7c81b40fd" />

<img width="470" height="370" alt="image" src="https://github.com/user-attachments/assets/b04ff857-1434-4864-913e-0558dc4fda16" />


### Observations:
- user-1 initially had no permissions and was not part of any group
- Groups were used to assign permissions efficiently
- Managed policies (AWS-managed) were used for read-only access
- Inline policies were used for custom EC2 administrative permissions

### Key IAM Concepts:
- **Managed policies**: reusable policies attached to multiple users/groups
- **Inline policies**: directly attached to a single user/group
- IAM policies define:
  - Effect (Allow/Deny)
  - Action (API permissions)
  - Resource (AWS resources affected)

---

## Task 3: Adding Users to Groups
I assigned users to groups based on their roles.

### Assignments completed:
- user-1 → S3-Support
- user-2 → EC2-Support
- user-3 → EC2-Admin
<img width="470" height="270" alt="image" src="https://github.com/user-attachments/assets/9a8066a2-8b83-4f41-a4da-f2afe6d0ef21" />

<img width="470" height="170" alt="image" src="https://github.com/user-attachments/assets/39e80beb-738b-4d0f-a82b-ff5d6668c171" />

<img width="470" height="205" alt="image" src="https://github.com/user-attachments/assets/6b980d14-a1a4-4712-a9c7-8ce263db3eea" />

<img width="470" height="170" alt="image" src="https://github.com/user-attachments/assets/2930e5f7-083f-44e8-8d9d-3748f46a8ddf" />

### Result:
Each user inherited permissions from their assigned group:
- S3-Support → Read-only access to Amazon S3
- EC2-Support → Read-only access to Amazon EC2
- EC2-Admin → Full EC2 management (view, start, stop instances)

---

## Task 4: IAM Permission Testing

I tested access using the IAM sign-in URL in a private browser session.
<img width="470" height="204" alt="image" src="https://github.com/user-attachments/assets/2a77acd5-d731-439f-bd53-9e8b7463b1b1" />


### user-1 (S3-Support)
- Successfully accessed Amazon S3
- Could list and view buckets
- No access to EC2 (access denied)

### user-2 (EC2-Support)
- Could view EC2 instances (read-only access)
- Unable to stop instances (permission denied)
- No access to S3

### user-3 (EC2-Admin)
- Could view EC2 instances
- Successfully stopped an EC2 instance
- Demonstrated full administrative EC2 permissions
<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/4756180c-4fe5-4dc4-895d-a15ad6c32025" />

<img width="470" height="130" alt="image" src="https://github.com/user-attachments/assets/ea6ec4de-3d26-4cce-a171-3a8a00a3b9f7" />

<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/e29453ec-ac95-46d5-b35b-d1780d90a7b9" />

<img width="470" height="130" alt="image" src="https://github.com/user-attachments/assets/a4065e38-7a43-4708-949e-8e300187337b" />

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/283e7538-0e44-4e5b-a345-4bfe27f4f209" />

<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/22f45a4c-206d-4947-9083-dcdf68de03d5" />
<img width="470" height="170" alt="image" src="https://github.com/user-attachments/assets/3577a422-e0cb-4bb9-961c-2f2f552e3801" />

---

## Key Takeaways
- IAM enforces least-privilege access control
- Groups simplify permission management
- Policies define precise access rules
- Managed policies reduce complexity
- Inline policies allow custom permission control
- Testing access is critical for validating security setup

---

## Conclusion
I successfully completed IAM configuration and testing tasks, including password policy setup, user-group assignment, and permission validation across multiple AWS services.

### Final Outcome:
- Secure IAM structure implemented
- Role-based access control applied correctly
- Permissions verified through real user testing
