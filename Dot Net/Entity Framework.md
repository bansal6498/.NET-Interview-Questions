## Entity Framework
Entity Framework (EF) is an Object-Relational Mapper (ORM) that allows developers to interact with a database using C# objects instead of writing raw SQL queries. It abstracts the database interactions and provides methods to query, insert, update, and delete data. EF supports both code-first and database-first approaches. EF Core is the lightweight, cross-platform version of EF, typically used with .NET Core.
#### Have you worked with ORM? Which ORM did you use, and how?
**Answer:**
-   Yes, Entity Framework Core.
-   Used for database mapping → LINQ queries to interact with SQL Server.
-   Applied migrations for schema changes.
-   Optimized with AsNoTracking, compiled queries.
### Pagination with EF Core
```csharp
var pageSize = 10;
var data = db.Users
             .Skip((page-1)*pageSize)
             .Take(pageSize)
             .ToList();
```
