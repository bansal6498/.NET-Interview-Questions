## <span style="background-color:#ff4d4d; color:white; padding:2px 6px; border-radius:4px;">High</span> <span style="background-color:#ff4d4d; color:white; padding:2px 6px; border-radius:4px;">High</span> <span style="background-color:#ff4d4d; color:white; padding:2px 6px; border-radius:4px;">High</span> Abstract Class
An abstract class is a class that cannot be instantiated directly. It can contain both abstract (unimplemented) methods and concrete (implemented) methods. Abstract classes are useful when you want to share code between several related classes, but still enforce that certain methods are implemented by the subclasses.
### Characteristics of Abstract Class:
1. Can have both abstract and concrete methods:
-       An abstract method is a method without implementation, while a concrete method can have an implementation.
    ### 🧩 Example
    ```csharp
    public abstract class Animal
    {
    public abstract void MakeSound(); // Abstract method (no implementation)
    public void Eat() // Concrete method (implementation provided)
    {
    Console.WriteLine("Eating...");
    }
    }
    ```
2.   Can have fields, constructors, and static members:
-       Abstract classes can contain fields, constructors, and static members, which cannot be declared in an interface.
3.  Can inherit from another class:
-       An abstract class can inherit from another class and can implement interfaces.
4.  Access modifiers:
-       Abstract classes can have different access modifiers for methods, properties, and fields (e.g., public, protected).
5.  Can have state:
-       Abstract classes can maintain state in fields (instance variables).
### Use Case for Abstract Class:
-   When you want to inherit some common implementation across derived classes and share code.
-   When you want to provide default behavior for some methods but leave others to be implemented by derived classes.
-   When you want to define a common base class for a family of related objects, especially if you plan to share some implementation across all subclasses.
## <span style="background-color:#ff4d4d; color:white; padding:2px 6px; border-radius:4px;">High</span> <span style="background-color:#ff4d4d; color:white; padding:2px 6px; border-radius:4px;">High</span> <span style="background-color:#ff4d4d; color:white; padding:2px 6px; border-radius:4px;">High</span> Interfaces
An interface defines a contract, meaning it only defines method signatures and properties but no implementation. Any class that implements an interface must provide an implementation for all of its methods.
<br>An interface in C# is a contract that defines a set of methods, properties, events, or indexers without providing implementations. A class or struct that implements the interface must provide the implementation for its members.
### 🧩 Example

Syntax

```csharp
public interface IMyInterface
{
 // Methods
 void Method1();
 int Method2(string param);
 // Properties
 string Property1 { get; set; }
 // Events
 event EventHandler MyEvent;
 // Indexers
 string this[int index] { get; set; }
}
```
### Characteristics of Interface:

