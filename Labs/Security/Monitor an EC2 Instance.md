# Monitor an EC2 Instance (CloudWatch, SNS, CPU Alarm Lab)

## Lab Overview

Logging and monitoring were used together to ensure system performance baselines and security requirements were continuously met.

Logging was used to record and store event data as log files, providing detailed visibility into system behavior. Monitoring was used to collect and analyze metrics to ensure optimal performance and detect unusual activity such as unauthorized access or resource abuse.

In this lab, an Amazon CloudWatch alarm was configured to trigger when an Amazon EC2 instance exceeded a CPU utilization threshold. An Amazon SNS subscription was created to send email notifications when the alarm was triggered. A stress test was then executed on the EC2 instance to simulate a CPU spike, causing the alarm to activate.

---

## Objectives

After completing this lab, the following were achieved:

- Created an Amazon SNS notification
- Configured a CloudWatch alarm
- Stress tested an EC2 instance
- Confirmed SNS email notifications were sent
- Created a CloudWatch dashboard

---

## Task 1: Configure Amazon SNS

An SNS topic was created to send notifications when alarms were triggered.

### Steps performed

- Amazon SNS service was opened.
- A topic named **MyCwAlarm** was created (Standard type).
- An email subscription was added using a valid email address.
- The subscription status initially remained **Pending confirmation**.
- The confirmation email was opened and the subscription was confirmed.
- The status changed to **Confirmed** in SNS.

### Result

An SNS topic was successfully configured and linked to an email endpoint for alert delivery.

---

## Task 2: Create a CloudWatch Alarm

CloudWatch metrics were reviewed and an alarm was created based on EC2 CPU utilization.

### Steps performed

- CloudWatch service was opened.
- EC2 metrics were explored under **Per-Instance Metrics**.
- CPUUtilization for the **Stress Test** instance was selected.
- A CloudWatch alarm was created with the following configuration:

#### Metric configuration
- Metric: CPUUtilization  
- Statistic: Average  
- Period: 1 minute  

#### Conditions
- Threshold type: Static  
- Condition: CPUUtilization > 60%

#### Actions
- Alarm state: In alarm  
- SNS topic: **MyCwAlarm**

- Alarm name: **LabCPUUtilizationAlarm**

### Result

A CloudWatch alarm was successfully created to monitor CPU usage and send SNS notifications when the threshold was exceeded.

---

## Task 3: Test the CloudWatch Alarm

A CPU stress test was executed to trigger the alarm.

### Steps performed

- The EC2 instance connection URL was opened via Session Manager.
- A CPU stress command was executed:
  ```bash
  sudo stress --cpu 10 -v --timeout 400s
