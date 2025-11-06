## Extension Methods
**Extension methods** in C# allow you to "add" new functionality to an existing class without modifying its source code. These methods are defined in static classes and are called as if they were instance methods of the target class. <br>Extension methods are particularly useful when working with types that you cannot modify directly, such as classes in third-party libraries, or when you want to provide additional utility methods for a class.<br>
**Why Use Extension Methods?**
-   **Improves Readability:** You can call methods in a fluent, natural syntax without modifying the original class.
-   **Encapsulation:** You can extend classes (including third-party libraries or framework types) without modifying their code or creating a derived class.
-   **Clean Code:** Helps reduce the need for utility or helper classes that are tightly coupled with the types they're operating on.
-   **Reusability:** Makes it easy to reuse the code for common operations across multiple projects or different types.
**When to Use Extension Methods?**
-   **Enhance existing classes:** When you want to add functionality to an existing class (including third-party or system libraries) without modifying the original class.
-   **Simplify code:** When a method is logically related to a type but doesn't belong to that type's definition, you can add it via extension methods to simplify your code and improve readability.
-   **For LINQ queries:** Extension methods are extensively used in LINQ to add methods like `Where, Select, OrderBy`, etc., to collections and other data structures.
**How to Implement an Extension Method:**
To implement an extension method, you need:
1.  A static class to contain your extension methods.
2.  A static method in that class with the this keyword in the first parameter, specifying the type you're extending.
