# ETL Data Pipeline using AirFlow

## Project Overview

An ETL Data Pipelines Project that uses AirFlow DAGs to extract employees' data from PostgreSQL Schemas, load it in AWS Data Lake, transform it with Python scripts, and finally load it into a Snowflake Data warehouse using SCD type 2.

## Project Details

![New Project](https://github.com/Dina-Hosny/ETL-Data-Pipeline-using-AirFlow/assets/46838441/32769201-4ecb-487a-b999-bbed1a851c2b)

The idea of the project is to use AirFlow DAGs to extract employees' data from HR and Finance PostgreSQL schemas and load it into a Snowflake data warehouse to store it and maintain all salary change history.

The AirFlow DAG runs hourly to check and extract all new data from the PostgreSQL source, then load it into AWS S3 buckets used as a Data Lake containing all raw data as CSV files. After that, Python functions are applied to extract the new records for insertion and the records containing salary changes for updates. This performs the Slowly Changing Dimension (SCD) Type 2 concept to keep all historical employees' salary changes in the Snowflake Data warehouse.

## Project Steps

- 1- Implement an AirFlow DAG that runs hourly and uses the TaskFlow approach to pass the outputs from each task to another.

- 2- Implement two tasks that use the SqlToS3Operator operation to extract the data from PostgreSQL schemas to AWS S3 buckets in CSV file format. One task extracts HR data and the other extracts Finance Data.

- 3- Implement two tasks that perform Python functions on the extracted data to retrieve the IDs of new records to insert in the Data warehouse, and the IDs of records that contain salary changes to update them and insert new records with new values to apply the SCD type 2 concept.

- 4- Load the data into the Snowflake Data warehouse table.

- 5- The Airflow DAG contains Python functions using the BranchPythonOperator operation to check if there are new records to insert or records to update before running the task to avoid errors.

## Tools and Technologies

- Apache Airflow
- Python
- Pandas
- PostgreSQL
- Snowflake
- AWS S3
- ETL
- Data Warehouse Concepts
- SCD

## Project Files

- Dags: Contains the AirFlow Dag.
- Includes: Contains the SQL and Python scripts used in the AirFlow Dag.
- Output: Contains screenshots from the AirFlow Dag Output.

## Project Output

![Screenshot 2023-05-14 191951](https://github.com/Dina-Hosny/ETL-Data-Pipeline-using-AirFlow/assets/46838441/eee98f52-db18-4022-bce0-6c38fb7dadd2)

## Maintainer

Mohan Teja Nandamudi
Data Engineer
Email: mohanteja.0117@gmail.com
LinkedIn: https://www.linkedin.com/in/nmohant/

Mohan is a Data Engineer with over 6 years of experience building and optimizing enterprise data pipelines, cloud warehouses, and real-time ingestion frameworks across AWS, Snowflake, and Airflow environments. This project serves as a demonstration of implementing automated ETL workflows and SCD Type 2 logic in a modern data stack. Based on the original work by Dina Hosny, this repository is currently maintained to showcase best practices in data orchestration.