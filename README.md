#Sparkify Airflow Data Pipeline

Data Pipelines with Airflow

**Overview**:

This project builds a data pipeline for Sparkify using Apache Airflow that automates and monitors the 
running of an ETL pipeline.

The ETL loads song and log data in JSON format from S3 and processes the data into analytics tables in a 
star schema on Reshift. A star schema has been used to allow the Sparkify team to readily run queries to 
analyze user activity on their app. Airflow regularly schedules this ETL and monitors its success by running 
a data quality check.

**Contents**:


<ol>
    <li> 
    sql_queries.py contains the SQL queries used in the ETL process. It should be placed in the plugins/helpers directory of your Airflow installation.
    </li>
    <li>
        create_tables.sql contains the SQL queries used to create all the required tables in Redshift. It should be placed in the dags directory of your Airflow installation.
    </li>
    <li>
        udac_example_dag.py contains the tasks and dependencies of the DAG. It should be placed in the dags directory of your Airflow installation.
    </li>
    <li>
        stage_redshift.py contains StageToRedshiftOperator, which copies JSON data from S3 to staging tables in the Redshift data warehouse.
    </li>
    <li>
        load_dimension.py contains LoadDimensionOperator, which loads a dimension table from data in the staging table(s).
    </li>
    <li>
        load_fact.py contains LoadFactOperator, which loads a fact table from data in the staging table(s).
    </li>
    <li>
        data_quality.py contains DataQualityOperator, which runs a data quality check by passing an SQL query and expected result as arguments, failing if the results don't match.
Configuration
    </li>
</ol>

Make sure to add the following Airflow connections:
<ul>
    <li>AWS credentials</li>
    <li>Connection to Postgres database</li>
</ul>