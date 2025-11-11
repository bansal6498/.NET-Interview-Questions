## JOINS
-   **INNER JOIN**: Returns records that have matching values in both tables.
-   **LEFT JOIN (or LEFT OUTER JOIN)**: Returns all records from the left table and the matched records from the right table. If no match is found, NULL values are returned for columns from the right table.
-   **RIGHT JOIN (or RIGHT OUTER JOIN)**: Returns all records from the right table and the matched records from the left table. If no match is found, NULL values are returned for columns from the left table.
-   **FULL JOIN (or FULL OUTER JOIN)**: Returns all records when there is a match in either the left or right table. If no match is found, NULL values are returned for columns from the table without a match.
-   **CROSS JOIN**: Returns the Cartesian product of both tables (i.e., all possible combinations of rows from both tables).
<br>

**INNER JOIN vs OUTER JOIN**
- INNER JOIN: Returns only the rows where there is a match in both tables.
- OUTER JOIN: Returns all rows from one table and the matched rows from the other table. 
    -   If there is no match, NULL values are returned for columns of the table that has no match.

**SYNTAX**
```sql 
SELECT column_name FROM table1 JOIN table2 ON table1.matchColumn = table2.matchedColumn;
```
## Queries
#### Retrieve the names of employees and their department names using INNER JOIN.
**Answer:**
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```
**Explanation:** This query retrieves only the employees who are assigned to a department. It
combines rows from employees and departments where the department_id matches in both
tables.

#### Retrieve all employees and their department names. If an employee does not belong to a department, show NULL for the department name.
**Answer:**
```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.department_id;
```
**Explanation**: This query retrieves all employees, including those who are not assigned to a department. For those without a department, the department_name will be NULL.