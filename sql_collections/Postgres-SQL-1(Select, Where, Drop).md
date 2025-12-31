# SQL-1-(SELECT, WHERE, DROP)
# DB name: practice
```sql
CREATE TABLE cars (
  brand VARCHAR(255),
  model VARCHAR(255),
  year INT
);

INSERT INTO cars (brand, model, year)
VALUES ('Ford', 'Mustang', 1985);

SELECT * FROM cars;
```
<img width="396" height="65" alt="image" src="https://github.com/user-attachments/assets/82feeb26-b47b-47a0-85e4-b2a1a8362efe" />

# Specify the columns
```sql
SELECT brand, year FROM cars;
```
<img width="330" height="73" alt="image" src="https://github.com/user-attachments/assets/e754cfef-0d05-4b8a-96be-1bbc2834f9d4" />


# Alter Table Statement, add a column name color:
```sql
ALTER TABLE cars ADD color VARCHAR(255);
```
# Update Statement:
```sql
UPDATE cars SET color = 'red' WHERE brand = 'Mazda';
SELECT * FROM cars;
SET color = 'red'
WHERE brand = 'Ford';
```
<img width="544" height="190" alt="image" src="https://github.com/user-attachments/assets/39b72c6c-7e03-4e12-a6e0-4a11408ee098" />

# Drop column, removes the color column:
```sql
ALTER TABLE cars
DROP COLUMN color;
```
<img width="415" height="192" alt="image" src="https://github.com/user-attachments/assets/818f2832-ea0d-475f-97fa-4f8d361ccaa9" />

# Delete Statement,
* Delete entire rows if WHERE not specified, keeps the table sturcture but data is gone.
* Deletes all records where brand is 'Volvo':
```sql
DELETE FROM cars;
```
# OR
```sql
DELETE FROM cars
WHERE brand = 'Ford';
```
<img width="424" height="167" alt="image" src="https://github.com/user-attachments/assets/0c0c72f8-d470-4dc6-8726-395f220c6e73" />

# Drop Table Statement, Delete the cars table:
* Table is completly gone
* Instant Speed
```sql
DROP TABLE cars;
```
# Alter Column Statement, Change the column type:
```sql
ALTER TABLE cars
ALTER COLUMN year TYPE VARCHAR(4);
```
<img width="465" height="52" alt="image" src="https://github.com/user-attachments/assets/b103eedb-bff1-4779-bad2-1cd456e8879e" />

* Truncate Statement, Removes all rows fast but keeps table structure:
* WHERE clause is not allowed.
```sql
TRUNCATE TABLE cars;
```
