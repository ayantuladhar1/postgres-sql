# Create DB name and Table:
* DB name: practice
```sql
CREATE TABLE cars (
  brand VARCHAR(255),
  model VARCHAR(255),
  year INT
);

INSERT INTO cars (brand, model, year)
VALUES ('Ford', 'Mustang', 1964);

SELECT * FROM cars;
```
* Specify the columns
```sql
SELECT brand, year FROM cars;
```
* Alter Table Statement, add a column name color:
```sql
ALTER TABLE cars ADD color VARCHAR(255);
```
* Update Statement:
```sql
UPDATE cars SET color = 'red' WHERE brand = 'Volvo';
SELECT * FROM cars;
SET color = 'red'
WHERE brand = 'Ford';
```
* Drop column, removes the color column:
```sql
ALTER TABLE cars
DROP COLUMN color;
```
* Delete Statement, Deletes all records where brand is 'Volvo':
```sql
DELETE FROM cars
WHERE brand = 'Volvo';
```
* Drop Table Statement, Delete the cars table:
```sql
DROP TABLE cars;
```
* Alter Column Statement, Change the column type:
```sql
ALTER TABLE cars
ALTER COLUMN year TYPE VARCHAR(4);
```
* Select Statement, To select from cars table:
```sql
SELECT * FROM cars;
```
