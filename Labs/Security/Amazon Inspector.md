<!-- ========================= -->
<!-- PREMIUM PORTFOLIO README -->
<!-- ========================= -->

<h1 align="center">AWS Vulnerability Assessment with Amazon Inspector</h1>

<p align="center">
Automated Security Scanning and Remediation for Serverless Workloads
</p>

<hr>

<h2>Project Overview</h2>
<p>
Implemented an automated vulnerability management workflow using Amazon Inspector to identify and remediate security risks in AWS Lambda functions. The project simulated a real-world scenario where secure software development practices were required during active application development.
</p>

<p>
The solution focused on continuous scanning, vulnerability analysis, and rapid remediation to ensure secure deployment of serverless applications.
</p>

<hr>

<h2>Architecture Components</h2>

<ul>
<li>Amazon Inspector</li>
<li>AWS Lambda Functions</li>
<li>Vulnerability Database Integration (CVE/NVD)</li>
<li>Automated Scanning Pipeline</li>
</ul>

<hr>

<h2>Implementation Steps</h2>

<h3>1. Amazon Inspector Activation</h3>
<p>
Activated Amazon Inspector to enable continuous vulnerability scanning across supported AWS resources.
</p>


<p>
Scanning was automatically enabled for Lambda functions, EC2 instances, and container repositories.
</p>

<img width="470" height="175" alt="image" src="https://github.com/user-attachments/assets/82079380-cd1c-4f65-9acc-0e3d30a1d96c" />

<hr>

<h3>2. Scan Monitoring and Coverage Validation</h3>
<p>
Monitored the Inspector dashboard to ensure full resource coverage and successful scan initiation.
</p>

<pre><code>Target Resource: AWS Lambda
Coverage Status: 100%</code></pre>

<img width="470" height="200" alt="image" src="https://github.com/user-attachments/assets/5e268117-e30a-4971-a57e-6396d06cd774" />


<hr>

<h3>3. Vulnerability Analysis</h3>
<p>
Reviewed identified vulnerabilities within Lambda functions and analyzed their severity and impact.
</p>

<pre><code>Example Finding:
CVE-2023-32681
Severity: Medium
Affected Component: Python requests library</code></pre>

<p>
Detailed vulnerability information was validated against external security databases.
</p>

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/436bd360-1c75-43b5-8e50-00ea2a585a45" />


<hr>

<h3>4. Root Cause Identification</h3>
<p>
Identified outdated third-party dependencies as the primary cause of vulnerabilities within the Lambda environment.
</p>

<p>
The affected package version introduced known security risks requiring immediate remediation.
</p>

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/0269ddc0-4b28-46f0-97b4-da89e5e9f756" />

<img width="470" height="232" alt="image" src="https://github.com/user-attachments/assets/d167d3b2-0986-4914-a1cf-8d831621f23c" />

<hr>

<h3>5. Remediation Implementation</h3>
<p>
Updated the Lambda function dependency configuration to remove fixed package versions and allow automatic installation of the latest secure release.
</p>

<pre><code># Before
requests==2.20.0

# After
requests</code></pre>

<p>
Deployed updated Lambda function to trigger a new security scan.
</p>

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/d3d0f645-13ad-4ac3-ac69-1efc6b6c4411" />
<img width="470" height="194" alt="image" src="https://github.com/user-attachments/assets/479342e3-4020-42d4-b020-3ef2f16427c0" />

<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/4fae332c-66cd-4f2b-8c02-1365f09a121d" />

<img width="470" height="170" alt="image" src="https://github.com/user-attachments/assets/182513b6-9c73-4b6a-b506-04df0a0a078b" />

<hr>

<h3>6. Validation and Re-Scan</h3>
<p>
Verified remediation success by reviewing updated Amazon Inspector findings.
</p>

<p>
The vulnerability status transitioned from active to closed after re-scanning.
</p>

<img width="470" height="204" alt="image" src="https://github.com/user-attachments/assets/d1515196-33ee-4526-b099-ec0c1de07c0e" />

<img width="470" height="210" alt="image" src="https://github.com/user-attachments/assets/c6582d5d-c63e-41cb-9901-f0a1ba93d57c" />

<img width="470" height="215" alt="image" src="https://github.com/user-attachments/assets/8a2ebeee-d650-4134-8a1e-e0609e05d371" />

<hr>

<h2>Key Outcomes</h2>

<ul>
<li>Enabled automated vulnerability scanning across serverless workloads</li>
<li>Identified and analyzed real CVE-based security issues</li>
<li>Successfully remediated vulnerable dependencies in Lambda functions</li>
<li>Validated security improvements through re-scanning</li>
<li>Established continuous security monitoring workflow</li>
</ul>

<hr>

<h2>Technical Highlights</h2>

<ul>
<li>Serverless security assessment using Amazon Inspector</li>
<li>CVE-based vulnerability analysis</li>
<li>Dependency management and remediation strategy</li>
<li>Automated re-scan validation process</li>
<li>Integration with external vulnerability intelligence sources</li>
</ul>

<hr>

<h2>Conclusion</h2>

<p>
Delivered a practical implementation of cloud-native security using Amazon Inspector. Demonstrated the ability to detect, analyze, and remediate vulnerabilities in serverless environments, aligning with modern DevSecOps and secure software development practices.
</p>
