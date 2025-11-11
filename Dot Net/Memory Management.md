## Memory Management
Memory management in .NET Core is automatically handled by the **Garbage Collector (GC)**, which is responsible for leaning up unused objects and reclaiming memory. However, improper memory management can still lead to **memory leaks.**
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