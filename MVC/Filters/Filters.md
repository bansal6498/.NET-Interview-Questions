###HTTP Filters
<br>
HTTP Filters in ASP.NET Core allow you to intercept HTTP requests and responses at various stages of the pipeline. They can be used to perform actions such as logging, exception handling, authentication, and more. 
<br>
In ASP.NET Core, filters are used to run code before or after the execution of controller actions. Filters are powerful tools for handling cross-cutting concerns such as logging, exception handling, authorization, caching, and more. Filters allow for better separation of concerns and can be applied globally, at the controller level, or at the action level.
<br>

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
```csharp
OnException
<br>
**Authorization Filters:** Used to determine whether a user has the necessary permissionsto execute the action.
Example: 
```csharp
IAuthorizationFilter
<br>
**Resource Filters:** Executed before any other filters, can be used to perform tasks like caching.
Example: 
```csharp
OnResourceExecuting and OnResourceExecuted
<br>