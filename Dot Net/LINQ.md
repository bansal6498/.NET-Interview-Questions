## LINQ
Language Integrated Query (LINQ) is a feature in C# that allows you to query collections (such as arrays, lists, and databases) using a SQL-like syntax directly in C#. LINQ can be used to filter, group, and manipulate data from various data sources such as in-memory collections or databases. It provides a readable and concise way to interact with data.
LINQ (Language Integrated Query) is a set of methods that allows you to query collections, databases, XML, and other data sources in a declarative way, directly from C#. It is integrated into C# language and provides a consistent approach to querying various types of data.
### Why it's used:
-   Concise Code: LINQ enables more readable and expressive queries with fewer lines of code.
-   Integration: It can be used with arrays, collections, XML, databases (using Entity Framework), etc.
-   Strong Typing: LINQ queries are strongly typed, meaning that errors are caught during compile-time.
### 🧩 Example

SYNTAX

```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0);
```
#### Explain the difference between LINQ to Objects, LINQ to SQL, and LINQ to Entities.
**Answer:**
-   **LINQ to Objects:** This type of LINQ is used to query in-memory collections like arrays, lists, etc.
-   **LINQ to SQL:** It is used to query SQL Server databases using LINQ, and it translates LINQ queries to SQL queries and executes them against the database.
-   **LINQ to Entities:** It is used to query an Entity Framework model, which can be a representation of a database or other data source. It operates on entities and can be used to query databases like LINQ to SQL.
### 🧩 Example

LINQ to Objects

```csharp
var evenNumbers = numbers.Where(n => n % 2 == 0);
```
### 🧩 Example

LINQ to SQL

```csharp
var products = dbContext.Products.Where(p => p.Price > 100);
```
### 🧩 Example

LINQ to Entities

```csharp
var employees = context.Employees.Where(e => e.Department == "HR");
```
#### What is deferred execution in LINQ?
**Answer:**
Deferred execution in LINQ means that the query is not executed when it is defined, but rather when it is enumerated (e.g., when iterating over the results). This allows for more efficient querying since the data is not retrieved until necessary.
### 🧩 Example

Differed Execution

```csharp
var query = numbers.Where(n => n > 2); // Query is not executed yet.
var result = query.ToList(); // Query is executed here when enumerated.
```
#### Note: ToList(), ToArray(), etc., force immediate execution of the query.
#### What are the different types of LINQ operators?
**Answer:**
LINQ operators can be categorized into the following types:
-   Filtering: `Where()`, `OfType()`
-   Projection: `Select()`, `SelectMany()`
-   Sorting: `OrderBy()`, `OrderByDescending()`, `ThenBy()`, `ThenByDescending()`
-   Grouping: `GroupBy()`
-   Joining: `Join()`, `GroupJoin()`
-   Set Operations: `Distinct()`, `Union()`, `Intersect()`, `Except()`
-   Aggregation: `Count()`, `Sum()`, `Average()`, `Min()`, `Max()`
-   Element Operations: `First()`, `FirstOrDefault()`, `Last()`, `LastOrDefault()`, `Single()`, `SingleOrDefault()`.
### 🧩 Example
```csharp
var sortedNumbers = numbers.OrderBy(n => n);
var groupedNumbers = numbers.GroupBy(n => n % 2 == 0);
```
#### Explain how to perform a join operation using LINQ.
**Answer:**
A join in LINQ combines two collections based on a matching key. There are two types of joins:
-   Inner Join: Combines only the matching elements.
-   Group Join: Combines elements and groups them based on a common key.
### 🧩 Example

Inner Join (LINQ)

