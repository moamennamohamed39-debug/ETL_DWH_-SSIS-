# SSIS-ETL-Sales-Data-Warehouse-Project

## 📌 Overview

This project demonstrates the design and implementation of a complete **ETL (Extract, Transform, Load) pipeline** using **SQL Server Integration Services (SSIS)**.

The pipeline processes raw sales data from CSV files, transforms it, and loads it into a structured **SQL Server Data Warehouse** using a **Star Schema (Fact & Dimension tables)**.

It includes advanced data warehousing techniques such as:

* **Slowly Changing Dimension Type 2 (SCD Type 2)** for historical tracking
* **Incremental Loading** using a `LastModified` column

---

## 🛠️ Technologies Used

* SQL Server
* SQL Server Integration Services (SSIS)
* Visual Studio Community (SSDT)
* CSV Files (Data Source)
* Data Flow & Control Flow Tasks
* Lookup Transformation
* Derived Column Transformation
* Data Conversion Transformation

---

## 🧱 Data Architecture

### 🔹 ETL Flow

CSV Files → Staging Tables → Dimension Tables → Fact Table

### 🔹 Data Model

* **Fact Table:** Sales transactions
* **Dimension Tables:**

  * Customer Dimension (SCD Type 2)
  * Product Dimension (SCD Type 2)
  * Date Dimension (if implemented)

---

## ⚙️ ETL Process

### 1. Extract

* Sales data is extracted from CSV files

### 2. Load to Staging

* Raw data is loaded into SQL Server staging tables

### 3. Transform (SSIS Data Flow)

* Data Conversion → standardizes data types
* Derived Columns → creates calculated fields
* Lookup Transformation → maps dimension keys

### 4. Slowly Changing Dimension (Type 2)

* Tracks historical changes in dimension tables
* Inserts new records when changes occur
* Maintains:

  * Start Date
  * End Date
  * Current Flag

### 5. Incremental Load

* Uses `LastModified` column
* Loads only new or updated records (not full reload)

### 6. Load Fact Table

* Uses surrogate keys from dimensions
* Loads cleaned and structured data into Fact table

---

## 📦 SSIS Project Structure

All ETL processes are organized within a **single SSIS project**.
Each package is responsible for a specific stage in the pipeline:

* `01_Load_Staging.dtsx` → Load CSV data into staging tables
* `02_Load_Dimensions_SCD2.dtsx` → Handle SCD Type 2 for dimensions
* `03_Load_FactSales.dtsx` → Load fact table with surrogate keys
* `04_Incremental_Load.dtsx` → Process incremental updates

---

## 📊 Key Features

* End-to-end ETL pipeline
* Star Schema data warehouse design
* SCD Type 2 implementation (historical tracking)
* Incremental data loading (performance optimized)
* Lookup-based key resolution
* Modular SSIS package design

---

## 📊 Project Images

- [Dim Salesman](ETL_(ssis)_DWH/Images/dim-salesman.png)
- [Dim Customer](ETL_(ssis)_DWH/Images/dim_customer.png)
- [Dim Product](ETL_(ssis)_DWH/Images/dim_product.png)
- [Fact Sale](ETL_(ssis)_DWH/Images/fact_sale.png)
- [Incremental Load](ETL_(ssis)_DWH/Images/incremental_load.png)
- [OLAP Diagram](ETL_(ssis)_DWH/Images/olap_diagram.png)
- [OLTP Diagram](ETL_(ssis)_DWH/Images/oltp_diagram.png)

## 🚀 How to Run

1. Open the solution in **Visual Studio Community (SSDT)**
2. Execute SQL scripts in `/SQL_Scripts` to create the database
3. Update connection managers inside SSIS packages
4. Run packages in order:

   * `01_Load_Staging`
   * `02_Load_Dimensions_SCD2`
   * `03_Load_FactSales`
   * `04_Incremental_Load`

---

## 🎯 Project Purpose

This project demonstrates practical skills in:

* Data Warehousing
* ETL pipeline design
* SSIS development
* Incremental data processing
* Historical data tracking using SCD Type 2

---

## 👨‍💻 Author

Data Engineering Project – SSIS ETL Pipeline

---

## 📌 Notes

* This project is intended for educational and portfolio purposes
* No sensitive or production data is included
