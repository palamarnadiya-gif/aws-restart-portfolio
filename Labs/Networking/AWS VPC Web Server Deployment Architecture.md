<!-- ========================= -->
<!-- PREMIUM PORTFOLIO README -->
<!-- ========================= -->

<h1 align="center">AWS VPC Web Server Deployment</h1>

<p align="center">
Custom Cloud Network with Public Web Application Hosting
</p>

<hr>

<h2>Project Overview</h2>
<p>
Built and configured a custom Amazon VPC to deploy a publicly accessible web server. The implementation followed a structured approach to create networking components, enforce security controls, and validate end-to-end connectivity.
</p>

<p>
The solution replicated a real-world cloud scenario where a customer required a scalable and secure environment for hosting a web application.
</p>

<hr>

<h2>Architecture Components</h2>

<ul>
<li>VPC (10.0.0.0/16)</li>
<li>Public and Private Subnets</li>
<li>Internet Gateway (IGW)</li>
<li>NAT Gateway</li>
<li>Route Tables (Public and Private)</li>
<li>Security Group (HTTP access)</li>
<li>Amazon EC2 Instance (Web Server)</li>
</ul>

<img width="470" height="240" alt="image" src="https://github.com/user-attachments/assets/d1e302c5-c827-42f4-8387-f7ac9bc65d35" />

<hr>

<h2>Implementation Steps</h2>

<h3>1. VPC Creation</h3>
<p>
Created a VPC using the AWS wizard with integrated networking components.
</p>

<pre><code>VPC Name: Lab VPC
CIDR: 10.0.0.0/16</code></pre>

<img width="466" height="727" alt="image" src="https://github.com/user-attachments/assets/6695849c-142b-498e-9382-344c126643b9" />



<img width="470" height="203" alt="image" src="https://github.com/user-attachments/assets/9c5a6916-aad7-412b-9525-731896de0996" />


<hr>

<h3>2. Subnet Configuration</h3>
<p>
Provisioned both public and private subnets within the VPC for resource segmentation.
</p>

<pre><code>Public Subnet: 10.0.0.0/24
Private Subnet: 10.0.1.0/24</code></pre>

<img width="470" height="420" alt="image" src="https://github.com/user-attachments/assets/ce58d41e-411e-468e-90d6-181125e750de" />

<img width="470" height="151" alt="image" src="https://github.com/user-attachments/assets/d4268af2-ae15-47c9-aff1-299487b3fbd0" />

<img width="470" height="420" alt="image" src="https://github.com/user-attachments/assets/96ba1081-b9b7-4a1d-a00b-8463ce455d39" />

<hr>

<h3>3. Additional Subnets</h3>
<p>
Extended the architecture with additional subnets to support scalability.
</p>

<pre><code>Public Subnet 2: 10.0.2.0/24
Private Subnet 2: 10.0.3.0/24</code></pre>

<img width="470" height="177" alt="image" src="https://github.com/user-attachments/assets/2e8ec7c2-cfe4-4936-a891-7c37bf9bed81" />


<hr>

<h3>4. Route Table Configuration</h3>
<p>
Configured routing to ensure correct traffic flow between subnets and the internet.
</p>

<ul>
<li>Public subnets linked to public route table</li>
<li>Private subnets linked to private route table</li>
</ul>

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/119442e6-e2e5-4cd4-bf38-96a2c8b6d34e" />

<img width="470" height="155" alt="image" src="https://github.com/user-attachments/assets/2b05da3a-2335-4d8d-a352-181f5d31fe12" />

<img width="470" height="205" alt="image" src="https://github.com/user-attachments/assets/f110eb4f-d11b-4a30-ad56-ee34549b5dff" />

<img width="470" height="185" alt="image" src="https://github.com/user-attachments/assets/13ad4265-6f09-4fe5-accc-cc845e520c08" />

<img width="470" height="187" alt="image" src="https://github.com/user-attachments/assets/c489b860-19e3-4c88-92f2-62a7f234774d" />


<img width="470" height="241" alt="image" src="https://github.com/user-attachments/assets/00704530-0b66-45c5-b3e5-0e79d09e61f9" />

<hr>

<h3>5. Security Group Setup</h3>
<p>
Created a security group to allow inbound HTTP traffic to the web server.
</p>

<pre><code>Inbound:
HTTP (80) → 0.0.0.0/0

Outbound:
All traffic allowed</code></pre>

<img width="470" height="211" alt="image" src="https://github.com/user-attachments/assets/e91f7df0-a92a-4628-9253-c6f5fc83e775" />

<img width="470" height="205" alt="image" src="https://github.com/user-attachments/assets/fdbf1dab-67b5-462a-a214-b811827fd83d" />

<hr>

<h3>6. EC2 Web Server Deployment</h3>
<p>
Launched an EC2 instance in the public subnet and configured it as a web server using a bootstrap script.
</p>

<pre><code>Instance: Web Server 1
AMI: Amazon Linux 2
Type: t3.micro
Subnet: Public Subnet 2</code></pre>

<p><strong>User Data:</strong></p>

<pre><code>#!/bin/bash
yum install -y httpd mysql php
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
unzip lab-app.zip -d /var/www/html/
chkconfig httpd on
service httpd start</code></pre>

<img width="470" height="125" alt="image" src="https://github.com/user-attachments/assets/f0d261d8-0a45-4e0c-a465-b426e1ecbaef" />

<img width="470" height="151" alt="image" src="https://github.com/user-attachments/assets/8c86abc3-9ec4-4b21-8ce6-738df593fa79" />

<img width="470" height="225" alt="image" src="https://github.com/user-attachments/assets/6bb7d6ef-c394-4c40-b9c3-9a545b1b5ee0" />

<hr>

<h3>7. Web Server Validation</h3>
<p>
Verified successful deployment by accessing the application via the EC2 public DNS.
</p>

<pre><code>http://&lt;public-dns&gt;</code></pre>

<p>
The web page loaded successfully, confirming proper configuration of networking and services.
</p>

<img width="467" height="284" alt="image" src="https://github.com/user-attachments/assets/d3d7c056-c50c-42db-bf08-dcc7ce718903" />

<img width="470" height="221" alt="image" src="https://github.com/user-attachments/assets/d28011df-24f3-4bb1-8871-cc607906c0ff" />

<hr>

<h2>Key Outcomes</h2>

<ul>
<li>Built a complete VPC architecture with public and private segmentation</li>
<li>Enabled internet access via IGW and NAT Gateway</li>
<li>Deployed a functional web server on EC2</li>
<li>Validated connectivity through public DNS access</li>
<li>Applied structured cloud networking design principles</li>
</ul>

<hr>

<h2>Technical Highlights</h2>

<ul>
<li>End-to-end AWS VPC deployment</li>
<li>Subnet and routing configuration</li>
<li>Security group implementation</li>
<li>Automated EC2 configuration using user data</li>
<li>Practical validation of web application hosting</li>
</ul>

<hr>

<h2>Conclusion</h2>

<p>
Delivered a structured AWS networking and compute solution capable of hosting a public web application. Demonstrated practical cloud engineering skills in infrastructure setup, security configuration, and service validation.
</p>
