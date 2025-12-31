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
```sql
select name, RANK() OVER(ORDER BY name) from fruits;
```
* DENSE_RANK Function:
* When using DENSE_RANK, the same rules apply as we described for RANK(), with one difference-when similar rows are detected, the next rank in line isn't skipped.
```sql
select name, DENSE_RANK() OVER(ORDER BY name) from fruits;
```
* Before we explore these SQL Rank functions, let's prepare sample data. In this sample data, we have exam results for three students in Maths, Science and English subjetcs.
```sql
CREATE TABLE ExamResult (StudentName VARCHAR(70), Subject VARCHAR(20), Marks INT);
INSERT INTO ExamResult VALUES ('Lily', 'Maths', 65);
INSERT INTO ExamResult VALUES ('Lily', 'Science', 80);
INSERT INTO ExamResult VALUES ('Lily', 'english', 70);
INSERT INTO ExamResult VALUES ('Isabella', 'Maths', 50);
INSERT INTO ExamResult VALUES ('Isabella', 'Science', 70);
INSERT INTO ExamResult VALUES ('Isabella', 'english', 90);
INSERT INTO ExamResult VALUES ('Olivia', 'Maths', 55);
INSERT INTO ExamResult VALUES ('Olivia', 'Science', 60);
INSERT INTO ExamResult VALUES ('Olivia', 'english', 89);
```
* Execute the following query to get a rowNum for students as per their marks.
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	ROW_NUMBER() OVER(ORDER BY Marks) RowNumber
FROM ExamResult;
```
* We can specify descending order with Order By clause, and it changes the RANK accordingly.
* RANK Order
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	ROW_NUMBER() OVER(ORDER BY Marks) RowNumber
FROM ExamResult;
```
* Check Rank 5 in Output:
* We use PARTITION BY Studentname clause to perform calculations on each student group.
* Each subset should get rank as per their Marks in descending order.
* The result set uses Order By clause to sort results on Studentname and their rank.
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	RANK() OVER(PARTITION BY Studentname ORDER BY Marks DESC) Rank
FROM ExamResult
ORDER BY Studentname,
     	Rank;
```
* DENSE_RANK and RANK Fucntion:
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	DENSE_RANK() OVER(ORDER BY Marks DESC) Rank
FROM ExamResult
ORDER BY Rank;
```
* Check Rank 4 and 5
* PARTITION BY:
```sql
Update Examresult set Marks = 70 where Studentname = 'Isabella' and Subject = 'Maths';
SELECT Studentname,
   	Subject,
   	Marks,
   	DENSE_RANK() OVER(PARTITION BY StudentName ORDER BY Marks ) Rank
FROM ExamResult
ORDER BY Studentname,
     	Rank;
```
* Check Rank 1 and 2
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	RANK() OVER(PARTITION BY StudentName ORDER BY Marks ) Rank
FROM ExamResult
ORDER BY Studentname,
     	Rank;
```
* Check Rank 3 and 4
* CTE (Common Table Expression)
```sql
with t1 as (
  SELECT Studentname,
   	Subject,
   	Marks,
   	RANK() OVER(PARTITION BY StudentName ORDER BY Marks ) Rank
FROM ExamResult
ORDER BY Studentname,
     	Rank
) 
select * from t1 where Rank=1
```
* Multiple CTE
```sql
with t1 as (
SELECT Studentname,
   	Subject,
   	Marks,
   	RANK() OVER(PARTITION BY StudentName ORDER BY Marks ) Rank
FROM ExamResult
ORDER BY Studentname,
     	Rank
)
, t2 as (select Studentname, Rank from t1)

select * from t2 where Rank=1
```
