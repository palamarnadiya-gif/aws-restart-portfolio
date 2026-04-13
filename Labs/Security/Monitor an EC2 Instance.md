# Infrastructure Monitoring & Automated Incident Response

## Project Overview
Engineered an automated monitoring solution to maintain system performance baselines and security integrity for EC2 infrastructure. This project simulated a proactive defense against unauthorized resource exhaustion (e.g., malware or crypto-jacking) by implementing real-time alerting and observability dashboards.

## Technical Architecture
* Cloud Provider: AWS (EC2, CloudWatch, SNS)
* Linux Administration: Amazon Linux 2, Stress-ng utility
* Security Focus: Incident Detection & Automated Alerting

---

## 1. Notification Infrastructure Deployment
Established a centralized notification hub using Amazon SNS to ensure immediate stakeholder awareness during system anomalies.

* Created a Standard SNS Topic titled MyCwAlarm.
* Configured an email subscription protocol for real-time alert delivery.
* Validated the communication handshake through endpoint confirmation.

<img width="470" height="170" alt="image" src="https://github.com/user-attachments/assets/028e9759-8155-4731-b0c6-0fba26509c2e" />

<img width="470" height="280" alt="image" src="https://github.com/user-attachments/assets/c3eebae0-db0d-4542-80f1-e3c414205881" />

<img width="470" height="125" alt="image" src="https://github.com/user-attachments/assets/553f9659-14ce-48c0-837d-e035190e653f" />
<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/cdcda37d-0835-4b43-a2ea-77f76f553b61" />
<img width="47" height="115" alt="image" src="https://github.com/user-attachments/assets/27d9bb7d-ca7e-40a3-8692-4535ca076175" />

---

## 2. CloudWatch Alarm Engineering
Developed precise monitoring logic to distinguish between standard operations and potential security incidents.

* Defined a Metric Alarm for CPUUtilization.
* Set a deterministic threshold of >60% for a duration of 1 minute.
* Linked the "In Alarm" state to the SNS trigger for automated incident reporting.

<img width="470" height="255" alt="image" src="https://github.com/user-attachments/assets/48733d67-6722-4825-b9c8-19469234d531" />

<img width="470" height="450" alt="image" src="https://github.com/user-attachments/assets/a54b7acd-e2b2-435f-904a-2b52390aa45f" />

<img width="470" height="540" alt="image" src="https://github.com/user-attachments/assets/cb36cf9d-29d4-408e-809f-6a2efa15a938" />
<img width="470" height="300" alt="image" src="https://github.com/user-attachments/assets/63507673-2c17-47ba-afbb-a0bf57e48fa2" />
<img width="470" height="650" alt="image" src="https://github.com/user-attachments/assets/280c5e69-a480-4871-9672-885253ee7b67" />
---

## 3. Incident Simulation & Stress Testing
Executed a controlled stress test to validate the end-to-end integrity of the monitoring pipeline.

* Deployed the stress utility on the target EC2 instance.
* Forced a 100% CPU saturation to simulate a malicious takeover.
* Command Executed: sudo stress --cpu 10 -v --timeout 400s



<img width="470" height="150" alt="image" src="https://github.com/user-attachments/assets/460fdafd-713f-4e26-8f5d-ba1afa17a3f3" />
<img width="470" height="340" alt="image" src="https://github.com/user-attachments/assets/d4a58fea-93b6-4f99-80a7-c3c073c9ffac" />

<img width="470" height="350" alt="image" src="https://github.com/user-attachments/assets/abaf1308-fa50-4018-8b54-5aa8a287f708" />
---

## 4. Operational Observability & Verification
Confirmed the successful execution of the automated response and visualized the data.

* Received the automated SNS email notification within the defined 1-minute window.



<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/0bf426dc-ea2c-4c25-9129-663e1fc0bbb8" />
<img width="470" height="270" alt="image" src="https://github.com/user-attachments/assets/a9ee448f-177f-44f2-8472-e92c0d09489a" />

* Constructed a custom CloudWatch Dashboard to visualize the spike and recovery phases.

<img width="470" height="250" alt="image" src="https://github.com/user-attachments/assets/d105b894-b700-43d1-9376-fe4d3ec61885" />

<img width="470" height="155" alt="image" src="https://github.com/user-attachments/assets/934dcc03-9c5f-439b-903c-a812e776cae8" />
<img width="470" height="130" alt="image" src="https://github.com/user-attachments/assets/0cb4acb1-7d4a-4aad-a886-502e10bd5f28" />

---

## Key Achievements
* Reduced Mean Time to Detect (MTTD) for resource anomalies to under 60 seconds.
* Implemented a zero-latency notification pipeline for critical system events.
* Created high-level visibility for stakeholders via CloudWatch Dashboards.
