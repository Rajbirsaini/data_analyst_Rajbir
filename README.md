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

# Project 2
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

  # AWS Deployment Service (Module 1)
![image](https://github.com/user-attachments/assets/3272f92c-afdc-40c5-b710-fd2661dbc82c)

![image](https://github.com/user-attachments/assets/0dfa64d2-e49c-410f-b262-450874834119)
![image](https://github.com/user-attachments/assets/c772e954-c225-4c0f-a598-b20951df0f63)

![image](https://github.com/user-attachments/assets/f4fe162f-ee8f-4ffd-82d9-f69b0e4a84b4)

![image](https://github.com/user-attachments/assets/e26b77fb-fe72-407c-8647-822a3da42c03)

# AWS Cost Analysis (Module 2)
![image](https://github.com/user-attachments/assets/7087b100-5dd6-46de-9b58-58c39b01fdb9)
- Data Storage
![image](https://github.com/user-attachments/assets/28e5f324-ab21-48e3-aa38-2c5ec1768bdb)
- Data Profiling and Cleaning
![image](https://github.com/user-attachments/assets/1d335c88-ddba-46c9-afce-8c5602975f28)
- Data Analysis
![image](https://github.com/user-attachments/assets/066d78d9-24b2-4827-9eaa-dc5d4b645f9c)
![image](https://github.com/user-attachments/assets/38bcfe66-13be-4d50-9d4f-b0963491d8c7)
![image](https://github.com/user-attachments/assets/3ab4919f-caec-4fc5-96dd-bda0b3c3902c)

# AWS Global Infrastructure (Module 3)
![image](https://github.com/user-attachments/assets/42ca5e69-9fc2-491f-91bd-db72e467e78f)
![image](https://github.com/user-attachments/assets/5456e1fe-5d63-4343-b3d7-04f9e54782c3)
![image](https://github.com/user-attachments/assets/22964bb5-4d0c-4623-a866-dca833624bc2)

# AWS IAM (Module 4)

![image](https://github.com/user-attachments/assets/a8a4ae89-1954-4a2a-b886-28f3512abe0d)

![image](https://github.com/user-attachments/assets/8a3d474b-11ac-4fb8-be3e-e1c9edab190e)
![image](https://github.com/user-attachments/assets/70d417e6-63e6-42d5-8336-596469912406)

# AWS VPC (Module 5)
![image](https://github.com/user-attachments/assets/be1b2b0f-e319-435c-8e78-6a8ef9d3ebb1)
![image](https://github.com/user-attachments/assets/516cc8d7-363d-4b16-b8c0-d0ac741378bb)

# AWS Lambda (Module 6)

![image](https://github.com/user-attachments/assets/d4af70f7-a2ed-4f2e-bf5b-f00afcf99a77)
![image](https://github.com/user-attachments/assets/6adc8168-6096-4d0a-b217-1f32a1f3b20a)

# AWS EBS (Module 7)
![image](https://github.com/user-attachments/assets/0d6a61f4-b695-4bd7-ac0f-273d33c6b969)
![image](https://github.com/user-attachments/assets/375bd46c-ac7b-4b78-8698-79ff12b8303a)



