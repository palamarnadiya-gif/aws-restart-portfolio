
<h1>Introduction to Amazon EC2</h1>

<section>
<h2>Lab Overview</h2>

<p>
This lab provides a basic introduction to <strong>Amazon Elastic Compute Cloud (Amazon EC2)</strong>, 
one of the core services of Amazon Web Services (AWS).
</p>

<p>
Amazon EC2 allows users to create virtual servers in the cloud. These servers can be launched,
configured, resized, monitored, and terminated depending on the needs of an application.
</p>

<p class="highlight">
In this lab I practiced how to launch and manage a cloud server and understand how cloud
infrastructure can be scaled quickly when computing needs change.
</p>

</section>

<section>

<h2>What is Amazon EC2?</h2>

<p>
Amazon EC2 is a cloud computing service that provides secure and scalable virtual machines.
It allows developers and IT professionals to run applications without needing to manage
physical hardware.
</p>

<p>
Using EC2, servers can be created in minutes and adjusted at any time. This flexibility makes
cloud computing efficient and cost-effective because users only pay for the resources they use.
</p>

</section>

<section>

<h2>Why EC2 is Important</h2>

<ul>
<li>Quickly launch virtual servers in the cloud</li>
<li>Scale computing capacity up or down depending on demand</li>
<li>Pay only for the resources that are actually used</li>
<li>Run applications in a reliable and secure AWS environment</li>
<li>Build applications that are resilient to failures</li>
</ul>

</section>

<section>

<h2>Topics Covered in This Lab</h2>

<p>By completing this lab, I learned how to perform the following tasks:</p>

<ul>
<li>Launch a web server using an EC2 instance</li>
<li>Enable termination protection to prevent accidental deletion</li>
<li>Monitor the performance and status of the EC2 instance</li>
<li>Modify the security group to allow HTTP web traffic</li>
<li>Resize the EC2 instance to scale computing resources</li>
<li>Test termination protection</li>
<li>Safely terminate the EC2 instance when it is no longer needed</li>
</ul>

</section>

<section>

<h2>Skills Practiced</h2>

<ul>
<li>Cloud infrastructure management</li>
<li>Instance configuration</li>
<li>AWS security basics</li>
<li>Resource monitoring</li>
<li>Cloud scalability concepts</li>
</ul>

</section>

</body>
</html>
<img width="384" height="174.75" alt="image" src="https://github.com/user-attachments/assets/ee372ce4-5eff-4957-8940-919bc7513557" />









<h1>☁️ Introduction to Amazon EC2</h1>

<h2>Overview</h2>
<p>
In this lab, I worked with <strong>Amazon EC2</strong>, a core service of 
<strong>Amazon Web Services (AWS)</strong> that provides scalable virtual servers in the cloud.
The goal of this lab was to understand how to launch, configure, manage, and monitor an EC2 instance.
</p>

<p>
Amazon EC2 allows developers to quickly create virtual servers and scale computing capacity
depending on the needs of an application. This flexibility makes it possible to build reliable
and scalable cloud infrastructure while paying only for the resources that are actually used.
</p>

<hr>

<h2>Lab Objectives</h2>
<ul>
<li>Launch a web server with termination protection enabled</li>
<li>Monitor an EC2 instance</li>
<li>Modify the security group to allow HTTP traffic</li>
<li>Resize an EC2 instance to scale resources</li>
<li>Test termination protection</li>
<li>Terminate an EC2 instance safely</li>
</ul>

<hr>

<h2>Task 1: Launching an EC2 Instance</h2>

<p>
In this task, I launched a virtual server and configured it to automatically deploy a simple web server
using a <strong>User Data script</strong>. I also enabled <strong>termination protection</strong> to prevent
accidental deletion of the instance.
</p>

<h3>Steps I Performed</h3>

<h4>1. Accessed the EC2 Dashboard</h4>
<p>
I opened the AWS Management Console, navigated to the EC2 service, and selected
<strong>Launch Instance</strong> to begin creating a new virtual server.
</p>

