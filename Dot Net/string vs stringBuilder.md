## String vs StringBuilder

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
### String Pool
The String Pool (also called the Intern Pool) is a special memory area in the managed heap where the .NET runtime stores unique string literals.
When you create a string literal like "Hello", it is stored in the string pool.
If the same literal appears again in your program, the runtime does not create a new object—instead, it reuses the one in the pool.</br>
The String Pool is a special area in memory where CLR stores unique immutable string literals to save memory and improve performance
#### 🧩 Example
-   s1 and s2 both point to the same object in the string pool.
-   s3 creates a new string object on the heap, not pooled.
```csharp
string s1 = "Hello";
string s2 = "Hello";
string s3 = new string("Hello".ToCharArray());

Console.WriteLine(Object.ReferenceEquals(s1, s2)); // True (same pool object)
Console.WriteLine(Object.ReferenceEquals(s1, s3)); // False (new object)
```
#### Key Features of String Pool
-   Stored in Managed Heap → but managed by CLR for efficiency.
-   Immutable Strings → Since strings are immutable in C#, pooling is safe.
-   Automatic Pooling for Literals → All string literals in your program are pooled by default.
-   `String.Intern() `→ You can manually add strings to the pool.
#### Why to use String Pool
-   **Memory Optimization** → Only one copy of each unique literal is kept.
-   **Performance Boost** → Faster equality checks (reference comparison instead of character-by-character).