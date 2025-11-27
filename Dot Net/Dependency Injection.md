## Dependency Injection in .Net Core
Dependency injection (DI) is a design pattern used to implement Inversion of Control (IoC). It helps to decouple class dependencies and makes the system more testable and maintainable. In .NET Core, DI is used to inject services like database contexts, logging services, and configuration objects into classes at runtime, promoting loose coupling.
Dependency Injection (DI) is a design pattern that helps to implement Inversion of Control (IoC). In .NET Core, DI is a first-class citizen, meaning that DI is deeply integrated into the framework, and services can be injected into classes such as controllers, views, middleware, and even other services. It promotes loose coupling between classes and improves maintainability and testability.
### How Dependency Injection Works in .NET Core
**1. Registering Services:**
-   You register services in the ConfigureServices method of the `Startup.cs` class. Services are registered with different lifetimes (transient, scoped, singleton).

**2. Injecting Services:**
-   Once services are registered, they can be **injected** into classes that require them. This is typically done via **constructor injection**, where the DI container automatically provides the requested services.
### Steps in DI Process in .NET Core
**1. Service Registration:**
During application startup, in `Startup.cs`, you register services to the DI container using the `IServiceCollection` interface. This defines how dependencies should be created and disposed of.
#### 🧩 Example
```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddTransient<IEmailService, EmailService>(); // Transient service
    services.AddScoped<IUserService, UserService>(); // Scoped service
    services.AddSingleton<ILogger, Logger>(); // Singleton service
}
```
**2. Service Resolution:**
Once the services are registered, you can request them anywhere in your application. The DI container automatically resolves the required dependencies and injects them.</br>
**Constructor Injection** is the most common way to inject dependencies into a class:
#### 🧩 Example
```csharp
public class HomeController : Controller
{
    private readonly IEmailService _emailService;
    private readonly IUserService _userService;
    public HomeController(IEmailService emailService, IUserService userService)
    {
        _emailService = emailService;
        _userService = userService;
    }
}
```
**3.    Service Lifetime Management:**
The DI container manages the lifetime of each service. For example:
-   Transient services are created each time they are requested.
-   Scoped services are created once per request.
-   Singleton services are created once and shared across all requests.

**4.    Automatic Dependency Injection:**
.NET Core automatically injects the dependencies into the class constructors. For example, in a controller, the required dependencies are injected when the controller is created by the framework.
### Benefits of Dependency Injection
-   **Loose Coupling:** DI allows you to decouple the components of your application. Classes don’t need to create their dependencies; they just declare what they need, and the DI container provides them.
-   **Testability:** DI makes it easier to test classes. Instead of tightly coupling dependencies, you can inject mock services or test implementations during unit testing.
-   **Configuration and Flexibility:** By using DI, it becomes easier to configure services and replace them with other implementations. For example, you can replace the `EmailService` with a mock or a different implementation in a testing environment.
-   **Separation of Concerns:** Classes focus only on their core responsibility while the DI container manages their dependencies.
#### DI in Action- Example
#### Service Interface
```csharp
public interface IEmailService
{
    void SendEmail(string recipient, string subject, string body);
}
```
#### Service Implementation
```csharp
public class EmailService : IEmailService
{
    public void SendEmail(string recipient, string subject, string body)
    {
        Console.WriteLine($"Sending email to {recipient}: {subject}");
    }
}
```
#### Controller
```csharp
public class HomeController : Controller
{
    private readonly IEmailService _emailService;
    public HomeController(IEmailService emailService)
    {
        _emailService = emailService;
    }
    public IActionResult Index()
    {
        _emailService.SendEmail("user@example.com", "Hello", "Welcome to our website!");
        return View();
    }
}
```
#### Startup.cs (DI Registration)
```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddTransient<IEmailService, EmailService>(); // Register EmailService as a Transient service
}
```
### Conclusion
-   Service Lifetimes in .NET Core (Transient, Scoped, Singleton) help control how services are created and managed, optimizing performance and memory usage.
-   Dependency Injection helps to decouple the application components, making it easier to manage dependencies, test components in isolation, and achieve more maintainable code. It is a core part of ASP.NET Core and enables the development of scalable and flexible applications.
