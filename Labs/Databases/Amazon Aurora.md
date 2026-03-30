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

<div class="grid">
<img src="your-architecture-1">
<img src="your-architecture-2">
</div>
</div>

<!-- Implementation -->
<div class="card">
<h2>Implementation</h2>

<h3>1. Aurora Database Deployment</h3>
<p>
Configured and launched an Aurora MySQL-compatible cluster with defined credentials and networking setup.
</p>

<div class="grid">
<img src="your-image-1">
<img src="your-image-2">
<img src="your-image-3">
</div>

<h3>2. EC2 Connection</h3>
<p>
Accessed the EC2 instance using Session Manager to avoid SSH key management.
</p>

<div class="grid">
<img src="your-image-4">
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
<img src="your-image-6">
<img src="your-image-7">
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

<div class="grid">
<img src="your-image-8">
<img src="your-image-9">
<img src="your-image-10">
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
