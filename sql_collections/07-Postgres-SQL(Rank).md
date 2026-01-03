# SQL-7-(Rank)
# Create Table and Insert Values:
```sql
CREATE TABLE fruits(name varchar(255));
INSERT INTO fruits values('apple'),('apple'),('orange'),
 ('grapes'),('grapes'),('watermelon');
```
<img width="208" height="187" alt="image" src="https://github.com/user-attachments/assets/11380a95-a888-4e9f-9ba1-e30ae8f3a590" />

# ROW_NUMBER Function:
* This is the simplest of all to understand. This function will just rank all selected rows in an ascending order, regardless of the values that were selected.
```sql
SELECT name, ROW_NUMBER() OVER(ORDER BY name) from fruits;
```
<img width="288" height="188" alt="image" src="https://github.com/user-attachments/assets/ffcefd76-aec0-4f9b-99d4-83e8df818010" />

# RANK Function:
* This function is very similar to the ROW_NUMBER() function. The only difference is that identical rows are marked with the same rank. Also, please note that if the function skipped a number while ranking (because of row similarity), that rank will be skipped.
```sql
SELECT name, RANK() OVER(ORDER BY name) from fruits;
```
<img width="256" height="184" alt="image" src="https://github.com/user-attachments/assets/0dba38c1-6cec-4108-a3ac-d5f4140075b6" />

# DENSE_RANK Function:
* When using DENSE_RANK, the same rules apply as we described for RANK(), with one difference-when similar rows are detected, the next rank in line isn't skipped.
```sql
SELECT name, DENSE_RANK() OVER(ORDER BY name) from fruits;
```
<img width="291" height="187" alt="image" src="https://github.com/user-attachments/assets/68197c8e-3bca-4f03-a2ed-6b4c6df51063" />

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
<img width="393" height="255" alt="image" src="https://github.com/user-attachments/assets/d9973fba-1876-4c74-8ca2-abe97a12ca6e" />

* Execute the following query to get a rowNum for students as per their marks.
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	ROW_NUMBER() OVER(ORDER BY Marks) RowNumber
FROM ExamResult;
```
<img width="475" height="258" alt="image" src="https://github.com/user-attachments/assets/f258e870-352c-4fb7-9c7a-4faa6ff84288" />

* We can specify descending order with Order By clause, and it changes the RANK accordingly.
# RANK Order
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	ROW_NUMBER() OVER(ORDER BY Marks DESC) RowNumber
FROM ExamResult;
```
<img width="482" height="261" alt="image" src="https://github.com/user-attachments/assets/bbcefa27-78fd-44bd-94dc-a4b33d0dd556" />

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
<img width="448" height="259" alt="image" src="https://github.com/user-attachments/assets/2d821a10-bd9a-404d-a5f7-6b968c46b657" />

# DENSE_RANK and RANK Fucntion:
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	DENSE_RANK() OVER(ORDER BY Marks DESC) Rank
FROM ExamResult
ORDER BY Rank;
```
<img width="445" height="253" alt="image" src="https://github.com/user-attachments/assets/ef0f994c-596f-46fb-b9b3-c22f69339eb8" />

* Check Rank 4 and 5
# PARTITION BY:
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
<img width="452" height="255" alt="image" src="https://github.com/user-attachments/assets/da9a0c6a-ded0-4741-b4d0-47d1aa18ed1f" />

# Check Rank 1 and 2
```sql
SELECT Studentname,
   	Subject,
   	Marks,
   	RANK() OVER(PARTITION BY StudentName ORDER BY Marks ) Rank
FROM ExamResult
ORDER BY Studentname,
     	Rank;
```
<img width="439" height="252" alt="image" src="https://github.com/user-attachments/assets/c6fd3f7e-8163-4738-845d-d881b105121b" />

# Check Rank 3 and 4
# CTE (Common Table Expression)
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
<img width="451" height="141" alt="image" src="https://github.com/user-attachments/assets/4482841a-4e39-4bcc-a9ce-43e5e40ccc83" />

# Multiple CTE
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
<img width="253" height="146" alt="image" src="https://github.com/user-attachments/assets/f9106d9c-a9ed-4706-84bf-f89244bffe8b" />

