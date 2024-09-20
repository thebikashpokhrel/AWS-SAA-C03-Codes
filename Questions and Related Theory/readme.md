# Questions and Related Theory

1. **A company collects data for temperature, humidity, and atmospheric pressure in cities across multiple continents. The average volume of data that the company collects from each site daily is 500 GB. Each site has a high-speed Internet connection. The company wants to aggregate the data from all these global sites as quickly as possible in a single Amazon S3 bucket. The solution must minimize operational complexity. Which solution meets these requirements?**

   A. Turn on S3 Transfer Acceleration on the destination S3 bucket. Use multipart uploads to directly upload site data to the destination S3 bucket.

   B. Upload the data from each site to an S3 bucket in the closest Region. Use S3 Cross-Region Replication to copy objects to the destination S3 bucket. Then remove the data from the origin S3 bucket.

   C. Schedule AWS Snowball Edge Storage Optimized device jobs daily to transfer data from each site to the closest Region. Use S3 Cross-Region Replication to copy objects to the destination S3 bucket.

   D. Upload the data from each site to an Amazon EC2 instance in the closest Region. Store the data in an Amazon Elastic Block Store (Amazon EBS) volume. At regular intervals, take an EBS snapshot and copy it to the Region that contains the destination S3 bucket. Restore the EBS volume in that Region.

**Related Theory:**

## **S3 Transfer Acceleration**

Can speed up content transfers to and from Amazon S3 by as much as 50-500% for long-distance transfer of larger objects. Logically Shortens the distance between Client Applications and AWS S3 Servers. Full utilization of bandwidth for transfer

**Keyword:** Long distance data transfers

**Scenario**

- Many customers develop mobile or web applications that feature file uploads to S3. When these applications have users that are far from the destination S3 bucket, uploads and downloads may be slow. S3TA can help speed up these long-distance transfers to provide users a better experience.
- IT infrastructure teams and line-of-business teams have on-premises applications in distributed locations that use the S3 API to store files, lab imagery or media in a centralized bucket. S3TA can help speed up such time-sensitive transfers over long distances.
- Companies who engage in research and development projects often generate large quantities of data. They may collaborate with universities, hospitals, think tanks or even peer companies. For sharing of large data sets between companies, customers can set up special access to their S3 buckets with accelerated uploads to speed data exchanges and the pace of innovation.

## Multipart Uploads

- Allows to upload single object as set of parts
- Each part can be uploaded independently in any order in parallel. If transmission of any part fails, you can retransmit that part without affecting other parts.
- For bigger files use multipart upload
- **Scenario**: Uploading large objects over a stable high-bandwidth network
- If you're uploading over a spotty network, use multipart upload to increase resiliency to network errors by avoiding upload restarts. When using multipart upload, you need to retry uploading only the parts that are interrupted during the upload. You don't need to restart uploading your object from the beginning.

## S3 Cross Region Replication

- Replicate objects into other AWS regions for reduced latency, compliance, security, disaster recovery.
- Can set up replication at a bucket level, a shared prefix level, or an object level using S3 object tags.
- **Scenario:** Data replication over multiple regions for compliance, latency minimization, Compute Clusters in two or more regions analyzing same set of objects in this case maintaining same copies in all regions

## AWS Snowball

- Accelerate moving offline data or remote storage to the cloud
- Easily migrate terabytes of data to the cloud without limits in storage capacity or compute power.
- **Scenario:**
  - Move databases, backups, archives, healthcare records, analytics datasets, IoT sensor data and media content to the cloud - especially when network conditions are limited.
  - Run Amazon Machine Images (AMIs) within Amazon EC2 and deploy AWS Lambda code on Snowball Edge devices with machine learning (ML) or other applications.

**Answer Explanation:**

Key points: Real time data, Large data volume, High Speed Internet, Minimize Operational Complexity

Option A is correct

**S3TA for large data volume with high speed internet and multipart for larger data. Also, less operational overhead**

**2. A company needs the ability to analyze the log files of its proprietary application. The logs are stored in JSON format in an Amazon S3 bucket. Queries will be simple and will run on-demand. A solutions architect needs to perform the analysis with minimal changes to the existing architecture. What should the solutions architect do to meet these requirements with the LEAST amount of operational overhead?**

A. Use Amazon Redshift to load all the content into one place and run the SQL queries as needed.

B. Use Amazon CloudWatch Logs to store the logs. Run SQL queries as needed from the Amazon CloudWatch console.

C. Use Amazon Athena directly with Amazon S3 to run the queries as needed.

D. Use AWS Glue to catalog the logs. Use a transient Apache Spark cluster on Amazon EMR to run the SQL queries as needed.

**Related Theory:**

## Amazon Redshift

- Fully managed, AI powered, Massively Parallel Processing (MPP) Data Warehouse built for performance, scale, and availability.
- Easily access or ingest data across your data lakes, databases, data warehouses, streaming data - with no code/low code zero-ETL approach for integrated analytics
- Run SQL Queries, Open Source Analytics
- **Scenarios:**
  - Ingests hundreds of megabytes of data per second so you can query data in near real time and build low latency analytics applications for fraud detection, live leaderboards, and IoT.
  - Whether it's market data, social media analytics, weather data or more, subscribe to and combine third party data in AWS Data Exchange with your data in Amazon Redshift, without hassling over licensing and onboarding processes and moving the data to the warehouse.

## Amazon CloudWatch

- Observe and monitor resources and applications on AWS, on premises, and on other clouds
- Improve operational performance using alarms and automated actions set to activate at predetermined thresholds
- Troubleshoot operational problems with actionable insights derived from logs and metrics in your CloudWatch dashboards
- Amazon CloudWatch Logs to monitor, store, and access your log files from Amazon Elastic Compute Cloud (Amazon EC2) instances, AWS CloudTrail, Route 53, and other sources.
- **Scenarios:**
  - Find out exactly when your website is impacted and for how long by viewing screenshots, logs, and web requests at any point in time.
  - Visualize performance data, create alarms, and correlate data to understand and resolve the root cause of performance issues in your AWS resources

## Amazon Athena

- Provides a simplified, flexible way to analyze petabytes of data where it lives.
- Analyze data or build applications from an Amazon Simple Storage Service (S3) data lake and 30 data sources, including on-premises data sources or other cloud systems using SQL or Python.
- **Scenarios:**
  - Run queries directly on S3, on premises, or on other clouds

## AWS Glue

- A serverless data integration service that makes it easier to discover, prepare, move, and integrate data from multiple sources for analytics, machine learning (ML), and application development.
