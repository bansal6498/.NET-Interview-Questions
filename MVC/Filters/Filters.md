### HTTP Filters
HTTP Filters in ASP.NET Core allow you to intercept HTTP requests and responses at various stages of the pipeline. They can be used to perform actions such as logging, exception handling, authentication, and more. 
<br>
In ASP.NET Core, filters are used to run code before or after the execution of controller actions. Filters are powerful tools for handling cross-cutting concerns such as logging, exception handling, authorization, caching, and more. Filters allow for better separation of concerns and can be applied globally, at the controller level, or at the action level.
<br>
### Types of HTTP Filter
**Action Filters:** Run before or after an action method is called. Used to manipulate data
before an action is executed.
Example: 
`OnActionExecuting and OnActionExecuted`
<br>
**Result Filters:** Run before or after an action result is executed. Can be used to modify the result before sending it back to the client.
Example: 
`OnResultExecuting and OnResultExecuted`
<br>
**Exception Filters:** Handle exceptions thrown by an action method. You can use them to log exceptions or return custom error responses.
Example: 
`OnException`
<br>
**Authorization Filters:** Used to determine whether a user has the necessary permissionsto execute the action.
Example: 
`IAuthorizationFilter`
<br>
**Resource Filters:** Executed before any other filters, can be used to perform tasks like caching.
Example: 
`OnResourceExecuting and OnResourceExecuted`
<br>
### How to implement Filter in ASP.NET Core
Filters can be implemented as attributes or by using the `IActionFilter` and `IExceptionFilter` interfaces.

Example of Action Filter:
```csharp
public class LoggingActionFilter : IActionFilter
{
    public void OnActionExecuting(ActionExecutingContext context)
    {
        Console.WriteLine("Action is executing");
    }
    public void OnActionExecuted(ActionExecutedContext context)
    {
        Console.WriteLine("Action has executed");
    }
}
```
<br>
Apply filter Globally:
You can apply the filter globally, at the controller level, or at the action level. This is ideal for scenarios where a filter, such as exception handling, needs to be applied to all requests.
<br>
To apply globally in `Startup.cs`:
`public void ConfigureServices(IServiceCollection services)
{
    services.AddControllersWithViews(options =>
    {
        options.Filters.Add(new LoggingActionFilter());
        options.Filters.Add(new CustomActionFilter());
    });
}`
<br>
Apply filter At the Controller Level:
Filters can be applied to all actions within a specific controller by adding them as attributes on the controller class.
`[ServiceFilter(typeof(CustomActionFilter))]
public class HomeController : Controller
{
    // All actions in this controller will use CustomActionFilter
}`
<br>
Apply filter At the Action Level:
Filters can be applied to a specific action method by adding them as attributes on that action.
`
[HttpGet]
[ServiceFilter(typeof(CustomActionFilter))]
public IActionResult GetProduct()
{
 // This action will use CustomActionFilter
 return View();
}
`
<br>
### Order of Execution of Filters
The filters in ASP.NET Core follow a specific order of execution, which determines when they will be executed during the request-response cycle:
1. Authorization Filters (run first)
2. Resource Filters
3. Action Filters
4. Result Filters
5. Exception Filters (if an exception occurs)

