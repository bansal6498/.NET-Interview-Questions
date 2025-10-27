## Common Table Explression (CTE)
A **Common Table Expression (CTE)** is a temporary result set that you can reference within a`SELECT, INSERT, UPDATE, or DELETE` statement. It helps improve the readability and structure of SQL queries.
**SYNTAX**
```sql
WITH CTE_Name AS (
 SELECT column1, column2
 FROM table_name
 WHERE condition
)
SELECT * FROM CTE_Name;
Example:
WITH DepartmentSales AS (
 SELECT department_id, SUM(sales_amount) AS total_sales
 FROM sales
 GROUP BY department_id
)
SELECT * FROM DepartmentSales WHERE total_sales > 50000;
```
Explanation: The CTE `DepartmentSales` is defined with the `WITH` keyword, and it can be used later in the query to filter departments with total sales greater than 50,000.

## <span style="background-color:#4caf50; color:white; padding:2px 6px; border-radius:4px;">Low</span> Subquery
A subquery is a query embedded within another query. It is used to retrieve data that will be used in the main query. A subquery can be used in SELECT, INSERT, UPDATE, and DELETE statements.

**SYNTAX**
```sql
SELECT name FROM employees
WHERE department_id = (SELECT department_id FROM departments WHERE
department_name = 'IT');
```

### <span style="background-color:#ffb84d; color:white; padding:2px 6px; border-radius:4px;">Medium</span> CTE vs Subquery
- CTE: A CTE is defined outside the main query using the `WITH` keyword and can be referenced multiple times within the query. It enhances readability, especially in complex queries.
- Subquery: A subquery is a query nested inside another query and can be used within the `SELECT, WHERE, or FROM` clauses. It is often harder to read and manage compared to CTEs.
<br>

A **Recursive CTE** is a CTE that references itself in its definition. It is used to solve problems involving hierarchical or tree-like data structures, such as organizational charts or directory structures.
**SYNTAX**
```sql
WITH RECURSIVE CTE_Name AS (
 -- Base case: the non-recursive part
 SELECT column1, column2
 FROM table_name
 WHERE condition
 UNION ALL
 -- Recursive case
 SELECT t.column1, t.column2
 FROM table_name t
 JOIN CTE_Name cte ON t.parent_id = cte.id
)
SELECT * FROM CTE_Name;
Example:
WITH RECURSIVE OrgChart AS (
 -- Base case: the CEO
 SELECT employee_id, employee_name, manager_id
 FROM employees
 WHERE manager_id IS NULL
 UNION ALL
 -- Recursive case: finding all subordinates
 SELECT e.employee_id, e.employee_name, e.manager_id
 FROM employees e
 JOIN OrgChart oc ON e.manager_id = oc.employee_id
)
SELECT * FROM OrgChart;
```
Explanation: This query uses a recursive CTE to fetch all employees and their subordinates, starting with the CEO (manager_id is NULL).

<span style="background-color:#ffb84d; color:white; padding:2px 6px; border-radius:4px;">Medium</span>

**How do you optimize a query involving views or CTEs?**
- **Materialize the View:** For complex views that involve expensive calculations or aggregations, consider creating an indexed view or materialized view.
- **Use of CTEs:** If the query is too complex, break it down using CTEs to enhance readability and performance. However, avoid overusing them if performance becomes an issue.
- **Avoid Nested Views:** Avoid creating views that reference other views, as it can make queries difficult to optimize.
- **Indexing:** Ensure the underlying tables and columns referenced by views and CTEs are properly indexed, especially for large datasets.
- **Limit Data:** Use WHERE clauses to filter data early, ensuring that only necessary rows are processed in views and CTEs.