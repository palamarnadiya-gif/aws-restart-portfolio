<h1>Amazon DynamoDB Music Library</h1>
<p>Demonstrated DynamoDB table creation, data operations, querying, and deletion in a fully managed NoSQL environment.</p>

<div class="tags">
<span class="tag">AWS</span>
<span class="tag">DynamoDB</span>
<span class="tag">NoSQL</span>
<span class="tag">Data Modeling</span>
<span class="tag">Querying</span>
</div>

<!-- Overview -->
<div class="card">
<h2>Overview</h2>
<p>
This project implemented a DynamoDB table to manage a music library, showcasing NoSQL capabilities for schema-less design, flexible attributes, and fast queries.
</p>
</div>

<!-- Implementation -->
<div class="card">
<h2>Implementation</h2>

<h3>1. Create a New Table</h3>
<p>
A table named <strong>Music</strong> was created with a partition key <strong>Artist</strong> and an optional sort key <strong>Song</strong>. Default settings were used for indexes and capacity.
</p>

<div class="grid">
<img width="940" height="1149" alt="image" src="https://github.com/user-attachments/assets/b63824c9-c51e-4daa-bb3c-9612a7c30c35" />

<img width="940" height="325" alt="image" src="https://github.com/user-attachments/assets/420694fb-83c0-428d-ad0d-2b5335cb4c26" />

</div>

<h3>2. Add Data</h3>
<p>
Three items were added with varying attributes to demonstrate the flexibility of DynamoDB:
<ul>
<li>Pink Floyd – Money (Album: The Dark Side of the Moon, Year: 1973)</li>
<li>John Lennon – Imagine (Album: Imagine, Year: 1971, Genre: Soft rock)</li>
<li>Psy – Gangnam Style (Album: Psy 6 (Six Rules), Part 1, Year: 2011, LengthSeconds: 219)</li>
</ul>
</p>

<div class="grid">
<img width="940" height="376" alt="image" src="https://github.com/user-attachments/assets/daf548e9-b19c-4d49-b201-581c46130a56" />

<img width="940" height="745" alt="image" src="https://github.com/user-attachments/assets/042289f0-aab5-4ba7-bcca-032f4c65c51f" />

</div>

<h3>3. Modify an Existing Item</h3>
<p>
The Year attribute of <strong>Psy – Gangnam Style</strong> was updated from 2011 to 2012 using the console.
</p>

<h3>4. Query the Table</h3>
<p>
Two methods were applied:
<ul>
<li><strong>Query</strong> by primary key: Artist = Psy, Song = Gangnam Style</li>
<li><strong>Scan</strong> with filter: Year = 1971</li>
</ul>
</p>

<h3>5. Delete the Table</h3>
<p>
The <strong>Music</strong> table was deleted, permanently removing all items. This confirmed proper table lifecycle management.
</p>

<div class="grid">
<img width="940" height="425" alt="image" src="https://github.com/user-attachments/assets/c333bccb-1aa2-4d20-97fe-1f61585aab14" />

<img width="470" height="298" alt="image" src="https://github.com/user-attachments/assets/6a297a05-4f70-442d-b839-ec8fffedeccf" />
<img width="940" height="313" alt="image" src="https://github.com/user-attachments/assets/2cca8a3f-edaf-4879-83f1-e8dd4e81ac15" />

</div>

</div>

<!-- Result -->
<div class="card">
<h2>Result</h2>
<ul>
<li>Created a DynamoDB table with flexible schema</li>
<li>Inserted and modified items with varied attributes</li>
<li>Executed efficient queries using primary key and scan filters</li>
<li>Deleted table to finalize lab operations</li>
</ul>
</div>

<!-- Learnings -->
<div class="card">
<h2>Key Learnings</h2>
<ul>
<li>Understanding partition and sort keys in DynamoDB</li>
<li>Schema-less data modeling for flexible attributes</li>
<li>Efficient querying using query and scan operations</li>
<li>Full lifecycle management of NoSQL tables in AWS</li>
</ul>
</div>

</div>

</body>
</html>
