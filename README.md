# etl_data_transformation

=> This PySpark notebook performs data transformations on raw bike sales data stored in Azure Blob Storage. It merges data from nine CSV files into two main tables:
Sales Table
Production Table

=> The notebook addresses data consistency and accuracy by:
Uploading raw data files to the raw_data/OLTP directory in Azure Blob Storage.
Setting up a new Azure Databricks account named bike-business-db with a 14 GB RAM, 4-core virtual machine.
Creating a new notebook named bike_sales_transformation to perform PySpark transformations.

=> Prerequisites:
An Azure Databricks account with a cluster configured.
Access to the raw data files in Azure Blob Storage.
Familiarity with PySpark basics (DataFrames, transformations, operations).


Steps:
-> Import Libraries: Import necessary PySpark libraries like pyspark.sql.SparkSession to create Spark sessions and manipulate DataFrames.
-> Create SparkSession: Create a SparkSession object to interact with Spark and access the data stored in Azure Blob Storage.
-> Define Data Paths: Specify the paths to the raw data files in the raw_data/OLTP directory.
-> Read CSV Data: Read each CSV file using spark.read.csv into separate DataFrames, setting appropriate options like header (header=True) and schema if known (schema=<schema_definition>) for efficiency.
-> Data Type Conversion: Apply transformations to ensure consistent data types across columns. Use functions like cast to convert data types (e.g., df = df.withColumn("column_name", df["column_name"].cast("dataType"))).
-> Left Join DataFrames: Perform left joins on relevant columns to merge data from multiple DataFrames into the two main tables: Sales and Production. Use methods like df1.join(df2, on="join_column", how="left") to combine data.
-> Write Transformed Data: Write the resulting Sales and Production DataFrames back to Azure Blob Storage (or other data stores) using methods like df.write.parquet("path/to/save/data") or df.write.format("csv").option("header", True).save("path/to/save/csv") depending on your desired format.

Data Source Link:- 
https://www.kaggle.com/datasets/dillonmyrick/bike-store-sample-database
