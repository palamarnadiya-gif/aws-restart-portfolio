<h1>World Database – Using Functions in SQL</h1>
<p>Exploring SQL functions with SELECT and WHERE clauses on a relational database containing country, city, and countrylanguage tables.</p>

<div class="tags">
<span class="tag">AWS</span>
<span class="tag">MySQL</span>
<span class="tag">EC2</span>
<span class="tag">SQL Functions</span>
<span class="tag">Database Operations</span>
</div>

<!-- Overview -->
<div class="card">
<h2>Overview</h2>
<p>
This project demonstrates querying the world database using common SQL functions including aggregates, string manipulation, and distinct value retrieval. The lab focused on extracting, transforming, and analyzing data efficiently.
</p>
</div>

<!-- Architecture -->
<div class="card">
<h2>Architecture</h2>
<p>
The lab environment consists of a Command Host EC2 instance with MySQL client installed. The world database contains three tables: <b>country</b>, <b>city</b>, and <b>countrylanguage</b>. Queries were executed from the Command Host using Session Manager.
</p>

<div class="grid">
<img src="screenshots/command_host.png" alt="Command Host Terminal">
<img src="screenshots/world_db_tables.png" alt="World Database Tables">
</div>
</div>

<!-- Implementation -->
<div class="card">
<h2>Implementation</h2>

<h3>1. Connecting to the Command Host</h3>
<p>Connected to the EC2 Command Host using AWS Session Manager and launched the MySQL client.</p>

<div class="code">
sudo su<br>
cd /home/ec2-user/<br>
mysql -u root --password='re:St@rt!9'
</div>

<div class="grid">
<img src="screenshots/session_manager.png" alt="Session Manager Connection">
<img src="screenshots/mysql_login.png" alt="MySQL Login">
</div>

<h3>2. Viewing Database and Table Schema</h3>
<p>Checked available databases and reviewed the structure of the country table.</p>

<div class="code">
SHOW DATABASES;<br>
USE world;<br>
SELECT * FROM country;
</div>

<div class="grid">
<img src="screenshots/show_databases.png" alt="Show Databases">
<img src="screenshots/country_table.png" alt="Country Table Schema">
</div>

<h3>3. Using Aggregate Functions</h3>
<p>Summarized country population data using SUM(), AVG(), MAX(), MIN(), and COUNT().</p>

<div class="code">
SELECT SUM(Population), AVG(Population), MAX(Population), MIN(Population), COUNT(Population) FROM country;
</div>

<div class="grid">
<img src="screenshots/aggregate_functions.png" alt="Aggregate Functions Output">
</div>

<h3>4. Splitting Strings with SUBSTRING_INDEX()</h3>
<p>Used SUBSTRING_INDEX() to split region names and filter countries based on the first word.</p>

<div class="code">
SELECT Region, SUBSTRING_INDEX(Region, " ", 1) FROM country;<br>
SELECT Name, Region FROM country WHERE SUBSTRING_INDEX(Region, " ", 1) = "Southern";
</div>

<div class="grid">
<img src="screenshots/substring_index.png" alt="Substring Index Example">
</div>

<h3>5. Using LENGTH() and TRIM()</h3>
<p>Calculated string lengths after trimming spaces and filtered short region names.</p>

<div class="code">
SELECT Region FROM country WHERE LENGTH(TRIM(Region)) &lt; 10;<br>
SELECT DISTINCT(Region) FROM country WHERE LENGTH(TRIM(Region)) &lt; 10;
</div>

<div class="grid">
<img src="screenshots/length_trim.png" alt="Length and Trim Functions">
</div>

<h3>6. Challenge: Splitting Multi-Part Regions</h3>
<p>Split the region "Micronesia/Caribbean" into two separate columns.</p>

<div class="code">
SELECT Name, 
       SUBSTRING_INDEX(Region, "/", 1) AS "Region Name 1", 
       SUBSTRING_INDEX(Region, "/", -1) AS "Region Name 2" 
FROM country 
WHERE Region = "Micronesia/Caribbean";
</div>

<div class="grid">
<img src="screenshots/micronesia_caribbean.png" alt="Split Multi-Part Region">
</div>

</div>

<!-- Result -->
<div class="card">
<h2>Result</h2>
<ul>
<li>Connected to world database and explored table schemas</li>
<li>Applied aggregate functions for population analysis</li>
<li>Used string manipulation functions to process and filter region data</li>
<li>Removed duplicates with DISTINCT() and identified unique regions</li>
<li>Successfully split multi-part regions into separate columns</li>
</ul>
</div>

<!-- Key Learnings -->
<div class="card">
<h2>Key Learnings</h2>
<ul>
<li>Applying SQL aggregate functions: SUM(), AVG(), MAX(), MIN(), COUNT()</li>
<li>String manipulation using SUBSTRING_INDEX(), LENGTH(), and TRIM()</li>
<li>Filtering unique records with DISTINCT()</li>
<li>Using functions in both SELECT and WHERE clauses</li>
<li>Querying and analyzing relational data from multiple perspectives</li>
</ul>
</div>

</div>
</body>
</html>
