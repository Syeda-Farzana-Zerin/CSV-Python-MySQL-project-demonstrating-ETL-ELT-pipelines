CSV-Python-MySQL-project-demonstrating-ETL-ELT-pipelines
A hands-on Python + MySQL project demonstrating ETL vs ELT pipelines using synthetic employee data, with CSV ingestion, SQL-based transformations, and Jupyter-based analysis.

ETL vs ELT with Python, MySQL, and Jupyter
=================================

Repository Description
----------------------
A hands-on Python + MySQL project demonstrating ETL (Extract–Transform–Load)
and ELT (Extract–Load–Transform) pipelines using synthetic employee data,
CSV ingestion, SQL-based transformations, and Jupyter-based analysis.

--------------------------------------------------

OVERVIEW
--------
This project demonstrates BOTH ETL and ELT data pipelines using:

- Python (pandas, SQLAlchemy)
- MySQL (XAMPP)
- Jupyter Notebook
- Synthetic CSV data

The goal is to clearly show how ETL and ELT differ, when to use each,
and how they are implemented in practice using the SAME dataset.

--------------------------------------------------

PROJECT STRUCTURE
-----------------
.
├── employees_1000.csv
├── ETL_Demo.ipynb
├── ELT_Demo.ipynb

--------------------------------------------------

DATASET
-------
Synthetic employee dataset with 1,000 rows.

Columns:
- name
- age (with missing values)
- salary (with missing values)
- city
- department
- hire_date

Missing values are intentional and used to demonstrate transformations.

--------------------------------------------------

ETL PIPELINE (Extract – Transform – Load)
-----------------------------------------

Definition:
ETL means data is transformed BEFORE loading into the database.

Flow:
CSV → Python (pandas) → MySQL

Steps:
1. Extract: Read CSV into pandas
2. Transform:
   - Fill missing values
   - Create derived features (years_of_service)
3. Load: Write cleaned data into MySQL

Characteristics:
- Python-centric
- Suitable for machine learning
- Feature engineering friendly
- No raw data preserved in database

Use ETL when:
- Building ML pipelines
- Doing research and experimentation
- Python is the main processing layer

--------------------------------------------------

ELT PIPELINE (Extract – Load – Transform)
-----------------------------------------

Definition:
ELT means raw data is loaded FIRST, then transformed using SQL.

Flow:
CSV → MySQL (RAW) → MySQL (CLEAN / ANALYTICS)

Tables:
1. employees_raw
   - Original untouched data
   - Contains missing values
   - NEVER modified

2. employees_extended
   - Cleaned data
   - Missing values handled
   - New features added

3. employees_analytics
   - Aggregated data
   - Used for BI and reporting

Characteristics:
- Database-centric
- SQL-driven transformations
- Raw data preserved
- Easy reprocessing and auditing

Use ELT when:
- Building BI dashboards
- Supporting analysts
- Working with SQL-heavy workflows
- Data governance is important

--------------------------------------------------

SQL TRANSFORMATIONS (ELT)
------------------------
Transformations are done entirely in MySQL:

- COALESCE for missing values
- Aggregate functions (AVG)
- Date calculations (TIMESTAMPDIFF)
- Creation of analytics tables

This makes transformations transparent, auditable, and reproducible.

--------------------------------------------------

JUPYTER NOTEBOOK
----------------
The notebook allows inspection of:

- employees_raw
- employees_extended
- employees_analytics

All tables can be viewed side-by-side using pandas DataFrames.

--------------------------------------------------

ETL vs ELT COMPARISON
--------------------

ETL:
- Transform in Python
- No raw data stored
- Best for ML and feature engineering

ELT:
- Transform in SQL
- Raw data preserved
- Best for BI and analytics

Rule of thumb:
If Python is the center → ETL
If SQL is the center → ELT

--------------------------------------------------

REQUIREMENTS
------------
pandas
sqlalchemy
pymysql
jupyter
