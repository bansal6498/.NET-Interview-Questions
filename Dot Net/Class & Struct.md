## Class & Struct
A `class` is a reference type, meaning it is stored on the heap, and variables hold references to the data.
A `struct` is a value type, meaning it is stored on the stack, and variables hold the actual data.
Classes support inheritance, whereas structs do not.
A `class` can have a default constructor, but a struct cannot have a parameter less constructor (unless explicitly defined).
A `struct` is a value type that is similar to a class, but it is stored on the stack (as opposed to a class, which is stored on the heap). Structs are often used for small, lightweight objects that contain only data and have no complex behaviour.
#### 🧩 Example
```csharp
public struct Point
{
 public int X;
 public int Y;
}
```
#### What is the Default Access Modifier of Class in C#?
**Answer:**</br>
Top-level class / abstract class → **internal** by default.</br>
Nested class → **private** by default.
1.  For a top-level class (including abstract class):
    -   The default access modifier is internal.
    -   Meaning: accessible only within the same assembly/project.
    #### 🧩 Example    
    ```csharp
    abstract class MyAbstractClass { }  // 👈 internal by default
    class MyClass { }                   // 👈 internal by default
    ```
    Equivalent to
    ```csharp
    internal abstract class MyAbstractClass { }
    internal class MyClass { }
    ```
2.  For a nested class (inside another class):
    -   The default access modifier is private.
    -   Meaning: only accessible inside the containing class.
    ```csharp
    class Outer
    {
        class Inner { }  // 👈 private by default
    }
    ```
    Equivalent to
    ```csharp
    class Outer
    {
        private class Inner { }
    }
    ```