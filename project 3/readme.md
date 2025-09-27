<img width="1511" height="717" alt="image" src="https://github.com/user-attachments/assets/87b10ee4-ea7a-4142-8a12-2f3476fcdbb0" />


**Azure Data Engineering Project:** Multi-Source Data Pipeline with Medallion Architecture
**Project Overview**
This project implements a robust data engineering pipeline on Azure that ingests data from two different sources (Web API and SQL Database), processes it using the Medallion Architecture, and delivers curated data for Power BI visualization and KPI insights.

**Architecture & Design**
**Data Sources**
Web API: Real-time data ingestion from external REST API

SQL Database: Structured data extraction from Azure SQL Database

**Medallion Architecture Implementation**
Bronze Layer (Raw Data)
Raw data ingestion from both sources

Schema enforcement and basic validation

Timestamped data capture for audit purposes

Silver Layer (Cleaned & Validated Data)
Data cleaning and standardization

Deduplication and data quality checks

Delta table format for reliability and performance

Structured and query-ready datasets

Gold Layer (Business-Level Aggregations)
Business-specific aggregations and metrics

Enriched datasets for analytics and reporting

Delta table format with optimized partitioning

Ready for consumption by BI tools

**Technology Stack**
**Azure Databricks:** Data processing and transformation

**Delta Lake:** Storage format for all layers

**Azure Data Factory:** Orchestration and scheduling

**Power BI:** Data visualization and KPI dashboards

**Azure SQL Database:** Source system

****Web API:**** **External data source
****
Project Structure**
text
project/
├── notebooks/
│   ├── 01_bronze_ingestion/
│   │   ├── web_api_ingestion.py
│   │   └── sql_database_ingestion.py
│   ├── 02_silver_processing/
│   │   ├── data_cleaning.py
│   │   └── data_validation.py
│   └── 03_gold_aggregation/
│       ├── business_metrics.py
│       └── powerbi_preparation.py
├── pipelines/
│   └── main_orchestration.json
├── config/
│   └── environment_variables.json
└── documentation/
    └── data_dictionary.md
**Key Features**
**Data Ingestion**
**Web API:** Automated API calls with error handling and retry logic

**SQL Database:** Incremental data extraction using watermark columns

**Data Validation:** Schema validation and data quality checks at ingestion

**Data Processing**
**Delta Tables:** ACID transactions and time travel capabilities

**Incremental Processing**: Efficient updates using MERGE operations

**Data Quality:** Automated checks and alerting for data anomalies

**Analytics & Visualization**
**Pre-aggregated Metrics:** Business KPIs ready for visualization

**Power BI Integration:** Direct connection to Databricks SQL tables

**Real-time Insights:** Near real-time data updates for dashboards

**Setup & Configuration**
**Prerequisites**
Azure Subscription with appropriate permissions

Databricks Workspace

Power BI Pro License

Azure SQL Database

API credentials for web data source

**Environment Setup**
Clone the repository to your Databricks workspace

Configure environment variables in config/environment_variables.json

Set up linked services in Azure Data Factory

Configure Power BI data source connections

**Pipeline Execution**
The main data pipeline is orchestrated through Azure Data Factory and can be triggered:

On a schedule (daily/hourly)

Event-based triggers

Manual execution for testing

**Delta Table Structure**
Silver Layer Tables
silver.customers_delta - Cleaned data

silver.transactions_delta - Processed transaction records

silver.products_delta - Standardized product information

Gold Layer Tables
gold.customer_metrics_delta - Customer lifetime value and behavior metrics

gold.sales_aggregations_delta - Daily/weekly/monthly sales summaries

gold.product_performance_delta - Product sales and performance indicators

**Power BI Integration**
Connection Setup
Databricks SQL Warehouse: Configured for optimal query performance

Direct Query Mode: Real-time data access for Power BI reports

Scheduled Refreshes: Automated data updates based on business requirements

**Key Dashboards**
Sales Performance: Revenue trends and regional performance

Customer Analytics: Customer segmentation and behavior insights

Product Intelligence: Sales patterns and inventory optimization

**Monitoring & Maintenance**

Data Quality Monitoring
Automated data validation checks

Alerting for data pipeline failures

Performance monitoring of Delta tables

**Performance Optimization**

Delta table optimization (Z-ordering, compaction)

Partitioning strategies for large datasets

Query performance tuning for Power BI

