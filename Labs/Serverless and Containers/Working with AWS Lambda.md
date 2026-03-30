<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
 
<body>

<h1>Serverless Sales Analysis Pipeline (AWS)</h1>

<h2>Overview</h2>
<p>
Implemented a serverless reporting solution using AWS services. The system generates daily sales reports by extracting data from a database and sending the results via email.
</p>
<img width="940" height="565" alt="image" src="https://github.com/user-attachments/assets/9379ee83-6254-45ba-bb6f-d5112dbfbd1e" />


<h2>Architecture</h2>
<ul>
  <li>Scheduled trigger via Amazon EventBridge (CloudWatch Events)</li>
  <li>Processing with AWS Lambda</li>
  <li>Database hosted on a LAMP stack</li>
  <li>Configuration stored in AWS Systems Manager Parameter Store</li>
  <li>Notifications via Amazon SNS</li>
  <li>Monitoring with Amazon CloudWatch</li>
</ul>

<h2>Implementation Steps</h2>

<h2>Task 1: Observing IAM Role Settings</h2>
<ul>
  <li><strong>salesAnalysisReportRole</strong>
    <ul>
      <li>Trusted entity: lambda.amazonaws.com</li>
      <li>Policies: AmazonSNSFullAccess, AmazonSSMReadOnlyAccess, AWSLambdaBasicRunRole, AWSLambdaRole</li>
    </ul>
  </li>
  <li><strong>salesAnalysisReportDERole</strong>
    <ul>
      <li>Trusted entity: lambda.amazonaws.com</li>
      <li>Policies: AWSLambdaBasicRunRole, AWSLambdaVPCAccessRunRole</li>
    </ul>
  </li>
</ul>
<p>Ensured proper permissions for accessing SNS, Parameter Store, CloudWatch, and VPC.</p>

<img width="940" height="433" alt="image" src="https://github.com/user-attachments/assets/fe78f96f-218f-4c60-9997-96fb8bd5ad0e" />

<img width="940" height="395" alt="image" src="https://github.com/user-attachments/assets/f445adeb-992f-40d7-bf5d-dbc7f6fdb87f" />
<img width="940" height="405" alt="image" src="https://github.com/user-attachments/assets/cbc946b4-9bd7-44d5-a61e-9e2e77fc7b75" />
<img width="940" height="421" alt="image" src="https://github.com/user-attachments/assets/d8b1b905-6773-4e9b-8f99-c704b909676b" />
<img width="940" height="402" alt="image" src="https://github.com/user-attachments/assets/e9437922-88f8-47f0-9c61-d054dcf31148" />
<img width="940" height="427" alt="image" src="https://github.com/user-attachments/assets/ed9ebee5-5e58-4846-a2d3-c4812a9468a9" />

<img width="940" height="417" alt="image" src="https://github.com/user-attachments/assets/f5782b0b-ea47-4526-9120-18f07a4fa058" />

<h2>Task 2: Creating Lambda Layer and Data Extractor Function</h2>
<h3>Lambda Layer</h3>
<ul>
  <li>Created <strong>pymysqlLibrary</strong> for PyMySQL dependencies</li>
  <li>Compatible with Python 3.9</li>
</ul>

<img width="940" height="435" alt="image" src="https://github.com/user-attachments/assets/ebc59e64-9f11-4b58-9c32-1ad4449849ad" />
<img width="940" height="413" alt="image" src="https://github.com/user-attachments/assets/1e565398-7c76-4b88-aa78-3b514f73d8b4" />
<img width="940" height="421" alt="image" src="https://github.com/user-attachments/assets/e1b2afea-b754-4897-a9a8-488f2cbf7208" />
<img width="940" height="316" alt="image" src="https://github.com/user-attachments/assets/507e2d59-8d64-4f59-8c0f-3dd53fb1749f" />

<h3>Data Extractor Function</h3>
<ul>
  <li>Created <strong>salesAnalysisReportDataExtractor</strong> using salesAnalysisReportDERole</li>
  <li>Added pymysqlLibrary layer</li>
  <li>Uploaded code from <em>salesAnalysisReportDataExtractor-v3.zip</em></li>
</ul>

<img width="940" height="422" alt="image" src="https://github.com/user-attachments/assets/04ce9051-d561-41f8-a090-a2c12fdf3b55" />
<img width="940" height="436" alt="image" src="https://github.com/user-attachments/assets/80244f5f-1e3f-490f-a99d-733215aa7e9d" />
<img width="940" height="390" alt="image" src="https://github.com/user-attachments/assets/b631e3e5-d153-4d3a-bca0-5a5cbe686f3f" />


<h3>3. Function Testing & Debugging</h3>
<p>Tested function execution, identified a timeout issue, and resolved it by updating the security group to allow port 3306.</p>

