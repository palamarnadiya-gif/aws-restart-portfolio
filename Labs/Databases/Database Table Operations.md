<h1>Database Table Operations Lab</h1>
<p>Hands-on SQL practice creating, modifying, and deleting databases and tables in a relational cloud environment.</p>

<div class="tags">
<span class="tag">AWS</span>
<span class="tag">MySQL</span>
<span class="tag">SQL</span>
<span class="tag">Database Administration</span>
<span class="tag">EC2</span>
</div>

<!-- Overview -->
<div class="card">
<h2>Overview</h2>
<p>
This project demonstrated common database operations, including creating databases and tables, modifying table structure, querying table metadata, and deleting tables and databases.
</p>
</div>
<img width="470" height="304" alt="image" src="https://github.com/user-attachments/assets/652faff8-b4e3-4bc2-b35d-7c5dcacaa543" />


<!-- Implementation -->
<div class="card">
<h2>Implementation</h2>

<h3>1. Connect to the Command Host</h3>
<p>
Connected to an EC2 instance with a database client using Session Manager. Configured the terminal to access required tools and connected to the relational database using MySQL CLI.
</p>

<div class="code">
sudo su<br>
cd /home/ec2-user/<br>
mysql -u root --password='re:St@rt!9'
</div>

<h3>2. Create a Database and Table</h3>
<p>
Displayed existing databases and created a new database <strong>world</strong>. Created a table <strong>country</strong> with detailed schema, including data types and primary key.
</p>

<div class="code">
SHOW DATABASES;<br>
CREATE DATABASE world;<br>
SHOW DATABASES;<br>
USE world;<br>
CREATE TABLE country (<br>
&nbsp;&nbsp;`Code` CHAR(3) NOT NULL DEFAULT '',<br>
&nbsp;&nbsp;`Name` CHAR(52) NOT NULL DEFAULT '',<br>
&nbsp;&nbsp;`Conitinent` ENUM('Asia','Europe','North America','Africa','Oceania','Antarctica','South  America') NOT NULL DEFAULT 'Asia',<br>
&nbsp;&nbsp;`Region` CHAR(26) NOT NULL DEFAULT '',<br>
&nbsp;&nbsp;`SurfaceArea` FLOAT(10,2) NOT NULL DEFAULT '0.00',<br>
&nbsp;&nbsp;`IndepYear` SMALLINT(6) DEFAULT NULL,<br>
&nbsp;&nbsp;`Population` INT(11) NOT NULL DEFAULT '0',<br>
&nbsp;&nbsp;`LifeExpectancy` FLOAT(3,1) DEFAULT NULL,<br>
&nbsp;&nbsp;`GNP` FLOAT(10,2) DEFAULT NULL,<br>
&nbsp;&nbsp;`GNPOld` FLOAT(10,2) DEFAULT NULL,<br>
&nbsp;&nbsp;`LocalName` CHAR(45) NOT NULL DEFAULT '',<br>
&nbsp;&nbsp;`GovernmentForm` CHAR(45) NOT NULL DEFAULT '',<br>
&nbsp;&nbsp;`HeadOfState` CHAR(60) DEFAULT NULL,<br>
&nbsp;&nbsp;`Capital` INT(11) DEFAULT NULL,<br>
&nbsp;&nbsp;`Code2` CHAR(2) NOT NULL DEFAULT '',<br>
&nbsp;&nbsp;PRIMARY KEY (`Code`)<br>
);
</div>

<h3>3. Verify Tables and Columns</h3>
<p>
Verified the country table creation using <strong>SHOW TABLES;</strong> and listed all columns with <strong>SHOW COLUMNS;</strong>. Identified a misspelled column.
</p>

<div class="code">
USE world;<br>
SHOW TABLES;<br>
SHOW COLUMNS FROM country;
</div>

<h3>4. Alter Table Schema</h3>
<p>
Corrected the column name <strong>Conitinent</strong> to <strong>Continent</strong> using the ALTER TABLE command.
</p>

<div class="code">
ALTER TABLE country RENAME COLUMN Conitinent TO Continent;<br>
SHOW COLUMNS FROM country;
</div>
<img width="907" height="1454" alt="image" src="https://github.com/user-attachments/assets/9d0efee1-758a-4ec4-bdde-36a535bf9499" />


<!-- Result -->
<div class="card">
<h2>Result</h2>
<ul>
<li>Successfully connected to the database via EC2 Session Manager</li>
<li>Created and verified a new database and table</li>
<li>Listed and corrected table columns</li>
<li>Demonstrated proper use of SQL statements: CREATE, SHOW, ALTER</li>
</ul>
</div>

<!-- Key Learnings -->
<div class="card">
<h2>Key Learnings</h2>
<ul>
<li>Connecting to a relational database through an EC2 client</li>
<li>Executing SQL commands to manage database objects</li>
<li>Verifying table structures and metadata efficiently</li>
<li>Applying ALTER statements to modify table schema</li>
<li>Structured workflow for database lifecycle management</li>
</ul>
</div>

</div>

</body>
</html>