<h4>2. Named the Instance</h4>
<p>
I named the instance <strong>"Web Server"</strong>. AWS automatically created a tag with
the key <strong>Name</strong> and the value <strong>Web Server</strong> to help identify the resource.
</p>

<h4>3. Selected an Amazon Machine Image (AMI)</h4>
<p>
I selected <strong>Amazon Linux 2023</strong>, which provides the operating system and
configuration template required to launch the server.
</p>

<h4>4. Selected the Instance Type</h4>
<p>
I chose the <strong>t3.micro</strong> instance type, which includes
<strong>2 virtual CPUs and 1 GiB of memory</strong>. This instance type is commonly used
for small workloads and learning environments.
</p>

<h4>5. Configured the Key Pair</h4>
<p>
For this lab, I proceeded <strong>without creating a key pair</strong>, because direct login
to the instance was not required.
</p>

<h4>6. Configured Networking</h4>
<p>
I launched the instance inside the <strong>Lab VPC</strong> and created a security group
called <strong>Web Server security group</strong>. I removed the SSH inbound rule to improve
security since remote login was not needed.
</p>

<h4>7. Configured Storage</h4>
<p>
I used the default storage configuration with an <strong>8 GiB Amazon Elastic Block Store (EBS)</strong>
volume, which serves as the root disk for the operating system.
</p>

<h4>8. Configured Advanced Settings</h4>
<p>
I enabled <strong>termination protection</strong> to prevent the instance from being accidentally deleted.
</p>

<p>I also added a <strong>User Data script</strong> that automatically:</p>

<ul>
<li>Installed the Apache web server</li>
<li>Enabled the web server to start automatically at boot</li>
<li>Started the web service</li>
<li>Created a simple HTML web page</li>
</ul>

<h4>9. Launched the Instance</h4>
<p>
After reviewing the configuration, I launched the EC2 instance. The instance status changed
from <strong>Pending</strong> to <strong>Running</strong> once the server successfully started.
</p>

<hr>

<h2>Instance Status</h2>

<p>
After deployment, I verified that the instance was operating correctly in the EC2 dashboard.
</p>

<ul>
<li><strong>Instance State:</strong> Running</li>
<li><strong>Status Checks:</strong> 3/3 checks passed</li>
</ul>

<p>
The instance also received a <strong>public DNS address</strong>, which allows the web server
to be accessed from the internet.
</p>

<hr>

<h2>Skills Practiced</h2>
<ul>
<li>Cloud infrastructure deployment</li>
<li>EC2 instance configuration</li>
<li>Security group management</li>
<li>Automated server setup using User Data scripts</li>
<li>Monitoring EC2 instance health and status</li>
</ul>
<img width="160" height="165.5" alt="image" src="https://github.com/user-attachments/assets/a540af6b-fdfb-4f4d-a240-19a08585fdbd" />


<img width="477.75" height="185.25" alt="image" src="https://github.com/user-attachments/assets/f58df4fb-85a9-4485-94a6-778d6fd24ec5" />
<img width="379.25" height="184.75" alt="image" src="https://github.com/user-attachments/assets/60c45e1e-e672-4ce1-978c-231b6434cbad" />


<img width="194.5" height="44.5" alt="image" src="https://github.com/user-attachments/assets/dac53294-97d0-4c90-8c9d-f6f21654f590" />










<img width="388.25" height="183.5" alt="image" src="https://github.com/user-attachments/assets/b9aee678-9fa3-4116-8dc3-06a0f46550a0" />


<img width="387.75" height="182.25" alt="image" src="https://github.com/user-attachments/assets/02c039f2-dfad-4d7f-aeaf-796268a8e2b8" />


<img width="387" height="165" alt="image" src="https://github.com/user-attachments/assets/c987132f-8920-40b0-82a6-0b24a98233e6" />

<img width="378" height="168.5" alt="image" src="https://github.com/user-attachments/assets/35cb3db9-fc8a-4223-931c-a9af3665075f" />













