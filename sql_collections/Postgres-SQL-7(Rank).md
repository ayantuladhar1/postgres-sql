# SQL-7-(Rank)
* Create Table and Insert Values:
```sql
CREATE TABLE fruits(name varchar(255));
INSERT INTO fruits values('apple'),('apple'),('orange'),
 ('grapes'),('grapes'),('watermelon');
```
* ROW_NUMBER Function:
* This is the simplest of all to understand. This function will just rank all selected rows in an ascending order, regardless of the values that were selected.
```sql
select name, ROW_NUMBER() OVER(ORDER BY name) from fruits;
```
* RANK Function:
* This function is very similar to the ROW_NUMBER() function. The only difference is that identical rows are marked with the same rank. Also, please note that if the function skipped a number while ranking (because of row similarity), that rank will be skipped.
* 
