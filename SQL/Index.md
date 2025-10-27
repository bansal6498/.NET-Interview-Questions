## INDEX
An index is a database object that improves the speed of data retrieval operations on a table. It is created on one or more columns in a table to make searching faster. However, indexes can slow down write operations (INSERT, UPDATE, DELETE) since the index must be updated when the data changes.
-   **Unique Index**: Ensures that all values in a column are distinct.
-   **Non-Unique Index**: Allows duplicate values in the indexed column.

**SYNTAX**
```sql
CREATE INDEX idx_employee_name ON employees(name);
```
