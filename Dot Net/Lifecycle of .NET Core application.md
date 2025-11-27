## Lifecycle of .NET Core Applicatiom
**1.   Application Startup (Program.cs and Startup.cs)**
-   Program.cs: The entry point of a .NET Core application. The CreateHostBuilder method sets up and configures the web host, which includes settings like logging, configuration, and server options.
-   Startup.cs: This class is where you configure services and middleware for your application. It has two main methods:
    -   **ConfigureServices**: Registers services like dependency injection (DI), database contexts, identity services, etc.
    -   **Configure**: Defines the HTTP request pipeline by setting up middleware components (e.g., routing,  authentication, authorization, MVC, etc.).

**2.    Middleware Pipeline**
In ASP.NET Core, middleware is software that is used in the HTTP request-response pipeline. Middleware is executed in the order it's added to the pipeline in the Configure method in `Startup.cs`.
-   **Order Matters:** The sequence in which you add middleware components is crucial, as they execute in the order they're registered.
-   **Common Middleware**: Includes things like:
    -   `UseRouting():` Defines how requests are routed.
    -   `UseAuthentication()`: Handles user authentication.
    -   `UseAuthorization()`: Handles user authorization.
    -   `UseEndpoints()`: Maps routes to controllers or pages.
        
**3.    Dependency Injection (DI) and Service Registration-**
ASP.NET Core has built-in support for Dependency Injection (DI), which means services are registered and injected into components like controllers, middleware, and other services.
-   **Service Registration:** Services like logging, database contexts, or custom services are registered in the    `ConfigureServices` method.

**4.    Request Handling**
When an HTTP request is made, it follows this general flow:
1.  Request Routing: The request is routed by the ASP.NET Core router to the appropriate controller or endpoint.
2.  Controller Execution: The appropriate controller is instantiated, and its action method is executed. If any dependencies are required, they are injected automatically.
3.  Action Execution: The controller action executes its logic and returns a result (e.g., a view, JSON, etc.).
4.  Response: The result is returned to the client as an HTTP response.

**5.    MVC (Model-View-Controller) Pipeline**- 
ASP.NET Core uses the MVC pattern for handling requests. When a request is routed to an MVC controller:
1.  **Controller:** A controller class handles the HTTP request.
2.  **Action:** The controller action method processes the request and can return a view, redirect, or JSON data.
3.  **View:** If the action returns a view, the view engine (Razor, for example) renders the HTML.
4.  **Result:** The result is returned to the client.

**6.    Filters** allow you to add custom logic during different stages of the request processing pipeline in ASP.NET Core. The most common filter types are:
-   **Authorization filters:** Run first and are used for user authentication.
-   **Action filters:** Run before or after an action method executes.
-   **Result filters:** Run before or after the result is executed (e.g., before rendering a view).
-   **Exception filters:** Run when an exception is thrown.

**7.    Response Handling** Once the controller action is completed and the result is generated, the response is passed back
through the middleware pipeline for any final steps such as logging or content encoding.
-   **Response Result:** The result could be an HTML page, JSON, or file, depending on the controller’s action.

**8.    Application Shutdown** When the application shuts down, ASP.NET Core performs a graceful shutdown:
-   **Dispose Services:** It disposes of services and resources registered in the DI container.
-   **Logging:** Logs shutdown events.</br>

ASP.NET Core allows you to hook into the shutdown process using `IHostApplicationLifetime` or `IHost`.</br>

Summary of .NET Core Application Lifecycle
1. Program Initialization: Program.cs starts the application.
2. Service Configuration: Services and middleware are configured in Startup.cs.
3. Middleware Execution: The request is processed through the middleware pipeline.
4. Routing & Controller Execution: The request is routed to a controller, and the controller
action is executed.
5. Response Handling: The result is sent back to the client.
6. Shutdown: The application shuts down gracefully, cleaning up resources.
#### How Code Compilation in .NET Works?
**Answer:**
.NET code compilation involves multiple steps:
1. **Source Code:** The developer writes code in a high-level language like C# or F#.
2. **Compilation to Intermediate Language (IL):** The C# code is compiled by the C# compiler (csc) into an Intermediate Language (IL), which is a CPU-independent, platform-neutral code.
3. **Assembly:** The IL code is packaged into an assembly (DLL or EXE), which also contains metadata, type information, and references.
4. J**ust-In-Time (JIT) Compilation:** When the program runs, the Common Language Runtime (CLR) loads the IL code and converts it to machine code specific to the CPU architecture (x86, x64, ARM) using JIT compilation. This step occurs at runtime.
5. **Execution:** The JIT-compiled code runs directly on the hardware, using runtime services like garbage collection and exception handling.
#### How C# Program Execution Takes Place?
**Answer:**
1. **Code Writing:** The developer writes code in C#.
2. **Compilation to IL:** The C# code is compiled by the C# compiler (csc) to Intermediate Language (IL), which is platform-independent.
3. **Assembly Creation:** The IL code is packed into an assembly (DLL or EXE) which includes metadata.
4. **Loading:** When the program is executed, the Common Language Runtime (CLR) loads the assembly into memory.
5. **JIT Compilation:** The CLR uses the Just-In-Time (JIT) compiler to translate IL code into machine code for the specific CPU at runtime.
6. **Execution:** The machine code is executed by the processor, with the CLR managing memory (via garbage collection), exception handling, and other runtime services.