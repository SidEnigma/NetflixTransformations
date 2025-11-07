# 🎬 Netflix Streaming Data Transformation using dbt & Snowflake

![dbt](https://img.shields.io/badge/dbt-v1.8+-orange?logo=dbt&logoColor=white)
![Snowflake](https://img.shields.io/badge/Snowflake-Data%20Warehouse-blue?logo=snowflake&logoColor=white)
![AWS S3](https://img.shields.io/badge/AWS-S3-232F3E?logo=amazon-aws&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)


## 📘 Project Overview

This project demonstrates an **end-to-end data transformation pipeline** for Netflix streaming analytics using **dbt** and **Snowflake**. Raw data from **AWS S3** is ingested into Snowflake, where dbt performs all transformations to produce **analytics-ready, governed data models**.


## ⚙️ Tech Stack

| Tool / Service | Purpose |
|------|----------|
| **dbt (data build tool)** | Transformation, testing, and data modeling |
| **Snowflake** | Cloud data warehouse for scalable compute & storage |
| **AWS S3** | Raw data source for ingestion |
| **SQL & Jinja** | Transformation logic and dynamic templating |
| **Git / GitHub** | Version control and project documentation |


## 🧩 Data Pipeline Architecture

The project follows a **modern analytics engineering pattern** with a clear separation between layers: <br/>
AWS S3 → Snowflake (Raw) → dbt Staging → dbt Intermediate (Dimension / Fact) → Data Marts → BI Layer


## 🧱 Project Structure
. <br/>
├── analyses/ # Analytical SQL scripts <br/>
├── macros/ # Custom tests for data consistency <br/>
├── models/ <br/>
│ ├── dim/ # Dimesional tables with business logic <br/>
| ├── fct/ # Fact tables <br/>
│ ├── mart/ # Dedicated tables for analytics <br/>
| └── staging/ # Views from raw data <br/>
├── seeds/ # Static CSVs for lookup data <br/>
├── snapshots/ # SCD management <br/>
├── tests/ # Generic and singular data tests <br/>
├── dbt_project.yml <br/>
└── packages.yml <br/>


## 🔍 Core dbt Concepts Showcased

### ⚙️ **Materializations**
Experimented with `view`, `table`, `ephemeral`, and `incremental` materializations to balance cost and performance.

### ✅ **Testing and Data Quality**
Used:
- **Generic tests:** `unique`, `not_null`, `relationships`, `accepted_values`
- **Singular tests:** Custom SQL assertions for business logic

### 🕒 **Snapshots (SCD Type 2)**
Implemented snapshots for **Slowly Changing Dimensions** to retain historical subscription and content data.

### 📦 **dbt Packages**
Integrated:
- `dbt_utils` for macros and schema testing  
- `dbt_expectations` for extended data validation

### 🌱 **Seeds**
Loaded static CSVs directly with dbt — ideal for reference tables without external sources.

### 🧩 **Macros & Jinja**
Developed reusable macros for **dynamic SQL generation** and **templated transformations**, ensuring modularity and maintainability.

### 📚 **Documentation**
Generated with:
```bash
dbt docs generate
dbt docs serve
