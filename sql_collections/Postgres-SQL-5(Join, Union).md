# SQL-5-(JOIN, UNION)
# JOIN
* A JOIN clause is used to combine rows from two or more tables, based on a related column between them.
* Different Types of JOINS in PostgresSQL:
  1. INNER JOIN: Returns records that have matching values in both tables.
  2. LEFT JOIN: Returns all records from the left table, and match records from the right table.
  3. RIGHT JOIN: Retuens all records from right table, and match records from the left table.
  4. FULL JOIN: Returns all records when there is a match in either left or right table. 
# INNER JOIN:
* The INNER JOIN keyword selects records that have matching values in both tables.
```sql
SELECT * FROM testproducts;
SELECT * FROM categories;
```
<img width="383" height="289" alt="image" src="https://github.com/user-attachments/assets/5ab31666-f54d-4010-a2b3-f8309b61922a" />
<img width="603" height="244" alt="image" src="https://github.com/user-attachments/assets/2c729ca2-bf8c-4176-87d8-3af3a125e2ee" />

* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
INNER JOIN categories ON testproducts.category_id = categories.category_id;
```
<img width="447" height="143" alt="image" src="https://github.com/user-attachments/assets/2e321ea9-4dd0-4bf3-8315-88d717bc030c" />

# LEFT JOIN:
* The LEFT JOIN keyword selects ALL records from the "left" table, and the matching records from the "right" table. The result is 0 records from the right side if there is no match.
* Note: Many of the products in testproducts have a category_id that does not match any of the categories in the categories table.
* By using LEFT JOIN we will get all the records from testproducts, even the ones with no match in the categories table:
* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
LEFT JOIN categories ON testproducts.category_id = categories.category_id;
```
<img width="458" height="285" alt="image" src="https://github.com/user-attachments/assets/aab96984-50f1-422b-ab63-fcc036c5fdc0" />

# RIGHT JOIN:
* The RIGHT JOIN keyword selects ALL records from the "right" table, and the matching records from the "left" table. The result is 0 records from the left side if there is no match.
* Note: many of the products in testproducts have a category_id that does not have any of the categories in the categories table.
* By using RIGHT JOIN we will get all records from categories, even the ones with no match in the testproducts table:
* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
RIGHT JOIN categories ON testproducts.category_id = categories.category_id;
```
<img width="463" height="244" alt="image" src="https://github.com/user-attachments/assets/e9694d52-777e-44b1-8907-933c530ccec7" />

# FULL JOIN:
* The FULL JOIN keyword selects ALL records from both tables, even if there is not a match. For rows with a match the values from both tables are available, if there is not a match, the empty fields will get the value NULL.
* Note: Many of the products in testproducts have a category_id that does not match any of the categories in the categories table.
* By using FULL JOIN we will get all records from both the categories table and the testproducts table:
* Join testproducts to categories using the category_id column:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
FULL JOIN categories ON testproducts.category_id = categories.category_id;
```
<img width="449" height="373" alt="image" src="https://github.com/user-attachments/assets/a75a7923-4d65-4f3a-a4fe-7753a9ac1d0c" />

# CROSS JOIN:
* The CROSS JOIN keyword matches ALL records from the "left" table with EACH record from the "right" table.
* That means that all records from the "right" table will be returned for each record in the "left" table.
* This way of joining can potentially return very large table, and you should not use it if you do not have to.
* Join testproducts to categories using the CROSS KOIN keyword:
```sql
SELECT testproduct_id, product_name, category_name
FROM testproducts
CROSS JOIN categories;
```
<img width="448" height="981" alt="image" src="https://github.com/user-attachments/assets/71162d43-daee-4542-a354-5bb538fa42e8" />
<img width="445" height="943" alt="image" src="https://github.com/user-attachments/assets/51f0a83e-eeee-432f-afbb-bc0ff16cd7db" />


# UNION:
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
<img width="292" height="521" alt="image" src="https://github.com/user-attachments/assets/61ce0e4d-2742-4442-9351-2450684d5b23" />

# UNION vs UNION ALL:
* With the UNION operator, if some rows in the two queries returns the exact same result, only one row will be listed, because UNION selects only distinct values.
* Use UNION ALL to return duplicate values.
* Let's make some changes to the queries, so that we have duplicate values in the result:
# UNION:
```sql
SELECT product_id
FROM products
UNION
SELECT testproduct_id
FROM testproducts
ORDER BY product_id;
```
<img width="137" height="288" alt="image" src="https://github.com/user-attachments/assets/e89dec83-7f2c-4fee-9e52-88da44f6633b" />

# UNION ALL:
```sql
SELECT product_id
FROM products
UNION ALL
SELECT testproduct_id
FROM testproducts
ORDER BY product_id;
```
<img width="138" height="519" alt="image" src="https://github.com/user-attachments/assets/d26bc56d-02ed-497d-834e-15b1af68e479" />

