## Unit Testing
Unit testing is the practice of testing individual units or components of a software system in isolation. The goal is to validate that each unit works as expected in isolation from the rest of the application. 
In .NET, unit tests are typically written using a unit testing framework, and several frameworks are available, including xUnit, NUnit, and MSTest. The most common practice is to write unit tests using these tools, and in many cases, mocking frameworks are used to simulate the behavior of dependencies.
### How to Perform Unit Testing in .NET?
You can perform unit testing in two main ways:
#### 1. Manual Testing:
-   This involves executing your application manually and inspecting its behavior. While useful for testing UI and  integration, manual testing is not efficient for unit testing because it doesn't provide repeatability and can be  error-prone.
#### 2. Automated Unit Testing with a Tool:
-   This is the most common approach, where you use unit testing frameworks such as xUnit, NUnit, or MSTest to write and run tests.
-   Automated tests are repeatable, maintainable, and provide faster feedback during development.
### xUnit Framework (Common for Unit Testing in .NET)
xUnit is one of the most popular frameworks for unit testing in .NET. It is designed to be simple, flexible, and based on best practices for writing testable code.
#### Basic Structure of xUnit Test
1. **Test Class:** A class that contains test methods.
2. **Test Methods:** Methods that are decorated with `[Fact]` or `[Theory]` attributes to indicate that they are test methods.
3. **Assertions:** Used to verify that the expected results match the actual results.
#### 🧩 Example
-   `[Fact]` indicates that this is a simple test with no parameters.
-   `Assert.Equal()` is used to check whether the result matches the expected output.
```csharp
using Xunit;
public class CalculatorTests
{
    [Fact]
    public void Add_WhenCalled_ReturnsSumOfArguments()
    {
        // Arrange
        var calculator = new Calculator();
        // Act
        var result = calculator.Add(2, 3);
        // Assert
        Assert.Equal(5, result);
    }
}
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}
```
### Mocking in Unit Testing
Mocking is a technique used in unit testing to isolate the unit under test by replacing its dependencies with "mock" objects. These mock objects simulate the behaviour of real objects in a controlled way.
Mocking is essential when your unit has dependencies that are difficult or slow to work with (like database connections, file systems, or external APIs).
#### Why use Mocking?
1. **Isolation:** You isolate the unit under test by replacing its dependencies with mock objects.
2. **Control**: You can control the behaviour of mock objects to simulate various scenarios (success, failure, etc.).
3. **Speed**: Mocks don't require real services (e.g., databases, APIs), making tests faster.
4. **Test Coverage**: It allows testing components without relying on the actual implementation of the dependencies.
#### 🧩 Example

1. **Mock**: We create a mock instance of the `ICalculatorService` interface.
2. **Setup**: `mockService.Setup(...)` defines the behavior of the mock object.
3. **Verify**: We test the `AddNumbers()` method of the Calculator class to see if it correctly uses the mock service and returns the expected result.

```csharp
using Xunit;
public interface ICalculatorService
{
    int Add(int a, int b);
}
public class Calculator
{
    private readonly ICalculatorService _calculatorService;
    public Calculator(ICalculatorService calculatorService)
    {
        _calculatorService = calculatorService;
    }
    public int AddNumbers(int a, int b)
    {
        return _calculatorService.Add(a, b);
    }
}
public class CalculatorTests
{
    [Fact]
    public void AddNumbers_WhenCalled_ReturnsCorrectSum()
    {
        // Arrange
        var mockService = new Mock<ICalculatorService>();
        mockService.Setup(service => service.Add(It.IsAny<int>(), It.IsAny<int>())).Returns(10);
        var calculator = new Calculator(mockService.Object);
        // Act
        var result = calculator.AddNumbers(3, 7);
        // Assert
        Assert.Equal(10, result);
    }
}
```
#### Mocking Frameworks
1.  **Moq**: The most popular mocking library for .NET. It works seamlessly with xUnit, NUnit, and MSTest.
2.  **NSubstitute**: Another mocking library that is known for its simplicity.
3.  **FakeItEasy**: A simple mocking library that's easy to use.
4. **Microsoft Fakes**: A part of Visual Studio, useful for creating stubs and mocks in enterprise environments.
#### Advantages of Mocking in Unit Testing
1.  **Isolation**: Mocking helps isolate the code you are testing by replacing dependencies with controlled mock objects.
2.  **Test Coverage**: You can test edge cases and exceptions by controlling the behavior of mock objects.
3.  **Speed**: Mocking does not require real services, databases, or external systems, making tests run faster.
4.  **Flexibility**: Mocking libraries often allow you to simulate various scenarios, including method calls and exceptions, without relying on actual implementation.
#### What is the difference between unit testing and integration testing?
**Answer:**
Unit testing focuses on testing individual units of code in isolation, whereas integration testing checks the interaction between different units or systems (e.g., database, APIs). Unit tests are faster and more isolated, while integration tests are broader and test the system as a whole.
#### What is the difference between [Fact] and [Theory] in xUnit?
**Answer:**
[Fact] is used for a simple test with no parameters, whereas [Theory] is used for parameterized tests where you can pass multiple sets of data to the same test method.
#### What is the role of assertions in unit testing?
**Answer:**
Assertions are used to verify that the actual outcome of a test matches the expected result. Common assertions include checking equality (`Assert.Equal()`), truthiness (`Assert.True()`), and exceptions (`Assert.Throws()`).
#### When should you use mocking in unit testing?
**Answer:**
You should use mocking when your unit depends on external systems or components that are difficult or slow to test (e.g., databases, APIs, or third-party services). Mocking helps simulate these dependencies, ensuring the unit test runs efficiently.
#### What are some common mocking libraries used in .NET?
**Answer:**
Popular mocking libraries in .NET include Moq, NSubstitute, FakeItEasy, and Microsoft Fakes.
#### How do you handle exceptions in unit tests?
**Answer:**
You can use assertions like `Assert.Throws<TException>()` to test whether a specific exception is thrown during the execution of a unit. This allows you to verify that your code correctly handles exceptional cases.
#### What is test-driven development (TDD)?
**Answer:**
Test-driven development (TDD) is a development practice where tests are written before the actual code. The process follows a cycle: write a failing test, write the code to make it pass, and then refactor the code.
Unit testing, when used with mocking, ensures that your code is thoroughly tested and behaves as expected, even when it depends on complex or external systems. This improves code quality, maintainability, and reliability.