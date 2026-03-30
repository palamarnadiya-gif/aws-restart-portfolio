<h1>AWS Database Services – RDS Migration</h1>
<p>Migration of a café web application database to Amazon RDS MariaDB, including data migration, infrastructure setup, and monitoring.</p>

<div class="tags">
<span class="tag">AWS</span>
<span class="tag">Amazon RDS</span>
<span class="tag">MariaDB</span>
<span class="tag">EC2</span>
<span class="tag">CloudWatch</span>
<span class="tag">CLI</span>
<span class="tag">VPC</span>
</div>

<!-- Overview -->
<div class="card">
<h2>Overview</h2>
<p>
This project demonstrates migrating a local café database to Amazon RDS MariaDB, configuring VPC subnets and security, migrating data using mysqldump, reconfiguring the application, and monitoring with CloudWatch.
</p>
</div>

<!-- Architecture -->
<div class="card">
<h2>Architecture</h2>
<p>
<b>Starting Architecture:</b> Local database hosted on EC2 instance (LAMP stack) within a public subnet.<br>
<b>Final Architecture:</b> RDS MariaDB instance in private subnets within the same VPC, accessed by café application. Security group restricts access to the application instance only.
</p>

<div class="grid">
<img width="940" height="452" alt="image" src="https://github.com/user-attachments/assets/6dfe7971-1044-4cde-8095-182bab0d310f" />
</div>
</div>

<!-- Implementation -->
<div class="card">
<h2>Implementation</h2>

<h3>1. Generating Order Data</h3>
<p>
Browsed the café website and placed sample orders to generate data for migration.
</p>

<div class="grid">
<img width="940" height="411" alt="image" src="https://github.com/user-attachments/assets/9e260a16-df53-4fbf-ad4d-f19d464e2d04" />
</div>

<h3>2. Connecting to CLI Host and Configuring AWS CLI</h3>
<p>
Connected to CLI Host EC2 instance via EC2 Instance Connect and configured AWS CLI with access keys and default region.
</p>

<div class="code">
aws configure<br>
# Enter AccessKey, SecretKey, LabRegion, json output format
</div>

<div class="grid">
<img width="940" height="386" alt="image" src="https://github.com/user-attachments/assets/77dd3dcb-cee3-40ab-8706-d3ec0a2aa779" />

</div>

<h3>3. Creating Prerequisite Components</h3>
<p>
Created security group, two private subnets, and a DB subnet group for the RDS instance.
</p>

<div class="code">
aws ec2 create-security-group --group-name CafeDatabaseSG --description "Security group for Cafe database" --vpc-id &lt;VPC ID&gt;<br>
aws ec2 authorize-security-group-ingress --group-id &lt;CafeDatabaseSG Group ID&gt; --protocol tcp --port 3306 --source-group &lt;CafeSecurityGroup ID&gt;<br>
aws ec2 create-subnet --vpc-id &lt;VPC ID&gt; --cidr-block 10.200.2.0/23 --availability-zone &lt;AZ1&gt;<br>
aws ec2 create-subnet --vpc-id &lt;VPC ID&gt; --cidr-block 10.200.10.0/23 --availability-zone &lt;AZ2&gt;<br>
aws rds create-db-subnet-group --db-subnet-group-name "CafeDB Subnet Group" --db-subnet-group-description "DB subnet group for Cafe" --subnet-ids &lt;Subnet1 ID&gt; &lt;Subnet2 ID&gt; --tags "Key=Name,Value=CafeDatabaseSubnetGroup"
</div>

<div class="grid">
<img width="940" height="435" alt="image" src="https://github.com/user-attachments/assets/c4a207cc-3a77-4442-a07e-fc2f09935f47" />
<img width="940" height="444" alt="image" src="https://github.com/user-attachments/assets/c1efa573-ba70-4aa7-9052-ca34114fd1cf" />
<img width="940" height="434" alt="image" src="https://github.com/user-attachments/assets/46b8757e-2e34-416a-8b6e-521363390e3e" />

<img width="940" height="404" alt="image" src="https://github.com/user-attachments/assets/c9eeb045-77e4-4dec-9524-12ee96b2f7b7" />

<img width="940" height="474" alt="image" src="https://github.com/user-attachments/assets/862a868f-d485-4cc7-b175-435764de77ed" />

</div>

<h3>4. Creating Amazon RDS MariaDB Instance</h3>
<p>
Created the RDS instance with db.t3.micro, 20 GB storage, MariaDB engine 10.5.13, private access, and associated security group.
</p>

