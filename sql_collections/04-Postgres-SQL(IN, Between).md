# SQL-4-(In, BETWEEN)
# IN:
* The IN operator allows you to specify a list of possibles values in the WHERE clause.
* The IN operator is a shorthand for multiple OR conditions.
* Return all customers FROM 'Germany', 'France' or 'UK':
```sql
SELECT * FROM customers
WHERE country IN ('Germany', 'France', 'UK');
```
<img width="434" height="333" alt="image" src="https://github.com/user-attachments/assets/bb6dafe7-8506-4006-9ab5-d9a5e0d0b7fc" />

# NOT IN:
* By using the NOT keyword in front of the IN operator, you return all records that are NOT any of the values in the list.
* Return all customers that are NOT from 'Germany', 'France' or 'UK':
```sql
SELECT * FROM customers
WHERE country NOT IN ('Germany', 'France', 'UK');
```
<img width="430" height="388" alt="image" src="https://github.com/user-attachments/assets/a6829024-f8ff-4649-83d9-a52df7b6e8b1" />

# IN(SELECT):
* You can also use a SELECT statement inside the paranthesis to return all records that are in the result of the SELECT statement.
* Return all customers that have an order in the orders table:
```sql
SELECT * FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders);
```
<img width="433" height="399" alt="image" src="https://github.com/user-attachments/assets/2275810d-0519-45e4-be66-c29cff09db8d" />

# NOT IN(SELECT):
* The result in the example, above returned 89 records, that means that there are 2 customers that haven't placed any orders.
* Return all customers that have NOT placed any orders in the orders table:
```sql
SELECT * FROM customers
WHERE customer_id NOT IN (SELECT customer_id FROM orders);
```
<img width="437" height="102" alt="image" src="https://github.com/user-attachments/assets/35cb9e85-3134-43fe-ad5d-cd916ed86a22" />

# BETWEEN:
* The BETWEEN operator selects values within a given range. The values can be numbers, text or dates.
* The BETWEEN operator is inclusive: begin and end values are included.
* Select all products with a price between 10 and 15.
```sql
SELECT * FROM products
WHERE Price BETWEEN 100 AND 600;
```
<img width="130" height="173" alt="image" src="https://github.com/user-attachments/assets/5432b484-b00c-4628-9ac0-594088fd9393" />

# BETWEEN Text Values:
* The BETWEEN operator can also be used on text values.
* The result returns all records that are alphabetically between the specified values.
* Select all products between 'Pavlova' and 'Tofu':
```sql
SELECT * FROM products
WHERE product_name BETWEEN 'Pavlova' AND 'Tofu';
```
<img width="260" height="131" alt="image" src="https://github.com/user-attachments/assets/1c06a459-35c2-421a-bc45-c470f349b5dd" />

# BETWEEN Date Values:
* The BETWEEN operator can also be used on date values.
* Select all orders between 12th of April, 2023 and 5th of May, 2023:
```sql
SELECT * FROM orders
WHERE order_date BETWEEN '2023-04-12' AND '2023-05-05';
```
<img width="315" height="509" alt="image" src="https://github.com/user-attachments/assets/c084fb8d-a914-4f70-a2c8-70092d4e8094" />

# Aliases:
* SQL Aliases are used to give a table, or column in a table, a temporary name.
* Aliases are often used to make column names more readable.
* An alias only exists for the duration of that query.
* An alias is created with the 'AS' keyword.
* Using aliases for columns:
```sql
SELECT customer_id AS id
FROM customers;
```
<img width="117" height="279" alt="image" src="https://github.com/user-attachments/assets/d8b0b870-a7ce-4612-8f55-c1b92b35ff15" />

# AS is Optional,
* Acutally, you can skip the AS keyword and get the same result:
```sql
SELECT customer_id id
FROM customers;
```
<img width="117" height="280" alt="image" src="https://github.com/user-attachments/assets/7adffc86-cb69-43f1-a356-44fdfc85b83e" />

# Concatenate Columns:
* The AS keyword is often used when two or more fields are concatenated into one.
* The concatenate two fileds we use ||:
```sql
SELECT product_name || price AS product
FROM products;
```
<img width="163" height="285" alt="image" src="https://github.com/user-attachments/assets/799bf807-93b4-45be-9cde-20bd13b92e7a" />

# Using Aliases With a Space Character"
* If you want your alias to contain one or more spaces, like "My Great Products", surround your alias with double quotes.
```sql
SELECT product_name AS "My Great Products"
FROM products;
```
<img width="209" height="298" alt="image" src="https://github.com/user-attachments/assets/70024c5f-59c1-4b8d-922a-cda872f94f33" />

