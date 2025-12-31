# SQL-6-(GroupBY, Case, Exits)
* GROUP BY:
* The GROUP BY clause groups rows that have the same values into summary rows, like "find the number of customers in each country".
* The GROUP BY clause is often used with aggregated functions like COUNT(), MAX(), SUM(), AVG() to group the result-set by one or more columns.
* List the number of customers in each country.
```sql
SELECT COUNT(customer_id), country
FROM customers
GROUP BY country;
```
* GROUP BY with JOIN:
* The following SQL Statement lists the number of orders made by each customer:
```sql
SELECT customers.customer_name, COUNT(orders.order_id)
FROM orders
LEFT JOIN customers ON orders.customer_id = customers.customer_id
GROUP BY customer_name;
```
* HAVING:
* The HAVING clause was added to SQL because the WHERE clause cannot be used with aggregate functions.
* Aggregate functions are often used with GROUP BY clauses, and by adding HAVING we can write conditions like we do with WHERE clauses.
* List only countries that are represented more than 5 times:
```sql
SELECT COUNT(customer_id), country
FROM customers
GROUP BY country
HAVING COUNT(customer_id) > 5;
```
* More HAVING Examples:
* The following SQL statement lists only orders with a total proce of $400 or more:
```sql
SELECT order_details.order_id, SUM(products.price)
FROM order_details
LEFT JOIN products ON order_details.product_id = products.product_id
GROUP BY order_id
HAVING SUM(products.price) > 400.00;
```
* CASE:
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
* CASE With ALIAS:
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
* EXISTS:
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
* NOT EXISTS:
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
* ANY
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
  WHERE quantity > 120
);
``` 
