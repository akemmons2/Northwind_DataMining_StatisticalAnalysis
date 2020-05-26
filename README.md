# Northwind_DataMining_StatisticalAnalysis
## Project - database created in PostgreSQL, statistical analysis performed in SAS Studio and R

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

  
 ![data analysis](https://user-images.githubusercontent.com/54143493/82938320-3c3fb280-9f57-11ea-8289-dbaaafc7c681.png)

