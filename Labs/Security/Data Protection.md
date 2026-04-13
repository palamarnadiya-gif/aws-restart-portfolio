# Data Protection Using Encryption (AWS KMS Lab)

## Overview
In this lab, I worked with encryption concepts using AWS services. I used AWS Key Management Service (KMS) to create and manage encryption keys, and I applied encryption and decryption operations on files using the AWS Encryption CLI.

Encryption was used to convert readable data (plaintext) into unreadable data (ciphertext), ensuring confidentiality and data protection. I then reversed the process by decrypting the data back into its original form.

---

## Objectives
I successfully:
- Created an AWS KMS encryption key  
- Configured an EC2 instance using Session Manager  
- Installed the AWS Encryption CLI  
- Encrypted plaintext files using a KMS key  
- Decrypted ciphertext back into readable data  

---

## Environment
The lab environment included:
- One EC2 instance named **File Server**
- IAM role with Systems Manager Session Manager access  
- AWS KMS service enabled  

---

## Task 1: Create an AWS KMS Key

### What I did
I created a symmetric encryption key in AWS KMS to use for encrypting and decrypting data files.

### Steps completed
1. Opened AWS KMS in the AWS Console  
2. Created a new key  
3. Selected **Symmetric key type**  
4. Configured key details:
   - Alias: `MyKMSKey`
   - Description: Key used for encrypting and decrypting data files  

5. Assigned permissions:
   - IAM role: `voclabs`  

6. Copied the **KMS Key ARN** for later use
7. 
   <img width="470" height="600" alt="image" src="https://github.com/user-attachments/assets/ad405995-bf2f-4fe8-b7a7-902609e51f4f" />


### Result
A functional symmetric KMS key was created and ready for encryption operations.

<img width="470" height="141" alt="image" src="https://github.com/user-attachments/assets/20149787-a827-4248-b8ed-03b954982566" />

<img width="470" height="192" alt="image" src="https://github.com/user-attachments/assets/a1a01c63-20e6-4d09-b450-285f7fb09176" />

---

## Task 2: Configure the File Server Instance

### What I did
I connected to the EC2 instance and prepared the environment for encryption tasks.

### Steps completed
1. Connected to the **File Server** instance using Session Manager  
2. Configured AWS credentials using:
   - `aws configure`  
3. Replaced temporary credentials with lab-provided credentials  
4. Verified credentials file content  
5. Installed AWS Encryption CLI:
   - `aws-encryption-sdk-cli`  
6. Updated system PATH to use encryption tools
   
   <img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/40f5daf5-0a9f-4840-8c3a-1b513657a536" />

<img width="450" height="120" alt="image" src="https://github.com/user-attachments/assets/7df7819b-5d5e-4c23-8969-7cbc23de82d9" />


### Result
The EC2 instance was successfully configured to use AWS KMS and the encryption CLI.

<img width="470" height="480" alt="image" src="https://github.com/user-attachments/assets/0d1eb572-de93-451f-8907-fa9bc6365e25" />

---

## Task 3: Encrypt and Decrypt Data

### What I did
I created sample files, encrypted them using AWS KMS, and then decrypted them back to plaintext.

---

### Step 1: Create sample files
I created three text files:
- secret1.txt  
- secret2.txt  
- secret3.txt  

I added sample sensitive content:
- `"TOP SECRET 1!!!"`  
<img width="600" height="1150" alt="image" src="https://github.com/user-attachments/assets/73c3275b-f6bd-4ec6-8ff8-c72862af6aad" />

---

### Step 2: Prepare encryption
- Created an output directory  
- Stored KMS ARN in a variable (`keyArn`)  

---

### Step 3: Encrypt file
I ran the AWS Encryption CLI command to:
- Encrypt `secret1.txt`
- Use the KMS key
- Store encrypted output in `/output`
  
 <img width="460" height="270" alt="image" src="https://github.com/user-attachments/assets/c923dd77-b23e-4c05-8b2a-5e99e75da559" />


### Result
- A file named `secret1.txt.encrypted` was created  
- The original content became unreadable ciphertext  

---

### Step 4: Decrypt file
I used the decrypt command to:
- Restore the encrypted file back to readable form  
- Output the decrypted file
- 
  <img width="470" height="280" alt="image" src="https://github.com/user-attachments/assets/1aa551a7-7ef6-4a0f-89b0-5f66234fc5cd" />


### Result
- A decrypted file was created:  
  `secret1.txt.encrypted.decrypted`  
- The original plaintext content was restored successfully  

---

## Key Takeaways
- AWS KMS provides secure key management for encryption  
- Symmetric encryption uses the same key for encrypt and decrypt  
- AWS Encryption CLI simplifies encryption workflows  
- Encrypted data is unreadable without proper decryption keys  
- Session Manager enables secure EC2 access without SSH keys  

---

## Conclusion
By completing this lab, I successfully implemented end-to-end encryption using AWS KMS. I created encryption keys, configured a secure environment, encrypted sensitive data, and then decrypted it back to its original form, ensuring full understanding of data protection workflows in AWS.