<div class="code">
aws rds create-db-instance --db-instance-identifier CafeDBInstance --engine mariadb --engine-version 10.5.13 --db-instance-class db.t3.micro --allocated-storage 20 --availability-zone &lt;AZ1&gt; --db-subnet-group-name "CafeDB Subnet Group" --vpc-security-group-ids &lt;CafeDatabaseSG ID&gt; --no-publicly-accessible --master-username root --master-user-password 'Re:Start!9'
</div>

<div class="grid">
<img width="940" height="426" alt="image" src="https://github.com/user-attachments/assets/011aa3c5-d162-4e92-ad4f-f907147706f9" />

<img width="940" height="426" alt="image" src="https://github.com/user-attachments/assets/65316a73-7b4b-45fb-afe1-743a7f4ae495" />
<img width="940" height="190" alt="image" src="https://github.com/user-attachments/assets/72cb34c4-9547-4d1b-ba82-d12f1ffb0bb2" />
<img width="940" height="349" alt="image" src="https://github.com/user-attachments/assets/604f2865-3ec0-4fa9-a591-3533dd84e590" />
<img width="940" height="178" alt="image" src="https://github.com/user-attachments/assets/272ee8a0-cffb-41b4-9245-afe1b807870c" />

</div>

<h3>5. Migrating Application Data</h3>
<p>
Used <strong>mysqldump</strong> to export the local database and restored it to the Amazon RDS instance. Verified data integrity.
</p>

<div class="code">
mysqldump --user=root --password='Re:Start!9' --databases cafe_db --add-drop-database &gt; cafedb-backup.sql<br>
mysql --user=root --password='Re:Start!9' --host=&lt;RDS Endpoint&gt; &lt; cafedb-backup.sql<br>
mysql --user=root --password='Re:Start!9' --host=&lt;RDS Endpoint&gt; cafe_db<br>
select * from product;
</div>

<div class="grid">
<img width="940" height="391" alt="image" src="https://github.com/user-attachments/assets/4d24d830-9504-4356-9be4-4bed0ec64974" />
<img width="940" height="395" alt="image" src="https://github.com/user-attachments/assets/985fcb5a-0425-4022-b950-ae0c85fe7ada" />
<img width="940" height="390" alt="image" src="https://github.com/user-attachments/assets/593285a1-e121-4669-a0ac-01b19b367613" />

<img src="screenshots/rds_data.png">
</div>

<h3>6. Reconfiguring Café Website</h3>
<p>
Updated the database connection in AWS Systems Manager Parameter Store to point to the RDS endpoint and tested website functionality.
</p>

<div class="grid">
<img width="940" height="426" alt="image" src="https://github.com/user-attachments/assets/cf930867-8399-4b42-a4ae-7abfcdaf82d4" />

<img width="940" height="403" alt="image" src="https://github.com/user-attachments/assets/dfee6d32-dbe3-4749-a19e-bef6467462fc" />
<img width="940" height="422" alt="image" src="https://github.com/user-attachments/assets/2b845ab9-500f-40e0-ab17-6b47a322d539" />

</div>

<h3>7. Monitoring Amazon RDS</h3>
<p>
Monitored RDS performance metrics using Amazon CloudWatch including CPU utilization, DatabaseConnections, and storage.
</p>

<div class="grid">
<img width="940" height="422" alt="image" src="https://github.com/user-attachments/assets/65cb4434-c696-4b6c-bee6-20877d4cd978" />

<img width="940" height="415" alt="image" src="https://github.com/user-attachments/assets/70097233-ed56-493e-a377-8055d0978d12" />
<img width="940" height="242" alt="image" src="https://github.com/user-attachments/assets/a5878ca3-dcb6-4c31-961d-de15e8dd7b7d" />
<img width="940" height="311" alt="image" src="https://github.com/user-attachments/assets/f9405dd3-305f-449d-a6f7-c0b9eb916f2e" />

</div>

</div>

<!-- Result -->
<div class="card">
<h2>Result</h2>
<ul>
<li>Created Amazon RDS MariaDB instance with private subnets and security group</li>
<li>Successfully migrated local database to RDS</li>
<li>Reconfigured café application to use the new database</li>
<li>Monitored database performance using CloudWatch</li>
</ul>
</div>

<!-- Key Learnings -->
<div class="card">
<h2>Key Learnings</h2>
<ul>
<li>Configuring AWS CLI for secure cloud operations</li>
<li>Deploying Amazon RDS instances in private subnets</li>
<li>Managing security groups for database access control</li>
<li>Using mysqldump to migrate data between databases</li>
<li>Monitoring RDS metrics with CloudWatch</li>
<li>Applying best practices for application database configuration</li>
</ul>
</div>

</div>
</body>
</html>
