---
duration: 1h
---

# Lab: Introduction to NiFi Objectives

- Build an ETL pipeline with the NiFi ui

## Tasks

1. Set up the environment (Medium)
2. Configuration of Postgres database (Medium)
3. Build the flow (Medium)

## 1. Set up the environment

**NOTE: If you have finished the 01.nifi-dataflow lab, you may remove the `nifi` section in the [docker compose file](./lab-resource/compose.yaml)**

Finish the yaml file with the customized value before moving on to the next step.

1. Go to the lab-resource directory to run the containers.

   ```bash
   cd lab-resource
   docker compose up -d
   ```

2. You will need the following .jar file in NiFi container for accessing the Postgres database, so do the following command in the directory that you have mounted between your local file system and the contianer. Go into the container to get the resource into "/opt/nifi/nifi-current/lib/" folder

   ```bash
   docker exec -it nifi-ece-2025 /bin/bash
   ```

   ```bash
   # inside the container
   wget https://repo1.maven.org/maven2/org/postgresql/postgresql/42.2.24/postgresql-42.2.24.jar \
   -O /opt/nifi/nifi-current/lib/postgresql-42.2.24.jar
   chmod 664 /opt/nifi/nifi-current/lib/postgresql-42.2.24.jar
   exit
   ```

3. Restart the container

   ```bash
   docker restart nifi-ece-2025
   ```

## 2. Configuration of Postgres database

Get into Postgres container:

```bash
docker exec -it postgres-16 /bin/bash
```

Inside the container, do the following command to launch a Postgres shell:

```bash
psql -U <postgres username> -d ece_db
```

Create a target table for the data ingestion. Note that the table will depends the transformation process of the pipeline. 

   <details>
      <summary>
      Hint: Here is one of the example to create a Postgres table.</summary>

      ```bash
      CREATE TABLE wine_data (
         fixed_acidity FLOAT,
         volatile_acidity FLOAT,
         citric_acid FLOAT,
         residual_sugar FLOAT,
         chlorides FLOAT,
         free_sulfur_dioxide FLOAT,
         total_sulfur_dioxide FLOAT,
         density FLOAT,
         pH FLOAT,
         sulphates FLOAT,
         alcohol FLOAT,
         quality FLOAT,
         acidity_combination FLOAT
      );
      ```
   </details>


Check if your table is created successfully:

```
\d
\d wine_data
```

## 3. build a flow

1. Use "InvokeHTTP" processor to get the raw data csv file:
http://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv

   Note: try to have a more pleasant filename by tuning the "Response FlowFile Naming Strategy" property of the processor.

2. Use at least one "UpdateRecord" processor to do basic transformation with the FlowFile.

   For example, you could use 2 "UpdateRecord" processors to create a new column with the summation of the existed 2 columns.

3. Use PutDatabaseRecord processor to write the data to Postgres database.

   <details>
      <summary>
      Hint: try to do the configuration yourself before opening this block</summary>

      #### configuration of processor "PutDatabaseRecord"

      - Record Reader: CSVReader
      - Statement Type: INSERT
      - Database Connection Pooling Service: DBCPConnectionPool
      - Table Name: \<table name>  


      #### and in the controller of "DBCPConnectionPool"

      - Database Connection URL: "jdbc:postgresql://\<ip addr of the container>:5432/ece_db"
      - Database Driver Class Name: org.postgresql.Driver
      - Database User: \<postgres username>
      - Password: \<postgres password>

   </details>

## Reference

[NiFi Expression Language Guide](https://nifi.apache.org/docs/nifi-docs/html/expression-language-guide.html)
