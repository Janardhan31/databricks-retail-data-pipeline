# End-to-End Retail Data Engineering Pipeline (Databricks)

## Overview
This project demonstrates an end-to-end data engineering pipeline built using Databricks Free Edition and Apache Spark.  
A large retail transactions dataset was processed to clean raw data, handle missing and invalid values, and generate analytics-ready datasets using Delta Lake and SQL.

The project follows a simplified Medallion Architecture approach with Silver and Gold layers.

---

## Tech Stack
- Databricks (Free / Community Edition)
- Apache Spark (PySpark)
- Delta Lake
- SQL

---

## Dataset
- **Online Retail Transactions Dataset**
- ~500,000+ rows of real-world e-commerce transaction data
- Dataset source: Kaggle (link provided in the `data` folder)

---

## Project Workflow

### 1. Raw Data
- Dataset uploaded to Databricks and accessed as a managed table
- Initial data exploration performed to understand schema and data quality issues

### 2. Silver Layer (Data Cleaning & Validation)
- Removed records with invalid values:
  - Negative or zero quantity
  - Zero or negative unit price
- Filtered records with missing `CustomerID`
- Handled missing `Country` values by replacing them with `"Unknown"`
- Added a business metric:
  - `total_amount = Quantity * UnitPrice`
- Stored cleaned data as a managed Delta table

### 3. Gold Layer (Analytics)
Created business-ready aggregated tables:
- **Daily Revenue** – total revenue per day
- **Country-wise Revenue** – revenue contribution by country
- **Top Products by Revenue** – products ranked by total sales value

These Gold tables are optimized for reporting and analytics use cases.

---

