# SQL-5-(JOIN)
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
