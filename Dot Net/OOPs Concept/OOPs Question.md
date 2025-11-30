## Question
#### 🟥 If a class have only private constructor then can we create object of it and can we inherit?
**Answer:**
1.  You cannot create an object of it outside the class because the constructor is not accessible.
    #### 🧩 Example
    ```csharp
    public class MyClass
    {
        private MyClass() { }

        public static void SayHello()
        {
            Console.WriteLine("Hello");
        }
    }
    // Outside
    // var obj = new MyClass(); // ❌ Compile error
    MyClass.SayHello(); // ✅ Works because static methods are accessible

    ```
    👉 Such classes are often used in Singleton pattern or static utility classes.
2.  Can it be inherited?
-   No, a class with only a private constructor cannot be inherited because:
    -   For inheritance, the derived class must call a constructor of the base class.
    -   But if the only constructor is private, it is not accessible to the derived class.
    #### 🧩 Example
    ```csharp
    public class BaseClass
    {
        private BaseClass() { }
    }

    public class Derived : BaseClass
    {
        // ❌ Error: BaseClass does not contain a constructor that is accessible
    }
    ```
    