# data-analyst-amender
# City of Vancouver Data Analytics Portfolio

## Project Title

**Analyzing Employee Remuneration and Expenses in the City of Vancouver**

## Objective

To analyze trends in salaries and expenses of Journeyman Mechanics between 2008 and 2023 using AWS data engineering services. The insights support budgeting, financial planning, and workforce decisions.

## Dataset Description

**Source:** City of Vancouver Open Data Portal
**Name:** Employee Remuneration and Expenses – Earnings Over \$75,000 (2008–2023)
**Attributes:**

* Employee Name
* Department
* Job Title
* Year
* Remuneration
* Expenses

## Methodology

### Step 1: Data Ingestion

* Raw CSV file uploaded to **Amazon S3** bucket.
* Dataset includes 16 years of financial records for high-earning employees.

### Step 2: Data Profiling

* **AWS DataBrew** used to analyze the structure and quality of the data.
* Found 22% missing values in "expenses" and data type mismatches.

### Step 3: Data Cleaning

* Used **AWS Glue Studio** to create ETL job.
* Converted remuneration and expense fields to float.
* Filled missing values with `0`.
* Created two cleaned outputs: one for users, one for system.

### Step 4: Data Cataloging

* **AWS Glue Crawler** scanned cleaned data and added schema to the AWS Data Catalog.
* Enabled querying via **AWS Athena**.

### Step 5: Data Summarization

* **Athena** used to calculate:

  * Average annual remuneration
  * Average expenses per year
* Findings:

  * Salaries steadily increased.
  * Expenses fluctuated and were sometimes minimal or zero.

## Tools and Technologies

* **AWS S3** (storage)
* **AWS DataBrew** (profiling)
* **AWS Glue Studio** (ETL jobs)
* **AWS Glue Crawler** (cataloging)
* **AWS Athena** (SQL querying)

---

## AWS Deployment and Service Models

The platform was designed as a fully serverless, modular pipeline:

1. **Data Source:** Local CSV file
2. **Ingestion:** Amazon S3
3. **Profiling & Cleaning:** AWS DataBrew, AWS Glue Studio
4. **Cataloging:** AWS Glue Crawler
5. **Querying:** Amazon Athena

This design ensures scalability, low-cost operation, and modular maintenance.

---

## AWS Cost Analysis

Using **Standard S3 storage** and **daily read frequency**:

* Glue DataBrew and Glue Studio jobs incur pay-per-use costs.
* Overall storage cost remains minimal due to limited file size and optimization.
* AWS Cost Estimator projected minimal monthly charges under budget constraints.

---

## AWS Global Infrastructure

Deployed in **Canada (Central)** region to comply with data residency laws. The global AWS architecture ensures low-latency performance, high availability, and geographic redundancy.

---

## AWS IAM (Identity and Access Management)

* Used **KMS** to encrypt data in S3 with customer-managed keys.
* Defined specific IAM roles to limit access.
* Enabled **bucket versioning** to support rollback and file recovery.
* Set up S3 **replication** for backup resilience.

---

## AWS VPC (Virtual Private Cloud)

* Default VPC used for Glue, Athena, and S3 services.
* Future iterations may implement private subnet configuration for Glue jobs to enhance security.

---

## AWS Lambda

* Not used in this version of the project.
* Could be used in future to automate:

  * Trigger notifications
  * Auto-validation
  * Periodic updates

---

## AWS EBS (Elastic Block Store)

* Not applicable since project used **serverless architecture**.
* May be included in future if EC2-based compute is required.

---

## Data Security

* Encryption via **KMS**
* Enabled **versioning** to prevent accidental loss
* Set **replication rules** to backup S3 buckets
* Granular **access control** via IAM policies

## Data Governance

* Used **AWS Glue Evaluate Data Quality** transform
* Applied 95% completeness threshold for remuneration and expenses
* Passed and failed data stored in separate S3 destinations for auditability
* S3 versioning supported traceability

## Data Monitoring

* **Amazon CloudWatch** dashboard set up to monitor:

  * Job execution time
  * S3 storage size
  * Cost estimation alarms
* **AWS CloudTrail** logs monitored:

  * Glue job modifications
  * IAM changes
  * S3 policy edits
* Alerts notified on cost overages or unexpected resource changes

---

## Conclusion & Recommendations

This portfolio project successfully demonstrated how a public dataset can be analyzed end-to-end using AWS services. Key takeaways:

* Serverless AWS architecture scales well for civic data
* IAM and CloudTrail ensure security and accountability
* Descriptive analytics provide actionable insights for city financial planning

**Recommendations for future work:**

* Introduce **AWS Lambda** for automation
* Add **predictive analytics** using SageMaker
* Develop a public **Power BI dashboard** for citizens and stakeholders

---

## Repository Structure (Suggested for GitHub)

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




