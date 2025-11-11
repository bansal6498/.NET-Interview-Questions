## STORED PROCEDURE 
Stored procedures in Oracle are precompiled SQL code that is stored in the database and can be executed on demand. They are used to encapsulate business logic and improve performance by reducing the amount of data transferred between the application and the database.

### Stored Procedure vs Functions
Feature | Function | Stored Procedure|
|-----------|-------------|-----------|
**Definition** | A function is a named block of code that can accept parameters, perform operations, and return a value. | A stored procedure is a set of SQL statements that can perform operations on the database (e.g., insert, update, delete) and can accept input parameters, but unlike functions, it doesn’t necessarily return a value.
**Example** | `CREATE FUNCTION GetEmployeeSalary (@EmpID INT) RETURNS DECIMAL AS BEGIN RETURN (SELECT Salary FROM Employees WHERE EmployeeID = @EmpID); END;` | `CREATE PROCEDURE UpdateEmployeeSalary (@EmpID INT, @NewSalary DECIMAL) AS BEGIN  UPDATE Employees SET Salary = @NewSalary WHERE EmployeeID = @EmpID; END;`
**Key Point** |  A function can be used inside queries (e.g., SELECT statements). | A stored procedure can't be used directly inside queries. |
**Return Value** | A function returns a value (e.g., scalar value or table) | A stored procedure does not (though it can return result sets). |
**Usage** | Functions can be used in queries | stored procedures are called explicitly and usually involve a series of actions. |
**Try-Catch** | Functions cannot be directly used in Try-Catch Block | Stored procedures can be used in Try-Catch Block |
**Execution Plan Reusebility** | They do not maintain their own execution plan and are recompiled as part of the parent query. <br> Functions (scalar or table-valued) are treated as part of the query where they are invoked. | The SQL Server compiles and caches the execution plan for stored procedures upon their first execution. <br> This means that for subsequent calls, the precompiled execution plan is reused, reducing overhead.
**Performance** | Slower for Large Datasets, especially scaler functions | Faster due to precompiled execution plan |
**DML Operations** | Does not supports DML Operations | Supports DML Operations `DELETE, INSERT, UPDATE` |
**Caching** | No separate execution plan is cached | Execution plan is cached | 
#### Stored procedures are faster than functions primarily because of execution plan caching, batch processing, and reduced context switching. While both have their specific use cases, stored procedures are ideal for performance-critical and complex operations, whereas functions are better suited for simpler, reusable logic.