# Northwind_DataMining_StatisticalAnalysis
## Project - database created in PostgreSQL, statistical analysis performed in SAS Studio and R

  Data mining is the process of taking a raw, large set of data and extracting usable data from it (The Economic Times, n.d.). To determine if the data is usable, it is evaluated for anomalies, patterns and correlations which are then used to predict outcomes. The Northwind data set contains sales data, it will be analyzed, and the following questions will be the groundwork for the statistical analysis.  Which product category produces the highest profitability? What countries purchase the most products? 

### Database Creation
 
 The Northwind Database was created and populated in PostgreSQL.
 ```SQL
 >  -- Database: Northwind
 >
 >  -- DROP DATABASE "Northwind";  
 >
 >CREATE DATABASE "Northwind"
 >  WITH 
 >  OWNER = postgres
 >  ENCODING = 'UTF8'
 >  LC_COLLATE = 'English_United States.1252'
 >  LC_CTYPE = 'English_United States.1252'
 >  TABLESPACE = pg_default
 >  CONNECTION LIMIT = -1;
```
Schemas were added to organize the database. 

![Schemas](https://user-images.githubusercontent.com/54143493/82932115-8b80e580-9f4d-11ea-98b8-024947435fd2.png)

 ### Orders
 ```SQL
 >-- SCHEMA: Orders
 >
 >-- DROP SCHEMA "Orders" ;
 >
 >CREATE SCHEMA "Orders"
 >   AUTHORIZATION postgres;
```
### Suppliers
```SQL
 >-- SCHEMA: Suppliers
 >
 >-- DROP SCHEMA "Suppliers" ;
 >
 >CREATE SCHEMA "Suppliers"
 >  AUTHORIZATION postgres;
```    
### Customers
```SQL
 >-- SCHEMA: customers
 >
 >-- DROP SCHEMA customers ;
 >
 >CREATE SCHEMA customers
 >  AUTHORIZATION postgres;
 ```
### Employees
```SQL
 >-- SCHEMA: employees
 >
 >-- DROP SCHEMA employees ;
 >
 >CREATE SCHEMA employees
 >  AUTHORIZATION postgres;
 ```
### Regions
```SQL
 >-- SCHEMA: regions
 >
 >-- DROP SCHEMA regions ;
 >
 >CREATE SCHEMA regions
 >    AUTHORIZATION postgres;
```
### Fact and Dimension Tables

![fact and dimension table](https://user-images.githubusercontent.com/54143493/82932212-ace1d180-9f4d-11ea-910d-2f383a0234c6.png)

```SQL
 >SELECT
 >  nspname AS schemaname, relname, rultuples
 >FROM pg_class C
 >LEFT JOIN pg_namespace N ON (N.oid = C.relnamespace)
 >WHERE
 >   nspname NOT IN ('pg_catalog', 'information_schema') AND relkind='r'
 >ORDER BY schemaname ASC;
```

## Mining & Extraction

  Part of the mining process is determining if the data you are using is suitable. Is the data structured? Structured data has columns and rows such as in Excel, CSV or a text file. “The less ETL (extraction, transformation and loading) an organization has to do before analysis, the faster it can start generating insights” (IDG Communications, Inc., 2020). The Northwind data set is structured, allowing us to move to the next step. 
  
 ![data analysis](https://user-images.githubusercontent.com/54143493/82938320-3c3fb280-9f57-11ea-8289-dbaaafc7c681.png)

References
IDG Communications, Inc. (2020). Creating data ecosystems and the requirements for a successful data exchange. Retrieved 05 08, 2020, from CIO: https://www.cio.com/article/3530335/creating-data-ecosystems-and-the-requirements-for-a-successful-data-exchange.html

SAS Institute Inc. (2018). localhost:10080. Retrieved from SAS Studio: http://localhost:10080/SASStudio/38/main?locale=en_US&zone=GMT-05%253A00&http%3A%2F%2Flocalhost%3A10080%2FSASStudio%2F38%2F=

The Economic Times. (n.d.). Definition of data mining. Retrieved 05 08, 2020, from The Economic Times: https://economictimes.indiatimes.com/definition/data-mining

