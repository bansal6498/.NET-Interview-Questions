## Memory Management
Memory management in .NET Core is automatically handled by the **Garbage Collector (GC)**, which is responsible for leaning up unused objects and reclaiming memory. However, improper memory management can still lead to **memory leaks.**
-   .NET uses Automatic Memory Management to handle memory allocation and deallocation.
-   **Heap**: The heap is used for dynamically allocated objects. When an object is created, it is allocated in the heap.
-   **Stack**: The stack is used for method calls and local variables.
-   **Garbage** Collection (GC): .NET uses garbage collection to automatically reclaim memory by removing objects that are no longer in use. The garbage collector identifies unused objects and frees their memory, preventing memory leaks.
-   Generational Approach: .NET GC divides objects into generations (0, 1, and 2) based on their lifetimes. Short-lived objects are collected more frequently, while long-lived objects are collected less frequently.
### How Garbage Collection Works?
-   The garbage collector runs automatically to clean up unreferenced objects, freeing up memory.
-   .NET Core uses a **generational garbage collection model** (Young Generation, Old Generation), where most objects are allocated in the young generation, and older objects are promoted to the old generation.
#### Generational Garbage Collection
-   **Young Generation:** New objects are allocated here. These objects are collected frequently.
-   **Old Generation:** Objects that survive several GC cycles are moved here. GC runs less frequently in the old  generation.
### Memory Leaks
Memory leaks occur when objects are still referenced even though they are no longer needed, preventing the garbage collector from reclaiming their memory.
#### Common causes of Memory Leaks:
1.  **Static references:** If an object is held in a static variable, it will not be garbage collected because the static variable keeps a reference to it.
2.  **Event Handlers:** If an object subscribes to an event but doesn't unsubscribe, the event handler holds a reference to the object, preventing it from being garbage collected.
3. **Unmanaged Resources:** While .NET Core’s GC manages memory for managed objects, it doesn't handle unmanaged resources (like file handles or database connections). These resources must be explicitly released.</br>
To handle unmanaged resources, implement the `IDisposable` interface and use `Dispose()` to clean up resources.
#### How to Prevent Memory Leaks:
-   **Dispose of Resources:** Always ensure you dispose of unmanaged resources by implementing the `IDisposable` interface.
-   **Avoid Static References:** Be mindful of static variables holding references to objects that should be garbage collected.
-   **Unsubscribe from Events:** Always unsubscribe from events to prevent objects from being held in memory unnecessarily.
-   **Use Weak References:** In certain cases, you can use weak references to allow garbage collection to clean up objects without breaking the reference chain.
-  **Use GC.SuppressFinalize()** to avoid the finalizer running if `Dispose()` has already been called manually.
-   **Finalizer (~)**: The finalizer is a special method that the garbage collector calls when the object is being collected. It is useful for cleaning up unmanaged resources if the developer forgets to call `Dispose()`.
### Dispose vs Finalize
-   Use **Dispose** for deterministic cleanup of resources.
-   Use **Finalize** as a safety net for unmanaged resource cleanup if Dispose isn’t called.

| 🔹 **Aspect** | **Dispose** | **Finalize** |
|----------------|----------------|----------------|
| Purpose | Explicitly releases resources. | Cleans up unmanaged resources as a backup. |
| Implementation | Implemented via the `IDisposable` interface. | Implemented as a destructor `(~ClassName).` |
| Call Mechanism | Called manually or via using. | Called automatically by the garbage collector. |
| Performance | Faster and deterministic. | Slower, non-deterministic, and depends on garbage collection. |
| Scope | Can release both managed and unmanaged resources. | Only releases unmanaged resources. |
| Usage | Recommended for deterministic cleanup. | Used as a last-resort mechanism. |
| Suppression | Use `GC.SuppressFinalize` to avoid Finalize. | Cannot suppress directly.|
#### Best Practices
1.  **Implement IDisposable:**
    -  Use Dispose for managed and unmanaged resources.
    -  Avoid relying solely on Finalize as it is non-deterministic.
2.  **Use the using Statement:**
    -   Ensures Dispose is called automatically and reliably.
3. **Suppress Finalization When Dispose Is Called:**
    -   Call `GC.SuppressFinalize(this)` within Dispose to optimize resource cleanup.
4. **Finalize Only When Necessary:**
    -   Use Finalize only if your class deals with unmanaged resources and does not expose Dispose.
#### How does mamory management works in this case? 
```csharp
public static void Main(String[] args) { 
    int x = 10; 
    String name = "C#"; 
    String name2 = "C#"; 
    String name3 = new string(name); 
    display(x, name); 
    } 
    public static void display(int number, String text) { 
        System.Console.WriteLine("Number: " + number); 
        System.Console.WriteLine("Text: " + text);
```
**Answer:**
This example mixes **value types (int)** and **reference types (string)**, so let’s break down what happens in memory management step by step.
1.  int x = 10;
    -   int is a **value type**.
    -   Stored **directly on the stack** (inside the Main method’s stack frame).
    -   So, x contains the value 10.
2. String name = "C#";
    -   "C#" is a **string literal**.
    -   String literals are stored in the **intern pool** (a special area in the managed heap maintained by the CLR).
    -   name (the variable) is on the **stack**, but it **points to the interned string object** on the **heap**.
3. String name2 = "C#";
    -   "C#" already exists in the **intern pool**.
    -   Instead of creating a new object, name2 will **reference the same heap object** as name.
    -   So name and name2 point to the **same memory location**.
4. String name3 = new string(name);
    -   new string(name) explicitly asks for a **new object**.
    -   Even though the content is "C#", this is **not interned** automatically.
    -   So a **new string object** is allocated on the **heap**, and name3 references it.
5. Calling display(x, name);
    -   x (10) is a **value type**, passed **by value** → a **copy** of 10 goes into number (stack).
    -   name (a reference to "C#") is a **reference type**, passed **by value** → a **copy of the reference** is given to text.
        -   That means both name (in Main) and text (in display) point to the **same heap object** "C#".

📌 Memory Snapshot</br>
Stack (Main Frame)
```csharp
x = 10
name → reference to interned "C#"
name2 → reference to interned "C#"
name3 → reference to new "C#"
```
Heap
```csharp
Intern Pool:  "C#"
Heap Object:  "C#" (new string, different from interned one)
```
Stack (Display Frame)
```csharp
number = 10
text → reference to interned "C#"
```
### 🔑 Key Points of Memory Management

-   Value types (`int`) live on the stack (copied when passed).
-   Reference types (`string`) store the reference on the stack, object itself lives on the heap.
-   String interning ensures literals like `"C#"` are stored once and reused.
-   `new string(...)` forces allocation of a s**eparate object**, bypassing interning.
-   Garbage Collector (GC) will eventually free `name3` (since it’s not interned), but interned strings live for the lifetime of the application domain.