# SQL-2-(Count, Min, Max, Sun, Avg)
# Create Tables:
```sql
CREATE TABLE customers (customer_name VARCHAR(255), customer_id int, country VARCHAR(255));
CREATE TABLE products (price int);
CREATE TABLE order_details (quantity int);
```
# Select colunn names:
```sql
SELECT customer_name, country FROM customers;
```
<img width="347" height="167" alt="image" src="https://github.com/user-attachments/assets/4ffefdc3-ccb4-4d25-b369-ae4538f4596f" />

# Select Distinct Values from the column(country) in customer table:
```sql
SELECT DISTINCT country FROM customers;
```
<img width="204" height="124" alt="image" src="https://github.com/user-attachments/assets/4008b98a-30a8-4c05-8284-e98462603335" />

# To return the number of different countries there are in the customers table:
```sql
SELECT COUNT(DISTINCT country) FROM customers;
```
<img width="117" height="80" alt="image" src="https://github.com/user-attachments/assets/92553b9b-b12f-453a-a247-0fa87772d76a" />

# Filter Records:
* The WHERE clause is used to filter records.
* It is used to extract only those records that fulfil a specified condition.
* If we want to return only the records where city is London, we can specify that in the
# WHERE clause:
```sql
SELECT * FROM customers
WHERE country = 'London';
```
<img width="435" height="95" alt="image" src="https://github.com/user-attachments/assets/d643bddd-ba11-49ad-bfd6-1e2d622aa637" />

# Sort Data:
* The ORDER BY Keyword is used to sort the result in ascending or descending order.
* The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
* Sort the table by year:
```sql
SELECT * FROM products
ORDER BY price;
```
<img width="115" height="278" alt="image" src="https://github.com/user-attachments/assets/cad817d9-188c-4ba9-8055-0d5c8cbdb981" />

# DESC:
* The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.
* Sort the table by year, in descending order:
```sql
SELECT * FROM products
ORDER BY price DESC;
```
<img width="120" height="284" alt="image" src="https://github.com/user-attachments/assets/e93d7771-d0d3-496f-8962-7a1b983d7e9f" />

# The LIMIT clause:
* The LIMIT clause is used to limit the maximum number of records to return.
* Return only the 20 first records from the customer table:
```sql
SELECT * FROM customers
LIMIT 20;
```
# The OFFSET Clause:
* The OFFSET clause is used to specify where to start selecting the records to return.
* If you want to retuen 20 records, but start at number 40, we can use both LIMIT and OFFSET.
* Note: The first record is number 0, so when you specify OFFSET 40 it means starting at record number 41.
* Return 20 records, starting from the 41th record:
```sql
SELECT * FROM customers
LIMIT 20 OFFSET 40;
```
<img width="439" height="522" alt="image" src="https://github.com/user-attachments/assets/a6f87cc9-3d7b-4148-9a34-c1662520a49b" />

# MIN:
* The MIN() function returns the smallest value of the selected column.
* Return the lowest price in the products table:
```sql
SELECT MIN(price)
FROM products;
```
<img width="119" height="73" alt="image" src="https://github.com/user-attachments/assets/819609d3-85d4-43a1-8f23-ef7051d27349" />

# MAX:
* The MAX() function returns the largest value of the selected column.
* Return the highest price in the products table:
```sql
SELECT MAX(price)
FROM products;
```
<img width="118" height="78" alt="image" src="https://github.com/user-attachments/assets/dcd9dd6f-34ec-48f6-bfe7-7211b6062a39" />

# Set Column Name:
* When you use MIN() and MAX(), the returned column will be named min or max by default. To give the column a new name, use the AS keyword.
* Return the lowest price, and name the column lowest_price:
```sql
SELECT MIN(price) AS lowest_price
FROM products;
```
<img width="152" height="73" alt="image" src="https://github.com/user-attachments/assets/8f6336a4-9365-40f6-91da-1e31254b7ccf" />

# COUNT:
* The COUNT() function returns the number if rows that matches a specified criterion.
* If the specified criterion is a column name, the COUNT() function returns the number of columns with that name.
* Return the number of customers from the customers table:
```sql
SELECT COUNT(customer_id)
FROM customers;
```
<img width="117" height="86" alt="image" src="https://github.com/user-attachments/assets/208ed796-b466-456f-a924-091038620930" />

* Note: NULL Values are not counted
* By specifying a WHERE clause, you e.g. return the number of customers that comes from London:
* Return the number of customers from London:
```sql
SELECT COUNT(customer_id)
FROM customers
WHERE country = 'London';
```
<img width="120" height="83" alt="image" src="https://github.com/user-attachments/assets/53f66433-7d9e-435a-a579-f4bc7178e40e" />

# SUM
* The SUM() function returns the total sum of a numeric column.
* The following SQL statement finds the sum of the quantity fields in the order_details table:
* Return the total amount of ordered items:
```sql
SELECT SUM(quantity)
FROM order_details;
```
<img width="118" height="73" alt="image" src="https://github.com/user-attachments/assets/618a7c69-c4b8-446c-9c62-66c5b49a0d0b" />

* NOTE: NULL Values are ignored
# AVG
* The AVG() function returns the average value of a numeric column.
* Return the average price of all the products in the products table:
```sql
SELECT AVG(price)
FROM products;
```
<img width="196" height="75" alt="image" src="https://github.com/user-attachments/assets/9223b8f8-946a-402f-8e46-4d8efc767a2c" />

* NOTE: NULL Values are ignored
# With 2 Decimals:
* The above example returns the average price of all products, the result was 552.90000000000000000000
* We can use the ::NUMERIC operator to round the average price to a number with 2 decimals:
* Return the average price of all the products, rounded to 2 decimals:
```sql
SELECT AVG(price)::NUMERIC(10,2)
FROM products;
```
<img width="163" height="82" alt="image" src="https://github.com/user-attachments/assets/66188126-22d0-4d3b-853c-81f6df99498d" />