<img width="940" height="422" alt="image" src="https://github.com/user-attachments/assets/015c4da2-b3ed-4371-a3dd-b3e709b37b5a" />
<img width="940" height="475" alt="image" src="https://github.com/user-attachments/assets/c66d7bd1-1355-4b51-b424-9ab37cae6ebd" />
<img width="940" height="441" alt="image" src="https://github.com/user-attachments/assets/8c51bf65-b4d9-439c-83be-6e1f4d62e01d" />
<img width="940" height="395" alt="image" src="https://github.com/user-attachments/assets/407fcc57-855e-4ef4-8026-fe7d134f5288" />
<img width="940" height="521" alt="image" src="https://github.com/user-attachments/assets/ac6340f4-812c-457c-84c3-cce57e12609b" />
<img width="940" height="355" alt="image" src="https://github.com/user-attachments/assets/565f3bac-203e-475f-a801-ea29be283029" />
<img width="940" height="397" alt="image" src="https://github.com/user-attachments/assets/d21b62c4-09af-4db1-9d06-77d5319a69c0" />

<img width="940" height="420" alt="image" src="https://github.com/user-attachments/assets/69b422db-ff69-438a-965d-9889561a3502" />
<img width="940" height="363" alt="image" src="https://github.com/user-attachments/assets/9c80e991-88bc-4faf-afa2-abaf7b85fde9" />


<h3>Network Configuration</h3>
<ul>
  <li>Configured VPC, subnet, and security group for EC2 database access</li>
</ul>
<img width="940" height="429" alt="image" src="https://github.com/user-attachments/assets/ac79e48a-b250-4bc3-a063-160a398e83d4" />
<img width="940" height="405" alt="image" src="https://github.com/user-attachments/assets/113daa56-8bf2-4209-883e-c6534911b298" />
<img width="940" height="388" alt="image" src="https://github.com/user-attachments/assets/40f91f6b-c352-468b-90df-730568d778e5" />
<img width="940" height="367" alt="image" src="https://github.com/user-attachments/assets/4d84ad8c-acf5-4271-bb03-7bb8ec8ac1d0" />
<img width="940" height="394" alt="image" src="https://github.com/user-attachments/assets/87747132-4a10-4b77-b743-188f3ea7abaf" />


<h2>Task 4: Testing and Troubleshooting the Data Extractor</h2>
<ul>
  <li><strong>Initial Test:</strong> Function timed out due to database connection port (3306) not open</li>
  <li><strong>Fix:</strong> Updated security group inbound rules for database access</li>
  <li><strong>Verified Success:</strong> Returned <code>statusCode: 200</code> with extracted report data</li>
  <li><strong>Data Population:</strong> Placed sample orders on café website to test with real data</li>
</ul>
<img width="940" height="429" alt="image" src="https://github.com/user-attachments/assets/0914592b-8cae-45e3-a480-a2063d3f0b2f" />
<img width="940" height="483" alt="image" src="https://github.com/user-attachments/assets/5954d63b-fe53-4aa1-bffb-2deba68878ce" />
<img width="940" height="408" alt="image" src="https://github.com/user-attachments/assets/91262cc3-e465-49ec-905d-41c89175530f" />
<img width="940" height="372" alt="image" src="https://github.com/user-attachments/assets/fb0a4e1f-7e5d-4f33-84b9-966c8b5929c9" />
<img width="940" height="375" alt="image" src="https://github.com/user-attachments/assets/cca52deb-1052-4071-b30d-e822815eff89" />
<img width="940" height="391" alt="image" src="https://github.com/user-attachments/assets/b8ce5c43-4c96-4caa-bffc-50d0e2da26be" />
<img width="940" height="427" alt="image" src="https://github.com/user-attachments/assets/739318dc-1f7e-4f78-aef6-78c7d650e406" />
<img width="940" height="370" alt="image" src="https://github.com/user-attachments/assets/b3db5eb1-be13-4781-8d30-9ae328ea47b2" />
<img width="940" height="399" alt="image" src="https://github.com/user-attachments/assets/cee1f1e1-be71-48d8-93d6-6201acb5c639" />
<img width="940" height="348" alt="image" src="https://github.com/user-attachments/assets/7d0be32f-9297-4f3f-aa4c-482e275f2f97" />
<img width="813" height="1454" alt="image" src="https://github.com/user-attachments/assets/6a8bfabd-1469-4fc7-a5bc-5a2c54b293f9" />

