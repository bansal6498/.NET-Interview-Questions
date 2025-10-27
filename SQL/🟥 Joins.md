### 🟥 JOINS
- **INNER JOIN**: Returns records that have matching values in both tables.
- **LEFT JOIN (or LEFT OUTER JOIN)**: Returns all records from the left table and the matched records from the right table. If no match is found, NULL values are returned for columns from the right table.
- **RIGHT JOIN (or RIGHT OUTER JOIN)**: Returns all records from the right table and the matched records from the left table. If no match is found, NULL values are returned for columns from the left table.
- **FULL JOIN (or FULL OUTER JOIN)**: Returns all records when there is a match in either the left or right table. If no match is found, NULL values are returned for columns from the table without a match.
- **CROSS JOIN**: Returns the Cartesian product of both tables (i.e., all possible combinations of rows from both tables).
<br>

**INNER JOIN vs OUTER JOIN**
- INNER JOIN: Returns only the rows where there is a match in both tables.
- OUTER JOIN: Returns all rows from one table and the matched rows from the other table. 
<br>

    **If there is no match, NULL values are returned for columns of the table that has no match.**
<br>

**SYNTAX**
```sql 
SELECT column_name FROM table1 JOIN table2 ON table1.matchColumn = table2.matchedColumn;
```
