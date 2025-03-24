# Healthcare Metrics Project Walkthrough: End-to-End Data Pipeline with AWS, Snowflake & DBT

## 🎯 Project Objective:
To design and deploy a complete data engineering pipeline that ingests data from Google Drive, processes it using AWS services, transforms it with DBT, and analyzes it in Jupyter Lab.

---

### Explore 1: Initial Data Analysis (`01_exploratory_data.ipynb`)
**Objective**: Analyze raw data for schema, relationships, and data quality.  
**Tasks**:
- Schema exploration and column relationships.
- Missing value analysis (e.g., histograms, summary tables).
- Duplicate detection and outlier identification.
- Basic visualizations (e.g., distributions, correlations).  
**Tools**: Pandas, NumPy, Matplotlib/Seaborn.  
**Deliverables**:
- Report on data quality (missing values, duplicates).
- List of key columns for joins (e.g., `CMS Certification Number (CCN)`).
from pathlib import Path



---
## 📁 Step 1: Data Ingestion - Google Drive to AWS S3 (Source Bucket)
- Data files are sourced from **Google Drive**.
- I use **Python scripts in VSCode** to:
  - Authenticate with Google Drive.
  - Fetch new/updated files.
  - Upload files into the **S3 Source Bucket**.

---

## ☁️ Step 2: CloudFormation for AWS Infrastructure 
### Pipeline Architecture steps (`02_aws_glue_formation.ipynb`)
All AWS resources are **automated using CloudFormation** templates:

### 📂 cloudformation/
```
├── 1-iam-roles-stack.json           # Defines IAM roles & policies for Glue, S3, Lambda
├── 2-s3-buckets-stack.json          # Sets up S3 Source and Processed buckets
├── 3-glue-snowflake-stack.json      # Creates Glue connections, crawlers, jobs for Snowflake integration
├── 4-glue-workflow-stack.json       # Defines Glue workflows for orchestration
├── 5-sns-sqs-notification-stack.json # Notification system using Outlook email
├── 6-s3-template-notify.json        # S3 notification events to trigger SNS
└── parameters/
    ├── dev-params.json              # Development environment parameters
    └── prod-params.json             # Production environment parameters
```

---

## 🔁 Step 3: Data Pipeline Flow
### 🔹 From S3 Source Bucket to Snowflake via Glue:
- **Glue Crawler** infers schema from S3 and creates a Glue catalog table.
- **Glue Job** processes and loads the data into **Snowflake (source schema)**.
- After loading to Snowflake, data is also stored into a **Processed S3 bucket** for archival.

### 🔹 Notification Integration:
- **S3 Upload Event** triggers **SNS topic**.
- **SNS** notifies **Lambda function**, which sends an email alert via **Outlook.com SMTP**.

---

## 📦 Step 4: Data Modeling using DBT on Snowflake
- **DBT Snowflake Project** structure:
  - `staging/` - Cleans and standardizes raw source data.
  - `transform/` - Applies business logic and derived calculations.
  - `mart/` - Final tables for reporting and analysis (Warehouse & Reports).

---

## 📊 Step 5: Final Analysis in Jupyter Lab: 
### Data Pipeline & Metrics Reports (`04_healthcare_rpt_matrics.ipynb`)
- DBT models are queried via **Snowpark in Jupyter Lab**.
- Visualizations and analytics are built in **Pandas, Plotly, Seaborn**.

---

## 📧 Summary: End-to-End Flow
```
Google Drive → VSCode Scripts → S3 Source Bucket
   ↓
CloudFormation Sets Up AWS Stack
   ↓
S3 → Glue Crawler → Snowflake (source)
         ↓           ↓
      SNS Notify → Lambda → Outlook Email
         ↓
    Snowflake DBT Models → Mart Layer
         ↓
    Reports & Analysis → Jupyter Lab
```

---

## 🚀 Future Enhancements:
- Add Delta Lake support for S3 ingestion.
- Automate DBT model tests via CI/CD.
- Integrate with Apache Airflow for complex orchestration.

---

This pipeline showcases a **modular, event-driven, cloud-native architecture** for modern data platforms.

👉 Stay tuned for the full walkthrough demo on YouTube!
