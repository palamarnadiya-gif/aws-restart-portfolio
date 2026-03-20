# Amazon EBS Lab Portfolio

## Overview
In this lab, I worked with **Amazon Elastic Block Store (EBS)**, a scalable, high-performance block storage service for **Amazon EC2**. I created EBS volumes, attached them to instances, configured file systems, and performed snapshot backups and restores.

## Objectives Achieved
- Created an EBS volume.
- Attached and mounted an EBS volume to an EC2 instance.
- Created a snapshot of an EBS volume.
- Restored a new EBS volume from a snapshot.
  <img width="940" height="280" alt="image" src="https://github.com/user-attachments/assets/0c17da90-e908-47ec-9a48-706c4e1e2804" />



## Key Tasks Completed

### 1. Created a New EBS Volume
- Launched EC2 instance and noted its Availability Zone.
- Created a **1 GiB General Purpose SSD (gp2)** volume.
- Tagged the volume as `My Volume`.
  <img width="940" height="435" alt="image" src="https://github.com/user-attachments/assets/317bae19-89cd-4e95-a616-77abcbcf9c8e" />

  <img width="940" height="339" alt="image" src="https://github.com/user-attachments/assets/69412188-eb87-4342-aaf7-147536629e2f" />
  <img width="940" height="407" alt="image" src="https://github.com/user-attachments/assets/d4782ca9-3adf-4d9b-a371-4c85f0c99376" />

  <img width="940" height="233" alt="image" src="https://github.com/user-attachments/assets/6d338ad5-4c2b-4993-b132-30d2e0e6981e" />

### 2. Attached the Volume to EC2
- Attached volume to the Lab instance as `/dev/sdb`.
- Verified that the volume status changed to `In-use`.
  <img width="940" height="478" alt="image" src="https://github.com/user-attachments/assets/46df3766-50b2-4921-9828-1082b905dc9a" />
  <img width="940" height="399" alt="image" src="https://github.com/user-attachments/assets/017ea8f7-a1f5-4007-bbe1-fc9ed65971b8" />
  <img width="940" height="428" alt="image" src="https://github.com/user-attachments/assets/50c7e073-71b9-4a40-852a-2e590e46c9fe" />

### 3. Connected to EC2 Instance
- Used **EC2 Instance Connect** to access the Lab instance.
- Prepared terminal for subsequent volume operations.
  
<img width="940" height="401" alt="image" src="https://github.com/user-attachments/assets/9773588a-0dcd-4efa-a07c-b3c9f39bd95d" />

### 4. Configured File System
- Created an **ext3** file system on `/dev/sdb`.
- Mounted volume to `/mnt/data-store`.
- Verified storage and created a test file `file.txt`.

  <img width="940" height="443" alt="image" src="https://github.com/user-attachments/assets/f165eb08-0b70-46ac-958a-cc9042ee427a" />
  <img width="940" height="946" alt="image" src="https://github.com/user-attachments/assets/638fda16-a915-4044-a11e-d4dddaf88b24" />
<img width="940" height="469" alt="image" src="https://github.com/user-attachments/assets/f4797f19-728b-4841-9433-a930d8738eea" />
<img width="940" height="358" alt="image" src="https://github.com/user-attachments/assets/a92dd46d-ef5d-4c8e-90c4-9afcf563478b" />

### 5. Created a Snapshot
- Created a snapshot of `My Volume` and tagged it as `My Snapshot`.
- Verified snapshot completion and deleted test file from the volume.
  
<img width="940" height="405" alt="image" src="https://github.com/user-attachments/assets/27c8a367-e457-483d-9933-2e3ba91610eb" />
<img width="940" height="379" alt="image" src="https://github.com/user-attachments/assets/8019ea86-9bb1-4d7e-94ec-6c6a64f5b9a4" />
<img width="940" height="457" alt="image" src="https://github.com/user-attachments/assets/d040f85d-aee2-4dcd-888c-f863362e2428" />
<img width="940" height="308" alt="image" src="https://github.com/user-attachments/assets/8bcac7c2-613e-478f-9320-18006a096611" />

### 6. Restored from Snapshot
- Created a new EBS volume from snapshot and tagged as `Restored Volume`.
- Attached restored volume to EC2 instance as `/dev/sdc`.
- Mounted it to `/mnt/data-store2` and verified the restored `file.txt`.
  <img width="940" height="428" alt="image" src="https://github.com/user-attachments/assets/606bc8f7-3a94-4279-bc39-6e88af106138" />
  <img width="940" height="334" alt="image" src="https://github.com/user-attachments/assets/eefc729f-1801-46b0-a360-4a2a8ce4acfc" />
  <img width="940" height="373" alt="image" src="https://github.com/user-attachments/assets/010e2115-82d9-4c32-8c62-32e88794e974" />
<img width="940" height="470" alt="image" src="https://github.com/user-attachments/assets/dde8816a-bbcd-4096-82bd-d253a4be947b" />
<img width="940" height="352" alt="image" src="https://github.com/user-attachments/assets/f188f634-686c-4cbc-aac6-3757d6a48f14" />
<img width="940" height="331" alt="image" src="https://github.com/user-attachments/assets/a74f3a1e-ed40-4d9b-8eb9-dd0e97618231" />
<img width="940" height="433" alt="image" src="https://github.com/user-attachments/assets/90079977-4bdd-418c-9fe7-7163798d27c0" />
<img width="940" height="185" alt="image" src="https://github.com/user-attachments/assets/327459a1-7667-44b2-8ecb-381b9897d3ff" />

## Conclusion
Successfully completed all objectives:
- Volume creation and attachment
- File system configuration
- Snapshot creation
- Volume restoration from snapshot

## References
- [Amazon EBS Documentation](https://aws.amazon.com/ebs/)
- [Connect to Your Linux Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)
