## Sealed Class
A sealed class in C# is a class that cannot be inherited. This means that no other class can derive from a sealed class. The keyword `sealed` is used to mark a class as sealed.
#### 🧩 SYNTAX

`MyClass` is a sealed class, and you cannot inherit from `MyClass` in any other
class.

```csharp
public sealed class MyClass
{
    public void MyMethod()
    {
        Console.WriteLine("Hello from MyClass!");
    }
}
```
**Key Points about Sealed Class:**
1. **Inheritance Restriction:** A sealed class cannot be inherited.
#### 🧩 Example

This will give a compile-time error because `MyClass` is sealed.

```csharp
public class MyDerivedClass : MyClass
{
}
```
2.  **Instantiation**: You **can** instantiate a sealed class like any other class, because being sealed only restricts inheritance, not instantiation.
#### 🧩 Example
```csharp
MyClass myClass = new MyClass(); // Valid
```
3. **Performance Optimization:** The sealed keyword can help optimize performance. For example, in certain scenarios, the Just-In-Time (JIT) compiler can perform optimizations like inlining method calls, as it knows the class is not inheritable.
4. **Use Cases:** Sealed classes are typically used when you want to prevent inheritance for security reasons, to ensure no subclass overrides important functionality, or when designing immutable objects.

| 🔹 **Feature** | **Sealed** | **Private** |
|----------------|----------------|----------------|
| Purpose | Prevents inheritance.  | Restricts access to class members (fields, methods, properties). |
| Scope | Applies to the class, preventing it from being inherited. | Applies to members (fields, methods, etc.) within the class. |
| Inheritance | A sealed class **cannot be inherited.** | A private member **cannot be accessed **outside its containing class. |
| Access | A sealed class can be instantiated and used but cannot be subclassed. | A private member can only be accessed within the same class. |
| Example | `sealed class MyClass {} ` | `private int myField;` |
### Summary
-   **Sealed Class:** Prevents inheritance but allows instantiation.
-   **Private Members:** Restricts access to class members within the same class only.
-   **Instantiation of Sealed Class:** Yes, a sealed class can be instantiated. The sealed keyword affects inheritance, not instantiation.