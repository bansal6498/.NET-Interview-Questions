##  RANK(), ROW_NUMBER(), DENSE RANK()
-   **ROW_NUMBER():** Assigns a unique sequential integer to rows, starting from 1. It does not consider duplicate values.
-   **RANK():** Assigns a rank to rows, with the same rank for identical values, but leaves gaps in the rank for ties.
-   **DENSE_RANK():** Similar to RANK(), but does not leave gaps in the rank for ties. 

**Example**
```sql
SELECT employee_name, salary,
 RANK() OVER (ORDER BY salary DESC) AS rank,
 ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num,
 DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank
FROM employees;
```
**Explanation**: This query returns three columns showing the rank, row number, and dense rank of employees based on their salary. Rows with the same salary will have the same rank in `RANK()` and `DENSE_RANK()`, but `ROW_NUMBER()` will assign a unique value to each row.

**Query to Find Second Highest Salary**<br>
To find the second-highest salary from an employee table, you can use the following SQL query:
```sql
SELECT MAX(salary) AS SecondHighestSalary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```
