## Basic
### Hard Binding vs Loose Binding
-   **Hard Binding**: This refers to a strong coupling between components. One component explicitly depends on the other, and changes to one will likely require changes to the other. It’s common in traditional development where dependencies are tightly coupled.<br>
Example: A method directly calls another method within the same class.
-   **Loose Binding**: This refers to a weak coupling between components. One component can function without knowing about the other’s internal details. It allows for more flexible, maintainable, and scalable systems.<br>
Example: Using interfaces or dependency injection to decouple classes.
### Memory Management in DotNet
-   .NET uses Automatic Memory Management to handle memory allocation and deallocation.
-   **Heap**: The heap is used for dynamically allocated objects. When an object is created, it is allocated in the heap.
-   **Stack**: The stack is used for method calls and local variables.
-   **Garbage** Collection (GC): .NET uses garbage collection to automatically reclaim memory by removing objects that are no longer in use. The garbage collector identifies unused objects and frees their memory, preventing memory leaks.
-   Generational Approach: .NET GC divides objects into generations (0, 1, and 2) based on their lifetimes. Short-lived objects are collected more frequently, while long-lived objects are collected less frequently.
### ENUM
**Enums** (short for **Enumerations**) are a special data type in C# that allows you to define a set of named constants. They are used to represent a collection of related values in a more readable and maintainable way.
#### 🧩 Example
SYNTAX- Here, Day is an enumeration, and its values (Sunday, Monday, etc.) are constants starting from 0 by default. You can explicitly assign values if needed.
```csharp
enum Day
{
Sunday,
Monday,
Tuesday,
}
```
-   Key Points:
1.  Enums improve code readability and reduce the risk of invalid values.
2.  They can be cast to integers and vice versa.
3.  Enums can have different underlying types (e.g., byte, short, int).
### Printing vs Logging
**Printing** typically refers to sending output to a console or display, often for debugging or temporary visibility.
#### 🧩 Example

Print is used for displaying messages to the user or developers during runtime for debugging purposes.

```csharp
Console.WriteLine("Hello, World!");
```
**Logging** is the process of recording runtime information (such as errors, warnings, or information) into a log file or a logging system.
#### 🧩 Example

Logging is a more formalized and persistent method of tracking application activity. It supports various log levels (e.g., Info, Error, Warning) and can write logs to files or external systems.

```csharp
ILogger logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();
logger.LogInformation("Application started");
```
-   Difference
Printing is more of a temporary or debugging feature, whereas logging is a structured and persistent record of events or activities in an application.
### Value Types vs Reference Types
**Value Types** These types hold data directly and are stored on the stack. Examples include `int, double, char, struct.`
-   When a value type is assigned to another variable, a copy of the data is made.
**Reference Types** These types store a reference (or pointer) to the actual data, which is stored on the heap. Examples include `class`, `string`, `array`, `delegate`.
-   When a reference type is assigned to another variable, both variables point to the same memory location, so changes to one will affect the other.
### Out vs Ref
In C#, both `out` and `ref` are used to pass arguments to methods by reference, allowing the method to modify the values of the arguments. However, there are key differences in how they work:
#### ref (reference Keyword)
**Definition**: The `ref` keyword is used to pass a parameter by reference, meaning that the method can modify the value of the argument. The parameter must be initialized before being passed to the method.<br>
**Usage**: The value of the argument is expected to be initialized before passing to the method.
#### 🧩 Example
```csharp
using System;
class Program
{
    static void ModifyValue(ref int number)
    {
        number = number + 5;
    }
    static void Main()
    {
        int num = 10;
        ModifyValue(ref num); // The value of num is passed by reference
        Console.WriteLine(num); // Output: 15
    }
}
```
**Key Points**
-   The variable must be initialized before calling the method.
-   The method can modify the value of the variable.
#### out (Output Keyword)
**Definition**: The out keyword is used to pass a parameter by reference, but it is specifically intended to return a value from the method. The argument does not need to be initialized before being passed, but it must be assigned a value before the method finishes execution.<br>
**Usage**: The parameter does not need to be initialized before passing it to the method.
#### 🧩 Example
```csharp
using System;
class Program
{
    static void GetNumber(out int number)
    {
        number = 42; // Assigning value inside the method
    }
    static void Main()
    {
        int num;
        GetNumber(out num); // The value of num is assigned inside the method
    Console.WriteLine(num); // Output: 42
    }
}
```
**Key Points**
-   The variable does not need to be initialized before calling the method.
-   The method must assign a value to the variable before returning.
### Const vs Var
In C#, const and var are used to declare variables, but they serve different purposes:
#### const (Constant):
**Definition:** The const keyword is used to define a constant value that cannot be changed during the program's execution. Once a value is assigned to a const variable, it is fixed and cannot be modified. <br>
**Usage:** You must assign a value at the time of declaration, and the value remains constant throughout the program.
#### 🧩 Example
```csharp
using System;
class Program
{
    const double Pi = 3.14; // Pi is a constant value
    static void Main()
    {
        Console.WriteLine(Pi); // Output: 3.14
    }
}
```
**Key Points**
-   The value assigned to a `const` is fixed at compile time.
-   `const` variables must be assigned a value at the time of declaration.
-   Constants are typically used for values that are not expected to change, such as mathematical constants.
#### var (Implicitly Typed Variable)
**Definition**: The var keyword is used to declare a variable without explicitly specifying its type. The compiler infers the type of the variable based on the assigned value.
**Usage**: You do not specify the type of the variable; the compiler automatically determines it based on the initializer.
#### 🧩 Example
```csharp
using System;
class Program
{
    static void Main()
    {
        var number = 10; // The compiler infers that 'number' is of type int
        var text = "Hello, world!"; // The compiler infers that 'text' is of type string
        Console.WriteLine(number); // Output: 10
        Console.WriteLine(text); // Output: Hello, world!
    }      
}
```
**Key Points**
-   The type of the variable is inferred by the compiler.
-   `var` can only be used when the variable is initialized at the time of declaration.
-   The type cannot change after the variable is initialized (it's strongly typed after initialization).
### Const vs Readonly
`const`: A const is a constant value that is determined at compile time. It must be assigned a value at the time of declaration and cannot be modified later.
#### 🧩 Example
```csharp
public const int MaxLimit = 100; // Compile-time constant
```
`readonly`: A readonly field can only be assigned a value during its declaration or in a constructor. It can be modified at runtime, but once assigned, it cannot be changed again.
#### 🧩 Example
```csharp
public readonly int MaxLimit; // Run-time constant
public MyClass(int limit)
{
    MaxLimit = limit; // Can assign value in constructor
}
```
#### Summary of Differences
| 🔹 **Feature** | **out** | **ref** | **const** | **var** |
|----------------|----------------|----------------|-------------|-------------|
| **Initialization Before Use** | No, does not need to be initialized | Yes | Yes, must be initialized at declaration | No, the compiler infers the type based on the initializer |
| **Purpose** | To return a value from a method | To pass a value by reference | To define a constant value | To let the compiler infer the variable type |
| **Value Change**| Must be assigned in method | Can be modified in method | Cannot be changed once assigned | Can change the value but type is fixed | 
| **Typical Use Case** | Returning multiple values from a method | Passing large objects or modifying values | Defining constant values like Pi, or mathematical constants | When the type is obvious from the initializer |




