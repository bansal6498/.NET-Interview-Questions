## Protected Class
-   **Access Level:** The protected modifier allows access to a member from **within the same class** and **derived classes** (subclasses). This means that members marked as protected can be accessed by the class itself and any class that inherits from it.</br>
-   **Visibility:** A protected member is **not accessible** from outside the class hierarchy. It can only be accessed within the class or its derived classes.</br>
-   **Use Case:** It is commonly used when you want to allow access to certain members in derived classes but keep them hidden from the general public (i.e., other classes that do not inherit from the class).</br>

| 🔹 **Feature** | **Private** | **Protected** |
|----------------|----------------|----------------|
| Access | Can only be accessed within the same class. | Can be accessed within the same class and derived classes. |
| Inheritance | Not accessible in derived classes. | Accessible in derived classes. |
| Visibility Outside the Class | Not visible at all outside the class. | Not visible outside the class or derived  lasses. |
| Use Cases | Used for internal class details. | Used when you want to allow access to derived classes but hide from outside classes. |
### When to use
Use `protected` when you want to expose certain members to derived classes but keep them hidden from the general public. This is useful when building class hierarchies and you want to provide access to base class members to subclasses while
still protecting them from outside access.
### public, private, protected, and internal in C#
-   **public**: Members are accessible from anywhere.
-   **private**: Members are accessible only within the same class or struct.
-   **protected**: Members are accessible within the same class or any derived class.
-   **internal**: Members are accessible within the same assembly but not outside it.