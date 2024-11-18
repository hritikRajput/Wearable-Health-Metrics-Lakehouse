# **Wearable Analytics with Medallion Architecture**

## **Project Overview**

This project simulates a data engineering pipeline for a wearable device company. The pipeline processes data from health-tracking wristwatches and fitness centers, refining it using the **Medallion Architecture**. It demonstrates the integration of **batch and streaming data**, **data governance**, and **analytics-ready outputs** using modern data engineering tools.

The pipeline is designed to:
- **Ingest**: Process historical and real-time data into the Bronze Layer.
- **Transform**: Clean and refine data in the Silver Layer.
- **Aggregate**: Produce curated datasets in the Gold Layer for analytics and reporting.

---

## **1. Architecture Overview**

The project employs the **Medallion Architecture**, which refines data through three stages:
- **Bronze Layer**: Raw, ingested data from batch and streaming sources.
- **Silver Layer**: Cleaned and transformed data with quality checks and CDC handling.
- **Gold Layer**: Aggregated data, optimized for business insights and reporting.


---

## **2. Technologies and Tools**

- **Databricks**: For data lakehouse implementation.
- **Apache Spark**: Handles batch and streaming ETL processes.
- **Apache Kafka**: Streams real-time data to the Bronze Layer.
- **Azure Data Factory (ADF)**: Ingests batch data from Azure SQL.
- **ADLS Gen2**: Data storage backend for Bronze, Silver, and Gold layers.
- **Unity Catalog**: Enforces data governance and role-based access control.

---

## **3. Data Pipeline Overview**

### **Data Sources**
1. **Batch Data**: User registration and profile updates from Azure SQL.
2. **Streaming Data**: Real-time data streams from Kafka, including:
   - Health metrics (BPM).
   - Gym login/logout events.
   - Workout session details.

### **Pipeline Workflow**
The data pipeline consists of the following steps:
1. **Setup and Configuration**:
   - Initialize directories, configurations, and tables.
2. **Data Ingestion**:
   - Process historical (batch) and real-time (streaming) data into the Bronze Layer.
3. **Data Transformation**:
   - Apply cleaning, de-duplication, and CDC updates in the Silver Layer.
4. **Analytics and Reporting**:
   - Aggregate data into the Gold Layer for analytical insights.

### Include Diagram: Pipeline Workflow  
*(Place a flowchart showing the steps: ingestion → transformation → analytics, along with file movement through layers.)*

---

## **4. Project Workflow and Notebooks**

### **Notebooks Overview**

| Notebook Name          | Purpose                                                                 |
|-------------------------|-------------------------------------------------------------------------|
| `01-config.py`         | Configures directories and project parameters.                         |
| `02-setup.py`          | Creates databases, tables, and initial resources.                      |
| `03-history-loader.py` | Loads historical data into the Bronze Layer.                           |
| `04-bronze.py`         | Ingests raw batch and streaming data into the Bronze Layer.            |
| `05-silver.py`         | Cleans and refines Bronze Layer data into the Silver Layer.            |
| `06-gold.py`           | Aggregates data into analytics-ready tables in the Gold Layer.         |
| `07-run.py`            | Orchestrates the execution of all pipeline steps.                      |
| `08-batch-test.py`     | Tests batch data ingestion and transformation processes.               |
| `09-stream-test.py`    | Tests streaming data ingestion and transformation.                     |
| `10-producer.py`       | Simulates data production and validates data in the Bronze Layer.      |

### **Execution Steps**

1. **Setup**:
   - Run `01-config.py` to set directories and configurations.
   - Execute `02-setup.py` to create databases and tables.
2. **Historical Data Load**:
   - Run `03-history-loader.py` to ingest batch historical data.
3. **Data Ingestion**:
   - Use `04-bronze.py` to process batch and streaming data into the Bronze Layer.
4. **Data Transformation**:
   - Execute `05-silver.py` to refine data in the Silver Layer.
5. **Analytics and Reporting**:
   - Run `06-gold.py` to produce analytics-ready tables in the Gold Layer.
6. **Pipeline Orchestration**:
   - Use `07-run.py` to execute all stages sequentially.
7. **Batch Testing**:
   - Validate batch data processing using `08-batch-test.py`.
8. **Streaming Testing**:
   - Test streaming ingestion and transformation using `09-stream-test.py`.
9. **Data Simulation**:
   - Use `10-producer.py` to simulate data production and validate ingestion.

---

## **5. Data Governance and Security**

- **Unity Catalog**: Implements role-based access control, ensuring secure access to datasets.
- **Cluster Policies**: Manage compute resources and prevent unauthorized usage.

### Include Diagram: Data Governance Workflow  
*(Include a diagram that shows how Unity Catalog and cluster policies secure data access.)*

---

## **6. Analytics Use Cases**

### Gold Layer Tables
1. **Workout BPM Summary**:
   - Summarizes heart rate data during workout sessions.
   - Helps users and fitness centers monitor performance trends.
2. **Gym Usage Summary**:
   - Tracks gym login/logout trends to analyze facility usage.

### Include Diagram: Gold Layer Reporting  
*(Show sample Gold Layer tables and how they support business decisions.)*

---

## **7. Testing and Validation**

- **Batch Testing (`08-batch-test.py`)**:
   - Ensures accurate ingestion and transformation of batch data.
- **Streaming Testing (`09-stream-test.py`)**:
   - Validates real-time streaming ingestion and processing.
- **Data Validation (`10-producer.py`)**:
   - Simulates data production and checks ingestion integrity.

---

## **8. Key Features**

- **Batch and Streaming Integration**:
   - Combines historical and real-time data ingestion seamlessly.
- **Data Refinement**:
   - Progressive refinement through Bronze, Silver, and Gold layers.
- **Scalable Architecture**:
   - Supports large-scale data ingestion and transformation.
- **Data Governance**:
   - Enforces security and access controls via Unity Catalog.
