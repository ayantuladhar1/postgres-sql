# SQL-6-(GroupBY, Case, Exits)
# GROUP BY:
* The GROUP BY clause groups rows that have the same values into summary rows, like "find the number of customers in each country".
* The GROUP BY clause is often used with aggregated functions like COUNT(), MAX(), SUM(), AVG() to group the result-set by one or more columns.
* List the number of customers in each country.
```sql
SELECT COUNT(customer_id), country
FROM customers
GROUP BY country;
```
<img width="264" height="196" alt="image" src="https://github.com/user-attachments/assets/e711a293-ba0b-48ff-85a7-10db51b614ef" />

# GROUP BY with JOIN:
* The following SQL Statement lists the number of orders made by each customer:
```sql
SELECT customers.customer_name, COUNT(orders.order_id)
FROM orders
LEFT JOIN customers ON orders.customer_id = customers.customer_id
GROUP BY customer_name;
```
<img width="244" height="740" alt="image" src="https://github.com/user-attachments/assets/e226fe8c-715f-4c43-a8ee-1739618e8f47" />
<img width="247" height="703" alt="image" src="https://github.com/user-attachments/assets/f1b472a0-2e0b-4b0d-90b3-e8eca75abf81" />
<img width="249" height="445" alt="image" src="https://github.com/user-attachments/assets/5caf2172-e002-4075-81e7-f9cfc8bab851" />

# HAVING:
* The HAVING clause was added to SQL because the WHERE clause cannot be used with aggregate functions.
* Aggregate functions are often used with GROUP BY clauses, and by adding HAVING we can write conditions like we do with WHERE clauses.
* List only countries that are represented more than 5 times:
```sql
SELECT COUNT(customer_id), country
FROM customers
GROUP BY country
HAVING COUNT(customer_id) > 5;
```
<img width="254" height="186" alt="image" src="https://github.com/user-attachments/assets/bce7db1d-6398-4433-896f-c5f0df35e09d" />

# More HAVING Examples:
* The following SQL statement lists only orders with a total proce of $400 or more:
```sql
SELECT order_details.order_id, SUM(products.price)
FROM order_details
LEFT JOIN products ON order_details.product_id = products.product_id
GROUP BY order_id
HAVING SUM(products.price) > 400.00;
```
<img width="185" height="195" alt="image" src="https://github.com/user-attachments/assets/581529aa-5e27-4eb5-baf0-d4d0198a5972" />

# CASE:
* The CASE expression goes through conditions and returns a value when the first condition is met (like an if-then-else statement).
* Once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.
* If there is no ELSE part and no conditions are true, it returns NULL.
```sql
SELECT product_name,
CASE
  WHEN price < 10 THEN 'Low price product'
  WHEN price > 50 THEN 'High price product'
ELSE
  'Normal product'
END
FROM products;
```
<img width="318" height="289" alt="image" src="https://github.com/user-attachments/assets/3b8a7154-8b8a-431a-8876-bf30b4c3bdbd" />

# CASE With ALIAS:
* When a column name is not specified for the "case" field, the parser uses case as the column name.
* To specify a column name, add an alias after the END keyword.
```sql
SELECT product_name,
CASE
  WHEN price < 10 THEN 'Low price product'
  WHEN price > 50 THEN 'High price product'
ELSE
  'Normal product'
END AS "price category"
FROM products;
```
<img width="314" height="284" alt="image" src="https://github.com/user-attachments/assets/b6034bd0-6d1c-469b-bf0a-b82e2eab223d" />

# EXISTS:
* The EXISTS operator is used to test for the existence of any record in a sub query.
* The EXISTS operator retuens TRUE if the sub query retuens one or more records.
* Return all customers that is represented in the orders table:
```sql
SELECT customers.customer_name
FROM customers
WHERE EXISTS (
  SELECT order_id
  FROM orders
  WHERE customer_id = customers.customer_id
);
```
<img width="195" height="908" alt="image" src="https://github.com/user-attachments/assets/5f3233f2-e461-4920-8b56-fe7cccda6893" />
<img width="191" height="983" alt="image" src="https://github.com/user-attachments/assets/f6c316a4-7f6b-43a7-ab17-0742714f4b8e" />

# NOT EXISTS:
* To check which customers that do not have any orders, we can use the NOT operator together with the EXISTS operator:
* Return all customers that is NOT represented in the orders table:
```sql
SELECT customers.customer_name
FROM customers
WHERE NOT EXISTS (
  SELECT order_id
  FROM orders
  WHERE customer_id = customers.customer_id
);
```
<img width="206" height="96" alt="image" src="https://github.com/user-attachments/assets/aa1af67f-70d0-486c-9c62-b2d2a8abf2f5" />

# ANY
* The ANY operator allows you to perform a comparison between a single column value and a range of other values.
* The ANY operator:
* 1. Returns a Boolean value as a result
* 2. Returns TRUE if ANY of the sub query values meet the condition
* ANY means that the condition will be true if the operation is true for any of the values in the range.
* List the products that ANY records in the order_details table with a quantity larger than 120:
```sql
SELECT product_name
FROM products
WHERE product_id = ANY (
  SELECT product_id
  FROM order_details
  WHERE quantity > 12
);
```
<img width="200" height="137" alt="image" src="https://github.com/user-attachments/assets/f7327b96-b416-4e70-9546-42dd17d39476" />

