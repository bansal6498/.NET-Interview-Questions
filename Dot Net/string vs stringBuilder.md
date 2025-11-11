### String vs StringBuilder

String: String is an immutable sequence of characters. When you modify a String, a new instance is created, and the original instance remains unchanged.
#### 🧩 Example
Since `String` is immutable, repeated concatenations can be inefficient, especially in loops.
```csharp
string str = "Hello";
str += " World"; // Creates a new string, "Hello World"
```
StringBuilder: `StringBuilder` is a mutable class that allows efficient string manipulation (like appending or inserting) without creating new instances.
#### 🧩 Example
StringBuilder is ideal for situations where you need to perform multiple string manipulations in a loop or dynamically change strings.
```csharp
StringBuilder sb = new StringBuilder("Hello");
sb.Append(" World"); // Modifies the original instance
```
#### Difference:
-   **Immutability (String)**: Strings are immutable, meaning every change creates anew object, making them less efficient for repeated changes.
-   **Mutability (StringBuilder)**: StringBuilder modifies the existing string, thus reducing memory usage and increasing performance for repetitive string operations.