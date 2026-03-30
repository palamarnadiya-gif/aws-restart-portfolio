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
<img width="470" height="297" alt="image" src="https://github.com/user-attachments/assets/02d8dc1f-dff9-4f48-b55a-550e9d2fac63" />

<img width="470" height="284" alt="image" src="https://github.com/user-attachments/assets/7d7f6bee-f302-4078-8191-5b4c57f88ece" />

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
<img width="940" height="467" alt="image" src="https://github.com/user-attachments/assets/8912d80c-b6d5-43fc-bd2a-750d51c772c7" />

<img width="940" height="273" alt="image" src="https://github.com/user-attachments/assets/c6abb4c6-a2fc-40e9-87d5-4093441623fd" />



</div>

<h3>2. Viewing Database and Table Schema</h3>
<p>Checked available databases and reviewed the structure of the country table.</p>

<div class="code">
SHOW DATABASES;<br>
USE world;<br>
SELECT * FROM country;
</div>
<img width="940" height="428" alt="image" src="https://github.com/user-attachments/assets/2cf70cb8-1479-473f-9bde-c06dbe0ed41c" />
<div class="grid">
<img width="940" height="363" alt="image" src="https://github.com/user-attachments/assets/ea36a082-026f-4303-ad7e-21243e7a953a" />

<img width="940" height="434" alt="image" src="https://github.com/user-attachments/assets/aa2e6696-67b0-4510-b318-b9504e93c661" />

</div>

<h3>3. Using Aggregate Functions</h3>
<p>Summarized country population data using SUM(), AVG(), MAX(), MIN(), and COUNT().</p>

<div class="code">
SELECT SUM(Population), AVG(Population), MAX(Population), MIN(Population), COUNT(Population) FROM country;
</div>
<img width="940" height="434" alt="image" src="https://github.com/user-attachments/assets/ca8c1209-5ce3-44e7-b4d9-b4b4195c42c2" />

<div class="grid">



<h3>4. Splitting Strings with SUBSTRING_INDEX()</h3>
<p>Used SUBSTRING_INDEX() to split region names and filter countries based on the first word.</p>

<div class="code">
SELECT Region, SUBSTRING_INDEX(Region, " ", 1) FROM country;<br>
SELECT Name, Region FROM country WHERE SUBSTRING_INDEX(Region, " ", 1) = "Southern";
</div>

<div class="grid">
<img width="940" height="419" alt="image" src="https://github.com/user-attachments/assets/efae7e45-a7c9-466d-a139-c603adbc5dea" />

</div>

<h3>5. Using LENGTH() and TRIM()</h3>
<p>Calculated string lengths after trimming spaces and filtered short region names.</p>

<div class="code">
SELECT Region FROM country WHERE LENGTH(TRIM(Region)) &lt; 10;<br>
SELECT DISTINCT(Region) FROM country WHERE LENGTH(TRIM(Region)) &lt; 10;
</div>

<div class="grid">
<img width="940" height="671" alt="image" src="https://github.com/user-attachments/assets/68f48ce9-32ab-470f-ba5c-cf4ae4173e40" />
<img width="940" height="204" alt="image" src="https://github.com/user-attachments/assets/dce44fae-a47f-4635-9956-a552950b4acb" />


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
<img width="940" height="241" alt="image" src="https://github.com/user-attachments/assets/dddbf88a-3fa3-4798-a386-4589e8069b6e" />

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
