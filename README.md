# Project 1
Overview of AWS Data Analysis Project
- Pipeline 1: Data Ingestion
  This pipeline ingests the raw tree inventory dataset (public-trees-adnac st.xlsx) into an S3 bucket (vancouver-tree-data-member4). It lays the foundation for further processing and ensures all source data is properly and securely stored.
- Pipeline 2: Data Profiling
  This pipeline profiles the raw data by analyzing columns like species_name, common_name, and cultivar_name. It provides a summary of data quality, revealing distinct values, duplicates, and nulls that help assess data readiness.
- Pipeline 3: Data Cleaning
  This pipeline handles data preparation. It drops rows with nulls in cultivar_name and formats the NEIGHBOURHOOD_NAME column into sentence case. This ensures that all data is cleaned and standardized before further processing.
- Pipeline 4: Data Cataloging
  Here, a Glue Crawler (tree-cleaning-crawler) is set up to scan cleaned data and store metadata into AWS Glue Data Catalog under the trees_db database. The resulting table (cleaned_clean_tree_job_csv) contains 17 columns properly typed and queryable.
- Pipeline 5: Data Summarization
  This pipeline utilizes Athena to query the cleaned data in S3. A query returns the count of each tree species per neighbourhood, answering the business question about the most common trees across Vancouver.
- AWS Pricing Estimate
  A minimal AWS cost estimate was also prepared to ensure a cost-efficient setup across all tools (S3, Glue, Athena).
![image](https://github.com/user-attachments/assets/94c3194d-307b-4d7c-8e4b-6fb1c6080376)

#Project 2
- Pipeline 1: Data Encryption & Security
  Created a KMS key (public-tree-key-rajbir) to enable secure data encryption on S3. The key is configured with proper permissions — admins manage the key, while authorized users can encrypt/decrypt data as required.
- Pipeline 2: Encryption on S3 Buckets
  Enabled the created KMS key as the default encryption on all S3 buckets used for the project (raw, clean, and curated). This ensures that all uploaded datasets are encrypted at rest, protecting data integrity and privacy.
- Pipeline 3: S3 Versioning & Backup
  Implemented S3 versioning across all project buckets. Versioning tracks all file updates and allows restoration of previous file versions, reducing risk of data loss due to accidental deletion or overwrites.
- Pipeline 4: Replication Rule
  Set up an S3 replication rule to automatically copy new raw data into a destination bucket. This replication is encrypted using the project’s KMS key and is restricted to the data team’s IAM role, ensuring reliable backups and fault tolerance.
- Pipeline 5: Data Governance (Glue ETL)
  Used AWS Glue Studio for ETL operations.
  Passed quality-check records (121/200) moved to clean-tree-trf-rajbir/Passed/.
  Failed records (79/200) moved to clean-tree-trf-rajbir/Failed/.
  This structure simplifies access control and audit trails for the data engineering team.
- Pipeline 6: Monitoring & Alerting
  Created a CloudWatch dashboard (public-tree-CW-rajbir) to monitor S3 bucket usage, file sizes, and Glue job execution metrics.
  Defined a CloudWatch alarm (public-tree-alm-rajbir) that tracks S3 bucket size and sends email notifications if bucket size exceeds 2MB threshold, ensuring rapid response to data volume spikes.
- Pipeline 7: CloudTrail Implementation
  Enabled CloudTrail to record all account activity across AWS resources for compliance, security monitoring, and troubleshooting. CloudTrail logs help review who accessed data, what was changed, and when — providing a complete audit trail.
  ![image](https://github.com/user-attachments/assets/cdba2585-047d-436c-90ea-98fd45c6deb2)
