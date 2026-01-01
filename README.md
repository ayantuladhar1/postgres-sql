# Postgres-SQL-1 (SELECT, WHERE, DROP)

PostgreSQL uses the SELECT statement to retrieve data from one or more tables, allowing users to view specific columns or all records. The WHERE clause is used to filter rows based on conditions, making queries more precise and efficient. The DROP statement is a Data Definition Language (DDL) command used to permanently remove database objects such as tables or databases. These commands form the foundation of working with data in PostgreSQL.

# Postgres-SQL-2 (COUNT, MIN, MAX, SUM, AVG)

PostgreSQL provides aggregate functions such as COUNT, MIN, MAX, SUM, and AVG to perform calculations on groups of rows. These functions are commonly used to generate summaries, statistics, and reports from data. Aggregate functions are often combined with the GROUP BY clause to calculate results for each group independently. They are essential for data analysis and reporting tasks.

# Postgres-SQL-3 (LIKE)

The LIKE operator in PostgreSQL is used for pattern matching within text data. It allows users to search for values using wildcard characters such as % (multiple characters) and _ (single character). LIKE is commonly used in search functionality, filtering text columns, and matching partial values. PostgreSQL also supports ILIKE for case-insensitive pattern matching.

# Postgres-SQL-4 (IN, BETWEEN)

PostgreSQL uses the IN operator to filter rows that match any value in a specified list, making queries cleaner and more readable than multiple OR conditions. The BETWEEN operator is used to filter results within a specific range, including both boundary values. These operators improve query clarity and are widely used in filtering numeric, date, and text data.

# Postgres-SQL-5 (JOIN)

PostgreSQL supports various types of joins such as INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN to combine data from multiple tables based on related columns. Joins are fundamental for working with normalized databases where data is split across tables. They allow users to retrieve meaningful combined results from relational data structures. Proper use of joins improves query accuracy and database design.

# Postgres-SQL-6 (GROUP BY, CASE, EXISTS)

The GROUP BY clause in PostgreSQL is used to group rows that share common values, often combined with aggregate functions. The CASE expression allows conditional logic within SQL queries, similar to if-else statements in programming languages. The EXISTS operator checks for the presence of rows in a subquery and is commonly used for efficient filtering. Together, these features enable advanced query logic and data analysis.

# Postgres-SQL-7 (Rank)

PostgreSQL provides powerful window functions such as RANK(), DENSE_RANK(), and ROW_NUMBER() to assign rankings to rows based on specified ordering criteria. These functions are commonly used to analyze performance, leaderboards, and ordered results without collapsing rows like GROUP BY. The ranking behavior can be controlled using the ORDER BY clause and refined with PARTITION BY to reset rankings within groups. Ranking functions are essential for analytical and reporting queries.
