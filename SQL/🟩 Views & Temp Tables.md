## <span style="background-color:#ffb84d; color:white; padding:2px 6px; border-radius:4px;">Medium</span> Views
A view is a virtual table that provides a way to represent data from one or more tables. It is stored as a query and does not hold data but rather provides a way to access it in a specific format.
<br>
<span style="background-color:#4caf50; color:white; padding:2px 6px; border-radius:4px;">Low</span> Can you update a view in SQL? If so, explain the conditions under which a view is updatable.
Yes, you can update a view, but there are some conditions under which a view is updatable:
- The view must directly reference one table (not multiple tables).
- It should not contain aggregate functions (SUM(), AVG(), etc.).
- The view should not have `DISTINCT, GROUP BY, or HAVING` clauses.
- The underlying table must allow updates (i.e., it must not be read-only).

**Example**
```sql
CREATE VIEW EmployeeView AS
SELECT employee_id, employee_name, salary
FROM employees
WHERE department_id = 1;
UPDATE EmployeeView
SET salary = salary * 1.1
WHERE employee_id = 101;
```
Explanation: The EmployeeView can be updated if it satisfies the conditions mentioned. In this case, we update the salary of employee 101.

### <span style="background-color:#4caf50; color:white; padding:2px 6px; border-radius:4px;">Low</span> Indexed Views
An **Indexed View** (also called a Materialized View) is a view that has a unique clustered index created on it. This allows the view to store the result set physically and improves performance for complex queries that reference the view frequently.

**Usage**: Indexed views are useful when you have complex calculations or aggregations and want to improve query performance by storing the precomputed results.

**SYNTAX**
```sql
CREATE VIEW SalesSummary AS
SELECT product_id, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY product_id;
CREATE UNIQUE CLUSTERED INDEX idx_sales_summary ON SalesSummary(product_id);
```
Explanation: The view `SalesSummary` is created with a clustered index, which physically stores the data in the database to improve performance.

**What is the purpose of a WITH CHECK OPTION in a view?** <br>
The `WITH CHECK OPTION` is used in a view to ensure that any modification (insert, update) made through the view adheres to the criteria defined in the view's `SELECT` statement. If the modification violates the condition, the operation will be rejected.

### Temprary Tables
A temporary table is a table that is created and exists for the duration of a session or until it is explicitly dropped. It is used to store intermediate data that is needed only during the session or transaction.

**SYNTAX**
```sql 
CREATE TEMPORARY TABLE TempEmployees AS SELECT * FROM employees WHERE department_id = 1;
```

### <span style="background-color:#ff4d4d; color:white; padding:2px 6px; border-radius:4px;">High</span> Temporary Tables vs Views
What is the difference between TEMPORARY tables and VIEWS in SQL?
- Temporary tables hold actual data, while views only store the query definition.
- Temporary tables exist until the session ends or the table is dropped, while views remain in the database unless dropped.
- Temporary tables can be indexed and modified, while views generally cannot.

| Feature | Temporary Table | Views |
|---------|-----------------|-------|
| Example | CREATE TEMPORARY TABLE TempEmployees AS SELECT * FROM employees WHERE department_id = 1; | CREATE VIEW DepartmentView AS SELECT employee_name, department_id FROM employees WHERE department_id = 1; |
