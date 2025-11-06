## Partial Class
A **partial class** in C# allows the definition of a class to be split into multiple files. This can be particularly useful in scenarios where a class is large, and different developers are working on different parts of the same class, or when separating auto-generated code from the manually written code. The `partial` keyword is used to indicate that a class can be defined across multiple files. All parts of the partial class must be in the same assembly and namespace.<br>
**When to Use a Partial Class?**
-   **When a class is large:** If a class becomes too large to maintain in a single file, you can split it across multiple files, making it more manageable.
-   **Separation of concerns:** You may want to separate automatically generated code (e.g., from a designer or ORM tool) from your own code. In such cases, the automatically generated part of the class can be in one file, and the custom logic can be in another.
-   **Collaboration:** When multiple developers are working on the same class, you can split the class into different parts and work on them simultaneously without conflict.
#### 🧩 Example
In this example, Person class is split into two files (PersonPart1.cs and PersonPart2.cs). Both parts define properties and methods for the same class.
```csharp
// File 1: PersonPart1.cs
public partial class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public void PrintName()
    {
        Console.WriteLine($"{FirstName} {LastName}");
    }
}
// File 2: PersonPart2.cs
public partial class Person
{
    public int Age { get; set; }
    public void PrintAge()
    {
        Console.WriteLine($"Age: {Age}");
    }
}
// In your main program:
class Program
{
    static void Main(string[] args)
    {      
        Person person = new Person();
        person.FirstName = "John";
        person.LastName = "Doe";
        person.Age = 30;
        person.PrintName(); // Output: John Doe
        person.PrintAge(); // Output: Age: 30
    }
}
```