```csharp
var employees = new List<Employee>
{
    new Employee { Id = 1, Name = "John", DepartmentId = 1 },
    new Employee { Id = 2, Name = "Jane", DepartmentId = 2 }
};
var departments = new List<Department>
{
    new Department { Id = 1, Name = "HR" },
    new Department { Id = 2, Name = "IT" }
};
var employeeDepartmentJoin = from e in employees
            join d in departments on e.DepartmentId equals d.Id
            select new { e.Name, d.Name };
foreach (var ed in employeeDepartmentJoin)
{
    Console.WriteLine($"{ed.Name} works in {ed.Name} department");
}
```
#### How can you perform grouping in LINQ?
**Answer:**
Grouping in LINQ can be done using the GroupBy() method, which groups elements based on a specified key.
### 🧩 Example
```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7 };
var groupedNumbers = numbers.GroupBy(n => n % 2 == 0);
foreach (var group in groupedNumbers)
{
    Console.WriteLine(group.Key ? "Even numbers" : "Odd numbers");
    foreach (var number in group)
    {
        Console.WriteLine(number);
    }
}
```
### SelectMany()
`SelectMany` is used when you need to project each element of a collection into a sequence of collections and then flatten the result into a single collection. It is typically used when working with nested collections.
#### 🧩 Example
SelectMany flattens the collection of products from each category into a singlecollection of product names.
```csharp
var categories = new List<Category>
{
    new Category { Name = "Electronics", Products = new List<Product> { new Product { Name = "Laptop" }, new Product { Name = "Smartphone" } } },
    new Category { Name = "Home Appliances", Products = new List<Product> { new Product {Name = "Refrigerator" }, new Product { Name = "Washing Machine" } } }
};
var products = categories.SelectMany(c => c.Products).Select(p => p.Name);
```
### First() and FirstOrDefault()
-   `First()`: Returns the first element from the collection. Throws an exception if no element is found.
-   `FirstOrDefault()`: Returns the first element or null (or the default value for value types) if no element is found.
#### 🧩 Example
```csharp
var firstNumber = numbers.First(); // Throws InvalidOperationException if empty
var firstOrDefaultNumber = numbers.FirstOrDefault(); // Returns 0 for an empty list
```
### Distinct()
The `Distinct()` operator is used to remove duplicate values from a collection.
#### 🧩 Example
```csharp
var numbers = new List<int> { 1, 2, 3, 3, 4, 5, 5 };
var distinctNumbers = numbers.Distinct();
foreach (var number in distinctNumbers)
{
    Console.WriteLine(number);
}
```
#### What is the Aggregate() function in LINQ? Explain with an example.
**Answer:**
The Aggregate() function is used to apply a custom accumulator function to a sequence, allowing for operations like sum, product, concatenation, etc.
#### 🧩 Example
```csharp
var numbers = new List<int> { 1, 2, 3, 4 };
var sum = numbers.Aggregate((total, next) => total + next);
Console.WriteLine(sum); // Output: 10
```
### IEnumerable vs IQueryable
#### IEnumerable<T>
-   Represents a collection of objects that can be iterated over in memory.
-   Works in-memory and executes the query immediately (when the ToList() or ToArray() method is called).
-   Suitable for working with in-memory collections (e.g., arrays, lists, or collections from LINQ to Objects).
-   Queries are executed in memory, meaning all data must be loaded into memory before the query is executed.
#### 🧩 Example
```csharp
IEnumerable<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
var result = numbers.Where(n => n > 2); // Query executed immediately
```
#### IQueryable<T>
-   Represents a queryable collection that supports deferred execution and is typically used for querying data from a data source like a database.
-   Executes the query against a data source, such as a database, when the results are enumerated or explicitly executed (like using ToList(), First(), etc.).
-   Queries are not executed immediately but are translated into a query language like SQL, which is executed when data is needed.
#### 🧩 Example
```csharp
IQueryable<int> numbers = dbContext.Numbers.Where(n => n > 2); // SQL query executed
when enumerated
var result = numbers.ToList();
```
### Single() vs SingleOrDefault()
-   `Single()` throws an exception if there is more than one matching element.
-   `SingleOrDefault()` returns the first match or null if none are found.
### Take() vs Skip()
-   `Take()` retrieves the first n elements.
-   `Skip()` skips the first n elements and returns the rest.
### Pagination with EF Core
```csharp
var pageSize = 10;
var data = db.Users
             .Skip((page-1)*pageSize)
             .Take(pageSize)
             .ToList();
```
### First Non-Repeating Character
```csharp
var ch = str.GroupBy(c => c)
            .Where(g => g.Count() == 1)
            .Select(g => g.Key)
            .FirstOrDefault();
```
### LINQ for Duplicates
```csharp
var duplicates = arr.GroupBy(x => x)
                    .Where(g => g.Count() > 1)
                    .Select(g => g.Key);
```