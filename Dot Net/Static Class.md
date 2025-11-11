## Static Class
A static class in C# is a class that cannot be instantiated and can only contain static members. Static classes are used to group related utility or helper methods that don't require object instances.
### Characteristics
1.  **Cannot Be Instantiated:** You cannot create an instance of a static class using the `new` keyword.
#### 🧩 Example

Invalid: Cannot create an instance of a static class.</br>

```csharp
static class MyStaticClass
{
    public static void MyMethod()
    {
        Console.WriteLine("Hello from static class!");
    }
}
// MyStaticClass obj = new MyStaticClass();
```
2.  **Contains Only Static Members:** All members (fields, properties, methods) of a static class must be static.
#### 🧩 Example
```csharp
static class MyStaticClass
{
    public static int Counter = 0;
    public static void Increment()
    {
        Counter++;
    }
}
```
3.  **Cannot Inherit or Be Inherited:** A static class cannot be inherited, nor can it inherit from another class.
4.  **Used for Grouping Related Methods/Utility Functions:** Static classes are often used to group methods or data that are related and don't require instance-based state, such as utility or helper methods.
### When to Use a Static Class?
Static classes are used in scenarios where:
-   The class does not need to maintain any state (i.e., no instance variables).
-   Methods are general utilities (e.g., string manipulation, math operations, logging).
-   You need to group related methods logically but don't want the overhead of creating objects.
-   Utility/Helper Methods: Functions like `Math.Pow()` or `Console.WriteLine()` are often static methods.
 
#### Can we Create a Constructor in Static Class?
**Answer:**
No, you cannot create an instance constructor for a static class. Static classes cannot be instantiated, and thus, they don’t have instance constructors. However, you can have a static constructor to initialize static data.
#### Can Static Classes Have Instance Members?
**Answer:**
No, static classes cannot have instance members (i.e., non-static fields or methods). All members of a static class must be declared with the static keyword.
-   A static class cannot be instantiated, and it can only have static members.
-   A static constructor initializes static members of a static class.
-   A constructor in a static class is allowed, but only as a static constructor.