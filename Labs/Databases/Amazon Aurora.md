<h1>Deploying Amazon Aurora with EC2 Integration</h1>
<p>Cloud database implementation demonstrating secure architecture, connectivity, and SQL operations.</p>

<div class="tags">
<span class="tag">AWS</span>
<span class="tag">Aurora</span>
<span class="tag">EC2</span>
<span class="tag">SQL</span>
<span class="tag">VPC</span>
</div>

<!-- Overview -->
<div class="card">
<h2>Overview</h2>
<p>
A scalable relational database solution was implemented using Amazon Aurora and connected to an EC2 instance.
The project focused on secure configuration, connectivity, and data operations in a cloud environment.
</p>
</div>

<!-- Architecture -->
<div class="card">
<h2>Architecture</h2>
<p>
Aurora was deployed in private subnets, while EC2 acted as a client within the same VPC. Security groups ensured controlled access between components.
</p>


<!-- Implementation -->
<div class="card">
<h2>Implementation</h2>

<h3>1. Aurora Database Deployment</h3>
<p>
Configured and launched an Aurora MySQL-compatible cluster with defined credentials and networking setup.
</p>

<div class="grid">
<img width="940" height="374" alt="image" src="https://github.com/user-attachments/assets/ccd6e6d9-1b31-4701-85ea-57c51296b2cc" />

<img width="940" height="416" alt="image" src="https://github.com/user-attachments/assets/2e719329-94c1-4bd0-8bb9-7aca0fe4850b" />



<h3>2. EC2 Connection</h3>
<p>
Accessed the EC2 instance using Session Manager to avoid SSH key management.
</p>

<div class="grid">
<img width="940" height="379" alt="image" src="https://github.com/user-attachments/assets/851f86b2-8e87-42c3-b7de-553196640d97" />

<img src="your-image-5">
</div>

<h3>3. Database Configuration</h3>
<p>
Installed MariaDB client and connected to Aurora using the cluster endpoint.
</p>

<div class="code">
sudo yum install mariadb -y<br>
mysql -u admin --password='***' -h &lt;endpoint&gt;
</div>

<div class="grid">
<img width="940" height="461" alt="image" src="https://github.com/user-attachments/assets/d49c605b-32c7-4b73-9e7c-de15d6baf7c4" />
  <img width="940" height="325" alt="image" src="https://github.com/user-attachments/assets/5b5de899-a2ea-4045-aa54-481ad20fc6c4" />

<img width="940" height="399" alt="image" src="https://github.com/user-attachments/assets/3832b58b-d975-45c5-bc84-9600655fbc24" />
</div>

<h3>4. Database Operations</h3>
<p>
Created a table, inserted records, and executed queries to validate the database functionality.
</p>

<div class="code">
SHOW DATABASES;<br>
USE world;<br>
SELECT * FROM country WHERE GNP > 35000;
</div>
<img width="940" height="492" alt="image" src="https://github.com/user-attachments/assets/f8b07eef-41d2-4f8b-8d01-767627a2843f" />

<img width="377" height="297" alt="image" src="https://github.com/user-attachments/assets/63ed2d25-4e06-42d2-b4c6-075154370058" />

<img width="940" height="506" alt="image" src="https://github.com/user-attachments/assets/07937bed-8118-4ed9-b8d6-0e48454961d9" />
<img width="940" height="478" alt="image" src="https://github.com/user-attachments/assets/39cc68f8-e6bf-46fe-8bb7-b8ca6a27a3c9" />
<img width="940" height="287" alt="image" src="https://github.com/user-attachments/assets/bffcbfb8-5df4-4269-9e98-61161820a78f" />

<div class="grid">


</div>

</div>

<!-- Result -->
<div class="card">
<h2>Result</h2>
<ul>
<li>Deployed a fully functional Aurora database</li>
<li>Established secure EC2-to-database connection</li>
<li>Validated SQL operations successfully</li>
</ul>
</div>

<!-- Learnings -->
<div class="card">
<h2>Key Learnings</h2>
<ul>
<li>Understanding Aurora cluster endpoints</li>
<li>Secure database access within VPC</li>
<li>Practical SQL execution in cloud environments</li>
<li>Advantages of managed database services</li>
</ul>
</div>

</div>

</body>
</html>