<img width="940" height="232" alt="image" src="https://github.com/user-attachments/assets/e6497cb6-924e-404d-993a-9cd95918237a" />
<img width="940" height="415" alt="image" src="https://github.com/user-attachments/assets/99733ce1-4aea-464f-8568-2cdecf8e2701" />
<img width="940" height="424" alt="image" src="https://github.com/user-attachments/assets/099c84e9-7386-4b70-ab7b-7ac56fa1bcbe" />
<img width="940" height="375" alt="image" src="https://github.com/user-attachments/assets/9c84d3ca-0562-4d32-8d55-e462c3929d28" />
<img width="940" height="413" alt="image" src="https://github.com/user-attachments/assets/3c25ca93-5247-4c5e-b4cc-bace6557a24c" />
<img width="940" height="233" alt="image" src="https://github.com/user-attachments/assets/1b49f44e-b110-40a6-89ca-ab252f06e1aa" />


<h2>Task 5: Configuring Notifications</h2>
<ul>
  <li>Created SNS topic <strong>salesAnalysisReportTopic</strong> with display name <strong>SARTopic</strong></li>
  <li>Subscribed an email endpoint and confirmed subscription</li>
  <li>Ensured Lambda function can publish messages to SNS topic</li>
</ul>
<img width="940" height="451" alt="image" src="https://github.com/user-attachments/assets/05c7b595-bcdb-436d-8bd5-b85528856b43" />
<img width="940" height="407" alt="image" src="https://github.com/user-attachments/assets/f148870b-6c03-4eaa-ab98-167a536c10e1" />
<img width="940" height="419" alt="image" src="https://github.com/user-attachments/assets/0d4f9d0c-57b6-4b70-945e-ca63593ef0af" />
<img width="940" height="338" alt="image" src="https://github.com/user-attachments/assets/7d42737c-2215-4bbe-bb1c-4aeb4723ee49" />
<img width="940" height="397" alt="image" src="https://github.com/user-attachments/assets/eefc4274-0c47-4927-a06b-2757bc90c725" />
<img width="940" height="432" alt="image" src="https://github.com/user-attachments/assets/10edf6d2-b1e2-4856-9801-17328ff84f2f" />

<h3>Function Testing</h3>
<ul>
  <li>Created test event <strong>SARTestEvent</strong></li>
  <li>Execution succeeded and email received with "Daily Sales Analysis Report"</li>
</ul>

<img width="940" height="526" alt="image" src="https://github.com/user-attachments/assets/62325308-28a1-444c-8ae2-876f0de2caae" />
<img width="940" height="438" alt="image" src="https://github.com/user-attachments/assets/e5ec5968-1244-4820-820e-6b5f7e7d6d3d" />
<img width="940" height="361" alt="image" src="https://github.com/user-attachments/assets/3b0dc65d-87d1-47ae-99a8-8f5106955b7c" />
<img width="940" height="302" alt="image" src="https://github.com/user-attachments/assets/f5d15bea-9c35-4aab-b5a9-1d846e636c4e" />
<img width="940" height="340" alt="image" src="https://github.com/user-attachments/assets/912be5b6-0ab5-482a-9205-f9c7c950f167" />
<img width="940" height="376" alt="image" src="https://github.com/user-attachments/assets/c2296652-0aa3-4f17-a654-41907fb8644b" />
<img width="940" height="378" alt="image" src="https://github.com/user-attachments/assets/7d4ef016-9137-4a24-ad00-d0c374a94b0d" />
<img width="940" height="373" alt="image" src="https://github.com/user-attachments/assets/1d75b20f-16b0-4f62-aebe-ee387a460691" />
<img width="940" height="350" alt="image" src="https://github.com/user-attachments/assets/0fcd73df-be00-46f3-a7b8-5124e0dafc64" />
<img width="940" height="385" alt="image" src="https://github.com/user-attachments/assets/aa024c2b-47fa-4c02-a891-8e13112b4a9a" />
<img width="940" height="389" alt="image" src="https://github.com/user-attachments/assets/9ceb1f8f-4d81-4d8f-a309-816648a1435c" />
<img width="940" height="355" alt="image" src="https://github.com/user-attachments/assets/0f2d012a-12ad-4df2-b9a3-c71cb18cbb1f" />
<img width="940" height="280" alt="image" src="https://github.com/user-attachments/assets/ad1cb638-dcd1-4f20-8c3a-7f5aa41a8ece" />
<h3>6. Scheduling Automation</h3>
<p>Configured a scheduled trigger (cron) to run reports automatically Monday through Saturday.</p>

<img width="940" height="713" alt="image" src="https://github.com/user-attachments/assets/0f8eb27f-e10f-42c0-8b47-e11ed8d46390" />
<img width="940" height="378" alt="image" src="https://github.com/user-attachments/assets/c4a22b5b-82f9-4eef-9412-dc544bd08f54" />


<h2>Outcome</h2>
<ul>
  <li>Automated serverless reporting pipeline</li>
  <li>Secure and scalable architecture</li>
  <li>Practical integration of AWS services</li>
</ul>

<h2>Skills</h2>
<p>
AWS Lambda • IAM • EC2 • SNS • Parameter Store • CloudWatch • VPC • AWS CLI
</p>

</body>
</html>
