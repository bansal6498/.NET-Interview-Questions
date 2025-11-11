## Polymorphism
## Method Overriding
-   Method overriding happens when a subclass provides a specific implementation of a method that is already defined in its superclass. It allows the subclass to modify the behavior of a method inherited from the parent class.
-   **Method name:** Must be the same.
-   **Input parameters:** Must have the exact same signature (number, type, and order of parameters).
-   Return type: Must be the same or covariant (a derived type of the return type in the base class).
-   Requires the `virtual`, `override`, or `abstract` keywords in C#.
-   **When to use:** When you need to provide specific behavior for a method in a derived class that is already defined in the base class.
-   **How to implement:** Use the `override` keyword in C#.
#### 🧩 Example
```csharp
class Animal
{
    public virtual void Sound()
    {
        Console.WriteLine("Animal makes a sound");
    }
}
class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Dog barks");
    }
}
// Usage:
Animal myAnimal = new Dog();
myAnimal.Sound(); // Output: Dog barks
```
## Method Overloading
-   Method overloading occurs when multiple methods with the same name but different parameters exist within the same class. The method's behaviour depends on the parameters passed to it.
-    **Method name:** Must be the same.
-   **Input parameters:** Must differ in number, type, or order.
-   **Return type:** The return type can be different, but it is not considered for method overloading resolution in C#.
-   **When to use:** When you want to create methods with the same name but different signatures (number or type of parameters).
#### 🧩 Example
```csharp
class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
    public double Add(double a, double b)
    {
        return a + b;
    }
    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }
}
// Usage:
Calculator calc = new Calculator();
Console.WriteLine(calc.Add(1, 2)); // Output: 3
Console.WriteLine(calc.Add(1.1, 2.2)); // Output: 3.3
Console.WriteLine(calc.Add(1, 2, 3)); // Output: 6
```
| 🔹 **Feature** | **Overloading** | **Overriding** |
|----------------|----------------|----------------|
| Method Name | Same | Same |
| Input Parametrs | Varies in type, number, or order | Must exactly match the base class method |
| Return Type | Not considered during resolution | Must match or be covariant with the base class method |