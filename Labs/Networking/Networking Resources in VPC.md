<!-- ========================= -->
<!-- PREMIUM PORTFOLIO README -->
<!-- ========================= -->

<h1 align="center">AWS VPC Networking Architecture Deployment</h1>

<p align="center">
Production-Grade Virtual Network with Full Internet Connectivity and Security Controls
</p>

<hr>

<h2>Project Overview</h2>
<p>
Designed and implemented a fully functional networking environment in Amazon VPC to enable secure outbound internet connectivity from cloud resources. The solution replicated a real-world troubleshooting scenario where network traffic could not reach external endpoints.
</p>



<p>
The architecture was built from scratch using a structured, top-down approach, ensuring correct routing, security configuration, and resource association across all networking layers.
</p>

<img width="470" height="260" alt="image" src="https://github.com/user-attachments/assets/c1e61613-89c4-4eb3-8c43-95729a40363b" />
<hr>

<h2>Architecture Components</h2>

<ul>
<li>Custom VPC (CIDR: 192.168.0.0/18)</li>
<li>Public Subnet</li>
<li>Internet Gateway (IGW)</li>
<li>Route Table with internet routing</li>
<li>Network ACL (stateless subnet firewall)</li>
<li>Security Group (stateful instance firewall)</li>
<li>Amazon EC2 Instance (Amazon Linux)</li>
</ul>

<hr>

<h2>Implementation Steps</h2>

<h3>1. VPC Creation</h3>
<p>
Created a custom Virtual Private Cloud to serve as the isolated network foundation for all resources.
</p>

<pre><code>VPC Name: Test VPC
CIDR Block: 192.168.0.0/18</code></pre>

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/c8fe323e-a6f5-41b8-91a6-f97f05d7e1c2" />


<hr>

<h3>2. Subnet Configuration</h3>
<p>
Provisioned a public subnet within the VPC to host internet-facing resources.
</p>

<pre><code>Subnet Type: Public
CIDR Block: 192.168.1.0/26</code></pre>

<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/049e32d6-7332-4600-bd20-67a6f0ccf334" />


<hr>

<h3>3. Route Table Setup</h3>
<p>
Configured a route table to control traffic flow and enable internet-bound routing.
</p>

<pre><code>Route:
Destination: 0.0.0.0/0
Target: Internet Gateway</code></pre>

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/c32dfcf0-2fea-4507-8494-c5cf3d2cb195" />

<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/256529f0-d0d1-4460-a133-753d061ef489" />

<hr>

<h3>4. Internet Gateway Deployment</h3>
<p>
Deployed and attached an Internet Gateway to enable communication between the VPC and external networks.
</p>

<img width="470" height="190" alt="image" src="https://github.com/user-attachments/assets/f33ed6db-ac13-459d-9ea5-b27f7277b186" />

<img width="470" height="160" alt="image" src="https://github.com/user-attachments/assets/099e5cbf-664a-442a-a2c9-6f81ef6d28d2" />
<hr>

<h3>5. Subnet Association</h3>
<p>
Linked the public subnet with the route table to ensure proper routing of outbound traffic.
</p>



<img width="470" height="194" alt="image" src="https://github.com/user-attachments/assets/0907c4c3-4350-4c7a-a8ff-189d16be2295" />

<hr>

<h3>6. Network ACL Configuration</h3>
<p>
Implemented a Network Access Control List at the subnet level allowing all inbound and outbound traffic for testing connectivity.
</p>

<pre><code>Inbound Rule: Allow ALL (0.0.0.0/0)
Outbound Rule: Allow ALL (0.0.0.0/0)</code></pre>

<hr>

<h3>7. Security Group Setup</h3>
<p>
Configured a security group at the instance level to allow essential traffic.
</p>

<pre><code>Inbound:
- SSH (22) from 0.0.0.0/0
- HTTP (80) from 0.0.0.0/0
- HTTPS (443) from 0.0.0.0/0

Outbound:
- All traffic allowed</code></pre>

<hr>

<h3>8. EC2 Instance Deployment</h3>
<p>
Launched an Amazon EC2 instance in the public subnet with automatic public IP assignment.
</p>

<pre><code>AMI: Amazon Linux 2023
Instance Type: t3.micro
Subnet: Public Subnet</code></pre>

<hr>

<h3>9. Connectivity Validation</h3>
<p>
Established SSH connection to the instance and verified outbound internet connectivity using ICMP requests.
</p>

<pre><code>ping google.com</code></pre>

<p>
Successful responses confirmed correct routing, gateway configuration, and firewall settings.
</p>

<hr>

<h2>Key Outcomes</h2>

<ul>
<li>Established a fully routable VPC with internet connectivity</li>
<li>Validated routing via Internet Gateway and Route Tables</li>
<li>Configured layered security using Security Groups and NACLs</li>
<li>Successfully tested outbound connectivity from EC2</li>
<li>Applied structured troubleshooting methodology aligned with networking layers</li>
</ul>

<hr>

<h2>Technical Highlights</h2>

<ul>
<li>End-to-end VPC network design and deployment</li>
<li>Traffic routing and subnet association strategy</li>
<li>Firewall configuration at subnet and instance levels</li>
<li>Hands-on validation using real network diagnostics</li>
<li>Cloud networking aligned with OSI-layer thinking</li>
</ul>

<hr>

<h2>Conclusion</h2>

<p>
Delivered a production-style AWS networking solution enabling secure and functional internet access from cloud resources. The implementation demonstrated practical cloud engineering skills, including infrastructure design, security configuration, and real-world troubleshooting.
</p>
