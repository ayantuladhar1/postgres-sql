# SQL-5-(JOIN, UNION)
* JOIN
* A JOIN clause is used to combine rows from two or more tables, based on a related column between them.
* Different Types of JOINS in PostgresSQL:
  1. INNER JOIN: Returns records that have matching values in both tables.
  2. LEFT JOIN: Returns all records from the left table, and match records from the right table.
  3. RIGHT JOIN: Retuens all records from right table, and match records from the left table.
  4. FULL JOIN: Returns all records when there is a match in either left or right table. 
* INNER JOIN:
* The INNER JOIN keyword selects records that have matching values in both tables.
```sql
select * from testproducts
select * from categories
```
* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
INNER JOIN categories ON testproducts.category_id = categories.category_id;
```
* LEFT JOIN:
* The LEFT JOIN keyword selects ALL records from the "left" table, and the matching records from the "right" table. The result is 0 records from the right side if there is no match.
* Note: Many of the products in testproducts have a category_id that does not match any of the categories in the categories table.
* By using LEFT JOIN we will get all the records from testproducts, even the ones with no match in the categories table:
* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
LEFT JOIN categories ON testproducts.category_id = categories.category_id;
```
* RIGHT JOIN:
* The RIGHT JOIN keyword selects ALL records from the "right" table, and the matching records from the "left" table. The result is 0 records from the left side if there is no match.
* Note: many of the products in testproducts have a category_id that does not have any of the categories in the categories table.
* By using RIGHT JOIN we will get all records from categories, even the ones with no match in the testproducts table:
* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
RIGHT JOIN categories ON testproducts.category_id = categories.category_id;
```
* FULL JOIN:
* The FULL JOIN keyword selects ALL records from both tables, even if there is not a match. For rows with a match the values from both tables are available, if there is not a match, the empty fields will get the value NULL.
* Note: Many of the products in testproducts have a category_id that does not match any of the categories in the categories table.
* By using FULL JOIN we will get all records from both the categories table and the testproducts table:
* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
FULL JOIN categories ON testproducts.category_id = categories.category_id;
```
* CROSS JOIN:
* The CROSS JOIN keyword matches ALL records from the "left" table with EACH record from the "right" table.
* That means that all records from the "right" table will be returned for each record in the "left" table.
* This way of joining can potentially return very large table, and you should not use it if you do not have to.
* Join testproducts to categories using the CROSS KOIN keyword:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
CROSS JOIN categories
```
* UNION:
* The UNION operaator is used to combine the result-set of two or more queries.
* The queries in the union must follow these rules:
* 1. They must have the same number of columns.
* 2. The columns must have the same data types.
* 3. The columns must be in the same order.
* Combine products and testproducts using UNION operator:
```sql
SELECT product_id, product_name
FROM products
UNION
SELECT testproduct_id, product_name
FROM testproducts
ORDER BY product_id;
```
* UNION vs UNION ALL:
* With the UNION operator, if some rows in the two queries returns the exact same result, only one row will be listed, because UNION selects only distinct values.
* Use UNION ALL to return duplicate values.
* Let's make some changes to the queries, so that we have duplicate values in the result:
* UNION:
```sql
SELECT product_id
FROM products
UNION
SELECT testproduct_id
FROM testproducts
ORDER BY product_id;
```
* UNION ALL:
```sql
SELECT product_id
FROM products
UNION ALL
SELECT testproduct_id
FROM testproducts
ORDER BY product_id;
```
