# City of Vancouver Data Analytics Portfolio

![AWS](https://img.shields.io/badge/Built%20With-AWS-orange?logo=amazon-aws&logoColor=white)
![Project Type](https://img.shields.io/badge/Type-Data%20Engineering-blue)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> This project analyzes 16 years of employee remuneration and expense data from the City of Vancouver using AWS cloud tools such as S3, Glue, Athena, and DataBrew. It demonstrates a full serverless data engineering workflow including ingestion, cleaning, cataloging, querying, and monitoring.

## Project Title
**Analyzing Employee Remuneration and Expenses in the City of Vancouver**

## Objective
To analyze trends in salaries and expenses of Journeyman Mechanics between 2008 and 2023 using AWS data engineering services. The insights support budgeting, financial planning, and workforce decisions.

## Dataset Description
**Source:** City of Vancouver Open Data Portal  
**Name:** Employee Remuneration and Expenses – Earnings Over $75,000 (2008–2023)  
**Attributes:**
- Employee Name
- Department
- Job Title
- Year
- Remuneration
- Expenses

## Methodology

### Step 1: Data Ingestion
- Raw CSV file uploaded to **Amazon S3** bucket.
- Dataset includes 16 years of financial records for high-earning employees.

### Step 2: Data Profiling
- **AWS DataBrew** used to analyze the structure and quality of the data.
- Found 22% missing values in "expenses" and data type mismatches.

### Step 3: Data Cleaning
- Used **AWS Glue Studio** to create ETL job.
- Converted remuneration and expense fields to float.
- Filled missing values with `0`.
- Created two cleaned outputs: one for users, one for system.

### Step 4: Data Cataloging
- **AWS Glue Crawler** scanned cleaned data and added schema to the AWS Data Catalog.
- Enabled querying via **AWS Athena**.

### Step 5: Data Summarization
- **Athena** used to calculate:
  - Average annual remuneration
  - Average expenses per year
- **Findings:**
  - Salaries steadily increased.
  - Expenses fluctuated and were sometimes minimal or zero.

## Tools and Technologies
- **AWS S3** (storage)
- **AWS DataBrew** (profiling)
- **AWS Glue Studio** (ETL jobs)
- **AWS Glue Crawler** (cataloging)
- **AWS Athena** (SQL querying)

---

## AWS Deployment and Service Models
The platform was designed as a fully serverless, modular pipeline:
1. **Data Source:** Local CSV file  
2. **Ingestion:** Amazon S3  
3. **Profiling & Cleaning:** AWS DataBrew, AWS Glue Studio  
4. **Cataloging:** AWS Glue Crawler  
5. **Querying:** Amazon Athena  

---

## AWS Cost Analysis
- Glue DataBrew and Glue Studio jobs incur pay-per-use costs.
- Overall storage cost remains minimal.
- AWS Cost Estimator projected minimal monthly charges.

---

## AWS Global Infrastructure
Deployed in **Canada (Central)** region to comply with data residency laws.

---

## AWS IAM (Identity and Access Management)
- Used **KMS** for encryption
- IAM roles to limit access
- S3 versioning and replication

---

## AWS VPC
- Used default VPC for serverless operations.

---

## AWS Lambda
- Not implemented but planned for future automation.

---

## AWS EBS
- Not applicable in current serverless setup.

---

## Data Security
- KMS encryption, versioning, replication, IAM policies

## Data Governance
- AWS Glue Data Quality checks
- Threshold: 95% completeness
- Versioning for traceability

## Data Monitoring
- **CloudWatch** for job metrics and billing
- **CloudTrail** for access and modification logs

---

## Conclusion & Recommendations
### Key Takeaways
- AWS architecture supports civic data analysis
- Strong IAM and audit practices
- Insightful analytics for planning

### Future Work
- Add AWS Lambda
- Use SageMaker for forecasting
- Create public Power BI dashboard

---

## Repository Structure
```bash
├── data/
│   └── raw_dataset.csv
├── notebooks/
│   └── descriptive_analysis.ipynb
├── aws_configs/
│   └── glue_jobs/
│   └── crawler_schema.json
├── screenshots/
│   └── profiling.png
│   └── cleaning_etl.png
│   └── cloudwatch.png
├── reports/
│   └── final_report.md
├── README.md
```

---

