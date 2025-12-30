# SQL-4-(In, BETWEEN)
* IN:
* The IN operator allows you to specify a list of possibles values in the WHERE clause.
* The IN operator is a shorthand for multiple OR conditions.
* Return all customers FROM 'Germany', 'France' or 'UK':
```sql
SELECT * FROM customers
WHERE country IN ('Germany', 'France', 'UK');
```
* NOT IN:
* By using the NOT keyword in front of the IN operator, you return all records that are NOT any of the values in the list.
* Return all customers that are NOT from 'Germany', 'France' or 'UK':
```sql
SELECT * FROM customers
WHERE country NOT IN ('Germany', 'France', 'UK');
```
* IN(SELECT):
* You can also use a SELECT statement inside the paranthesis to return all records that are in the result of the SELECT statement.
* Return all customers that have an order in the orders table:
```sql
SELECT * FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders);
```
* NOT IN(SELECT):
* The result in the example, above returned 89 records, that means that there are 2 customers that haven't placed any orders.
* Return all customers that have NOT placed any orders in the orders table:
```sql
SELECT * FROM customers
WHERE customer_id NOT IN (SELECT customer_id FROM orders);
```
* BETWEEN:
* The BETWEEN operator selects values within a given range. The values can be numbers, text or dates.
* The BETWEEN operator is inclusive: begin and end values are included.
* Select all products with a price between 10 and 15.
```sql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 15;
```
* BETWEEN Text Values:
* The BETWEEN operator can also be used on text values.
* The result returns all records that are alphabetically between the specified values.
* Select all products between 'Pavlova' and 'Tofu':
```sql
SELECT * FROM Products
WHERE product_name BETWEEN 'Pavlova' AND 'Tofu';
```
* BETWEEN Date Values:
* The BETWEEN operator can also be used on date values.
* Select all orders between 12th of April, 2023 and 5th of May, 2023:
```sql
SELECT * FROM orders
WHERE order_date BETWEEN '2023-04-12' AND '2023-05-05';
```
* Aliases:
* SQL Aliases are used to give a table, or column in a table, a temporary name.
* Aliases are often used to make column names more readable.
* An alias only exists for the duration of that query.
* An alias is created with the 'AS' keyword.
* Using aliases for columns:
```sql
SELECT customer_id AS id
FROM customers;
```
* AS is Optional,
* Acutally, you can skip the AS keyword and get the same result:
```sql
SELECT customer_id id
FROM customers;
```
* Concatenate Columns:
* The AS keyword is often used when two or more fields are concatenated into one.
* The concatenate two fileds we use ||:
```sql
SELECT product_name || unit AS product
FROM products;
```
* Using Aliases With a Space Character"
* If you want your alias to contain one or more spaces, like "My Great Products", surround your alias with double quotes.
```sql
SELECT product_name AS "My Great Products"
FROM products;
```
