# SQL-3-(Like)
# LIKE:
* The like operator is used in a WHERE clause to search for a specified pattern in a column.
* There are two wildcards often used in conjuntion with the LIKE operator.
*     % The percent sign represents zero, one, or multiple characters.
*     _ The underscore sign represents one, single character.
# Starts with:
* To return records that start with a specific letter or phrase, add the % at the end of the letter or phrase.
* Return all customers with a name that contains the letter 'A':
```sql
SELECT * FROM customers
WHERE customer_name LIKE 'A%';
```
<img width="447" height="265" alt="image" src="https://github.com/user-attachments/assets/2b56c050-5c17-4815-bf74-24bbc7a65f3a" />

# Contains:
* To return records that contain a specific letter of phrase, add the % both before and after the letter or phrase.
* Return all customers with a name that contains the letter 'A':
```sql
SELECT * FROM customers
WHERE customer_name LIKE '%A%';
```
<img width="434" height="311" alt="image" src="https://github.com/user-attachments/assets/23ba729d-1d0d-4a37-8185-825c2e6787ec" />

# ILIKE:
* Note: The LIKE operator is case sensitive, if you want to do a case insensitive search, use the ILIKE operator instead.
* Return all customers with a name that contains the letter 'A' or 'a':
```sql
SELECT * FROM customers
WHERE customer_name ILIKE '%A%';
```
<img width="435" height="317" alt="image" src="https://github.com/user-attachments/assets/16476c97-041a-4cf7-8c23-e8732252e5cc" />

# Ends with:
* To return records that end with a specified letter of phrase, add the % before the letter or phrase.
* Return all customers with a name that ends with the phrase 'en':
```sql
SELECT * FROM customers
WHERE customer_name LIKE '%en';
```
<img width="438" height="97" alt="image" src="https://github.com/user-attachments/assets/e5a8f39b-baad-49c2-a659-902aa6af6537" />

# The Underscore _ WildCard
* The _ wildcard represents a single character.
* It can be any character or number, but each _ represents one, and only one character.
* Return all customers from a city that starts with 'L' followed by one wildcard character, then 'nd' and then two wildcard caharcters:
```sql
SELECT * FROM customers
WHERE country LIKE 'L_nd__';
```
<img width="438" height="407" alt="image" src="https://github.com/user-attachments/assets/52d07368-5bfe-44d4-90eb-e6a5a40cc80e" />
