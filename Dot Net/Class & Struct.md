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
