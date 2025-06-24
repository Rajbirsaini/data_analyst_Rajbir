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
