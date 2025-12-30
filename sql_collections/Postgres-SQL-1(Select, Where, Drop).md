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
