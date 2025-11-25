✈️ Airline Data Ingestion – Incremental ETL Pipeline
An Industrial-Grade Incremental Data Pipeline using Python, AWS Glue, Step Functions & Redshift
📌 Project Overview

The Airline Data Ingestion Pipeline is designed to ingest airport codes and daily flight data incrementally into an AWS-based data lake and warehouse environment.
This pipeline automates ingestion, processing, cataloging, and loading of airline datasets using AWS serverless components.

The project ensures:

Incremental processing using Job Bookmarking

Automated orchestration using AWS Step Functions

Catalog-driven metadata with Glue Crawler + Glue Catalog

Reliable notifications using SNS

Scalable storage + warehouse integration with S3 & Redshift

🏗️ Architecture Diagram
S3 (raw & daily flight data)
        |
        v
Glue Crawler ----> Glue Catalog ----> Redshift (preloaded + target tables)
        |
        v
Glue ETL Job (Incremental using Job Bookmark)
        |
        v
Step Functions Orchestration
        |
        v
EventBridge (Triggers SFN)
        |
        v
SNS Notifications (Success/Failure)

🔧 Tech Stack

Python

AWS S3

AWS Glue (Crawler, Catalog, ETL, Job Bookmarking)

AWS Step Functions

AWS EventBridge

AWS Redshift

AWS SNS

📂 Project Folder Structure
Airline-Data-Ingestion/
│
├── data/
│   ├── airport_codes/        # Static reference dataset
│   ├── flights_daily/        # Daily incremental files
│
├── glue-scripts/
│   ├── incremental_flights_etl.py
│
├── sql/
│   ├── create_airport_codes_table.sql
│   ├── create_flights_target_table.sql
│
└── README.md

🛠️ Project Workflow
1️⃣ Load airport codes & daily flight data into S3

Upload airport_codes.csv (static)

Upload daily flight files into the flights folder

2️⃣ Create Redshift Tables

Preload airport_codes table

Create flights_target table structure

3️⃣ Register Tables Using Glue Crawler

Crawler scans S3

Crawler scans Redshift

Tables added/updated in Glue Data Catalog

4️⃣ Incremental Processing with Glue ETL

Glue ETL job reads new flight files only

Uses Job Bookmarking to avoid duplicates

Cleans & transforms data

Loads into Redshift flights_target table

5️⃣ Pipeline Orchestration with Step Functions

Manages:

Starting Glue Job

Checking job status

Handling success/failure paths

6️⃣ EventBridge Trigger

EventBridge triggers the Step Function based on:

Scheduled time (daily)

OR new file arrival in S3

7️⃣ SNS Notifications

Sends email alerts on success

Sends alerts on failure with error details

📊 Key Features

✔ Incremental daily ingestion
✔ Fully automated orchestration
✔ Glue Crawler for schema management
✔ Glue Job Bookmarking prevents duplicate loads
✔ Redshift warehouse integration
✔ Notifications for monitoring
✔ Serverless, scalable, cost-efficient pipeline

▶️ How to Run

Upload datasets to S3

Run Glue Crawler to register tables

Deploy Glue ETL job with Job Bookmark enabled

Create Step Functions workflow

Connect Step Function to EventBridge trigger

Subscribe email to SNS topic

Run the pipeline

📬 Contact

If you want me to generate:
✔ Architecture diagram (image)
✔ Glue ETL Python script (full code)
✔ Step Functions definition (ASL JSON)
✔ SQL scripts for Redshift

Just tell me — I can add them to the repo!
