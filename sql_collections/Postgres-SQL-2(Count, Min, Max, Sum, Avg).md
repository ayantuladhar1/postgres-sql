# SQL-2-(Count, Min, Max, Sun, Avg)
* Select colunn names:
```sql
SELECT customer_name, country FROM customers;
```
* Select Distinct Values from the column(country) in customer table:
```sql
SELECT DISTINCT country FROM customers;
```
* To return the number of different countries there are in the customers table:
```sql
SELECT COUNT(DISTINCT country) FROM customers;
```
* Filter Records:
* The WHERE clause is used to filter records.
* It is used to extract only those records that fulfil a specified condition.
* If we want to return only the records where city is London, we can specify that in the WHERE clause:
```sql
SELECT * FROM customers
WHERE city = 'London';
```
* Sort Data:
* The ORDER BY Keyword is used to sort the result in ascending or descending order.
* The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
* Sort the table by year:
```sql
SELECT * FROM products
ORDER BY price;
```
* DESC:
* The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
* Sort the table by year, in descending order:
```sql
SELECT * FROM products
ORDER BY price DESC;
```
* The LIMIT clause:
* The LIMIT clause is used to limit the maximum number of records to return.
* Return only the 20 first records from the customer table:
```sql
SELECT * FROM customers
LIMIT 20;
```
* The OFFSET Clause:
* The OFFSET clause is used to specify where to start selecting the records to return.
* If you want to retuen 20 records, but start at number 40, we can use both LIMIT and OFFSET.
* Note: The first record is number 0, so when you specify OFFSET 40 it means starting at record number 41.
* Return 20 records, starting from the 41th record:
```sql
SELECT * FROM customers
LIMIT 20 OFFSET 40;
```
* MIN:
* The MIN() function returns the smallest value of the selected column.
* Return the lowest price in the products table:
```sql
SELECT MIN(price)
FROM products;
```
* MAX:
* The MAX() function returns the largest value of the selected column.
* Return the highest price in the products table:
```sql
SELECT MAX(price)
FROM products;
```
* Set Column Name:
* When you use MIN() and MAX(), the returned column will be named min or max by default. To give the column a new name, use the AS keyword.
* Return the lowest price, and name the column lowest_price:
```sql
SELECT MIN(price) AS lowest_price
FROM products
```
* COUNT:
* The COUNT() function returns the number if rows that matches a specified criterion.
* If the specified criterion is a column name, the COUNT() function returns the number of columns with that name.
* Return the number of customers from the customers table:
```sql
SELECT COUNT(customer_id)
FROM customers;
```
* Note: NULL Values are not counted
* By specifying a WHERE clause, you e.g. return the number of customers that comes from London:
* Return the number of customers from London:
```sql
SELECT COUNT(customer_id)
FROM customers
WHERE city = 'London';
```
* SUM
* The SUM() function returns the total sum of a numeric column.
* The following SQL statement finds the sum of the quantity fields in the order_details table:
* Return the total amount of ordered items:
```sql
SELECT SUM(quantity)
FROM order_details
```
* NOTE: NULL Values are ignored
* AVG
* The AVG() function returns the average value of a numeric column.
* Return the average price of all the products in the products table:
```sql
SELECT AVG(price)
FROM products;
```
* NOTE: NULL Values are ignored
* With 2 Decimals:
* The above example returns the average price of all products, the result was 28.866363636363636364.
* We can use the ::NUMERIC operator to round the average price to a number with 2 decimals:
* Return the average price of all the products, rounded to 2 decimals:
```sql
SELECT AVG(price)::NUMERIC(10,2)
FROM products;
```
