## Delegates
A **delegate** is a type that defines a method signature and can hold references to methods with that signature. It is used to pass methods as arguments or define callback methods. Delegates are type-safe function pointers.
#### 🧩 Example
```csharp
public delegate void MyDelegate(string message);
public class Program
{
    public static void Main()
    {
        MyDelegate del = DisplayMessage;
        del("Hello from Delegate!");
    }
    public static void DisplayMessage(string message)
    {
        Console.WriteLine(message);
    }
}
```
