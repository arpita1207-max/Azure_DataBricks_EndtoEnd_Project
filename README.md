### Databricks ETL Project – Bronze, Silver & Gold Layers

### 📌 Project Overview

This project implements a scalable ETL pipeline on Databricks using the Medallion Architecture (Bronze → Silver → Gold).
The pipeline ingests raw data, applies transformations, and publishes curated datasets for analytics and reporting.

It demonstrates:

Delta Lake architecture (Bronze/Silver/Gold layers)

Streaming & batch ingestion

Data cleansing, transformations, and enrichment

Error handling & data governance

ADLS Gen2 as data storage with external location integration

Credential passthrough for secure access control

### 🏗️ Architecture

flowchart LR
    A[Raw Data Sources] --> B[Bronze Layer]
    B --> C[Silver Layer]
    C --> D[Gold Layer]
    D --> E[Analytics & BI Tools]


 #### Bronze Layer

Ingests raw data (Customers, Orders, Products, Regions).

Stored as Delta format in Azure Data Lake Storage Gen2 (ADLS).

Append-only storage for reliability.

#### Silver Layer

Cleans and standardizes Bronze data.

Handles schema evolution, null values, and type casting.

Creates domain-specific curated datasets.

#### Gold Layer

Business-ready tables for analytics.

Joins across domains (Customers, Orders, Products).

Supports KPIs, dashboards, and reporting use cases.

### 📂 Project Structure
Databricks ETL Project
│── Bronze-Layer.python        # Raw data ingestion (Delta tables)

│── Silver-Customers.python    # Customer transformations

│── Silver-Orders.python       # Order transformations

│── Silver-Products.python     # Product transformations

│── Silver-Regions.python      # Region transformations

│── Gold-Customers.python      # Final curated customers table

│── Gold-Orders.python         # Final curated orders table

│── Gold-Products.python       # Final curated products table

│── parameters.python          # Configurations & metadata


### ⚙️ Technologies Used

Databricks (DBFS, Notebooks, Delta Live Tables)

Delta Lake (time travel, schema enforcement, ACID transactions)

PySpark (transformations, cleaning, joins)

Azure Data Lake Storage Gen2 (ADLS) as the primary data storage

Unity Catalog external location for secure access to ADLS

Credential passthrough for fine-grained access control

Medallion Architecture (Bronze → Silver → Gold)

### 🚀 Key Features

End-to-end ETL pipeline with data lineage across layers.

Incremental & streaming ingestion with Delta Lake.

ADLS + External Location setup ensures data remains in cloud storage, not copied into Databricks.

Credential passthrough ensures security and compliance by mapping user identity to ADLS access.

Error handling: skipChangeCommits / materialized views for updates in source.

Parameterization for reusability across environments.

Business-ready Gold tables powering downstream BI dashboards.

### 🛠️ Deployment & Execution

Import notebooks (.dbc) into Databricks.

Configure ADLS external location and set up Unity Catalog permissions.

Run Bronze-Layer to ingest raw data into ADLS (Delta format).

Run Silver-layer notebooks for cleansing & transformation.

Run Gold-layer notebooks to publish curated data.

Use BI tools (Power BI, Tableau) for analytics.


### ⏱️ Job Scheduling & Orchestration

<img width="1136" height="562" alt="image" src="https://github.com/user-attachments/assets/3f92ccb0-c21b-4c0a-99cc-a0e13a3b6640" />


The entire ETL pipeline is orchestrated using Databricks Jobs, ensuring reliable, automated execution of Bronze → Silver → Gold workflows.

Job Workflow:

Bronze Ingestion runs first to load raw data from ADLS into Delta tables.

Silver Layer notebooks (Customers, Orders, Products) transform and clean the data.

Gold Layer notebooks (Customers, Products, Orders) aggregate and publish business-ready tables.

Scheduling: Jobs can be triggered manually or scheduled at defined intervals (hourly/daily/weekly).

Monitoring:

Job runs tracked with lineage visualization (upstream/downstream dependencies).

Automatic retries on failures.

Run history available for auditing and debugging.

Result: Automated, dependency-aware job orchestration that ensures each layer is executed in sequence with full data lineage tracking.



### 📊 Business Impact

Provided a reliable single source of truth across Customers, Orders, Products, and Regions.

Enabled real-time and batch analytics with curated Gold datasets.

Improved data quality, governance, and lineage using Delta Lake.

Leveraged ADLS external location + credential passthrough to ensure secure, compliant enterprise-grade deployment.

Reduced manual ETL effort with automated pipelines.

### 👩‍💻 Author

Arpita Sinha

Data Engineer | Data Analyst | SQL | Python | Power BI | Databricks



