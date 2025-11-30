## WHERE vs HAVING
-   WHERE: Used to filter rows before grouping.
-   HAVING: Used to filter rows after grouping. It is applied to the aggregated data.

#### Example
```sql 
SELECT department, COUNT(*)
FROM employees
WHERE salary > 50000
GROUP BY department
HAVING COUNT(*) > 5;
```
## Select vs Select All
-   The `SELECT` statement is used to query data from one or more tables in a database. It retrieves specified columns from the database table. It can be used to fetch specific columns or rows based on a condition.
-   The `SELECT ALL` is actually the default behavior in SQL. It retrieves all records from the specified columns or tables without removing duplicates. This is redundant as SELECT by default retrieves all rows and columns, including duplicates.
## NULL Value in SQL
**NULL:** Represents the absence of a value or unknown data. It is not the same as an empty string or zero.
-   Empty String: A string with no characters (''), but still exists as a value.
-   Zero: A numeric value representing 0, a valid number.
## Primary Key in SQL
A `PRIMARY KEY` is a constraint that uniquely identifies each record in a table. It ensures that the column(s) it is applied to do not have `NULL` values and are unique across all rows.
-   A table can have only one `PRIMARY KEY`.
-   It automatically creates a unique index on the column.
#### Example
```sql
CREATE TABLE employees (
 employee_id INT PRIMARY KEY,
 name VARCHAR(100)
);
```
#### What is a primary key in SQL?
**Answer:**
A primary key is a column or a combination of columns that uniquely identifies each row in a table. Primary keys must contain unique values and cannot contain NULLs. When a primary key is defined, a unique index is automatically created on the primary key column(s).
#### Example
```sql
CREATE TABLE Employees (
    EmployeeId INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);
```
#### What is a foreign key in SQL?
**Answer:**
A foreign key is a column or a combination of columns that establishes a link between the data in two tables. It enforces referential integrity by ensuring that the value in the foreign key column exists in the referenced primary key column of another table.
#### Example
```sql
CREATE TABLE Orders (
    OrderId INT PRIMARY KEY,
    OrderDate DATE,
    EmployeeId INT,
    FOREIGN KEY (EmployeeId) REFERENCES Employees(EmployeeId)
);
```
## UNION vs UNION ALL
-   `UNION`: Combines the result sets of two or more queries and removes duplicate rows.
-   `UNION ALL`: Combines the result sets of two or more queries, but does not remove duplicates.

#### Example
```sql
SELECT name FROM employees WHERE department = 'IT'
UNION
SELECT name FROM employees WHERE department = 'HR';
-- Will remove duplicates between both queries.
SELECT name FROM employees WHERE department = 'IT'
UNION ALL
SELECT name FROM employees WHERE department = 'HR';
-- Will not remove duplicates between both queries.
```
## CHAR vs VARCHAR
-   **CHAR**: A fixed-length character data type. It always reserves the specified length, even if the string is shorter.
-   **VARCHAR**: A variable-length character data type. It only uses the amount of space required for the data stored, plus a small overhead for length information.

**SYNTAX**
```sql
CREATE TABLE products (
 product_code CHAR(10), -- Fixed length of 10
 product_name VARCHAR(50) -- Variable length up to 50
);
```
## GROUP BY
The `GROUP BY` clause is used to arrange identical data into groups. It is typically used with aggregate functions (`COUNT(), SUM(), AVG(),` etc.) to perform calculations on each group.

**SYNTAX**
```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```
## Aggregate Functions
Aggregate functions perform a calculation on a set of values and return a single result. Common aggregate functions include:
-   **COUNT()**: Returns the number of rows in a set.
-   **SUM()**: Returns the sum of a numeric column.
-   **AVG()**: Returns the average of a numeric column.
-   **MIN()**: Returns the minimum value in a column.
-   **MAX()**: Returns the maximum value in a column.

**SYNTAX**
```sql
SELECT department, AVG(salary) FROM employees GROUP BY department;
```
#### What is the difference between SQL and NoSQL databases?
**Answer:**
-   **SQL**: Relational, structured schema, uses tables/joins (e.g., SQL Server, PostgreSQL).
-   **NoSQL**: Non-relational, flexible schema, stores JSON/documents/graphs (e.g., MongoDB, Cassandra).
#### In which scenarios would you prefer NoSQL over SQL?
**Answer:**
-   Large-scale, unstructured data.
-   Schema flexibility (rapid iterations).
-   High write scalability.
-   Examples: Real-time analytics, IoT data, social media feeds.
