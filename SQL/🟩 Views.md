### Views
A view is a virtual table that provides a way to represent data from one or more tables. It is stored as a query and does not hold data but rather provides a way to access it in a specific format.
<br>
Can you update a view in SQL? If so, explain the conditions under which a view is updatable.
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
