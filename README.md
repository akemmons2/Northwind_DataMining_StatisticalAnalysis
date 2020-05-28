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

Data was extracted from PostgreSQL using the following query.

```SQL
 > SELECT A.order_id, A.order_date, A.shipped_date, A.freight, A.ship_name, 
 > A.ship_country, B.unit_price, B.quantity, B.discount, 
 > C.unit_price as unit_cost, C.quantity_per_unit as cost_quantity, 
 > C.product_id, C.product_name, C.supplier_id, C.category_id, 
 > D.category_name, D.description
 > FROM "Orders".orders A
 > 	LEFT JOIN "Orders".order_details B ON B.order_id = A.order_id
 > 	  LEFT JOIN "Orders".products C  on C.product_id = B.product_id
 > 	    LEFT JOIN "Orders".categories D on D.category_id = C.category_id
 > ORDER BY ship_country ASC
```
Calculations were performed in Excel, demonstrating Excel proficiency.

The following columns were added: products_per_order, cost_per_UOM, sale_price (unit_price * quantity), total_salesprice (sale_price - discount), total_cost, profit_loss (total_salesprice - total_cost) and calculations were performed using formulas.






