# AWS S3 – Glue – Athena Data Engineering Pipeline

## 📌 Overview
This project demonstrates a cloud-native data engineering pipeline built
entirely on AWS using S3, AWS Glue, and Amazon Athena.

The pipeline ingests raw customer data, applies data quality rules using
AWS Glue (PySpark), and produces analytics-ready datasets queried using Athena.

---

## 🛠 AWS Services Used
- Amazon S3 (Data Lake)
- AWS Glue (ETL + Data Catalog)
- Amazon Athena (SQL Analytics)

---

## 🏗 Architecture
S3 (Raw) → AWS Glue → S3 (Curated) → Glue Catalog → Athena

---

## 📂 Project Structure
<pre>
aws-s3-glue-athena-pipeline/
├── data/raw/customers.csv
├── glue_jobs/customer_etl_job.py
├── athena/sample_queries.sql
├── architecture/pipeline_overview.md
└── README.md
</pre>

---

## ✅ Data Quality Rules
- customer_id must not be null
- email must contain '@'
- country must not be empty
- signup_date cast to DATE

---

## 🚀 How to Run
1. Upload CSV to S3 raw bucket
2. Create AWS Glue job using provided script
3. Run Glue job
4. Query data using Athena

---

## 📊 Sample Analytics
```sql
SELECT country, COUNT(*) FROM curated_customers GROUP BY country;
