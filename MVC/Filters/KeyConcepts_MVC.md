## Key Concepts in MVC
### Routing
Routing is how incoming requests are mapped to controllers and actions. In ASP.NET Core MVC, routing is defined in Startup.cs, usually through attributes or a route template.
#### 🧩 Example

```csharp
[Route("products")]
public class ProductController : Controller
{
 [HttpGet]
 public IActionResult Index()
 {
 return View();
 }
 [HttpGet("{id}")]
 public IActionResult Details(int id)
 {
 var product = _productService.GetProductById(id);
 return View(product);
 }
}
```
### Action Methods
Action methods are methods in controllers that respond to incoming HTTP requests. Each action corresponds to a particular route or URL. Action methods can return various result types like `View(), Redirect(), Json(), or File()`.
### ViewModel
-   A ViewModel is a data structure that contains the data you want to display in your view, often aggregating multiple models. It is specifically designed for the view layer and helps in transferring data in a way that is optimized for rendering in the view.
-   A ViewModel is a class used to pass data from the controller to the view in ASP.NET MVC. It is designed to hold data that is needed specifically for rendering the view.  ViewModels are different from models in that they don’t directly map to the database; instead, they aggregate the data from one or more models to display in the UI.
#### 🧩 Example
```csharp
public class ProductViewModel
{
 public string Name { get; set; }
 public decimal Price { get; set; }
 public bool IsAvailable { get; set; }
}
```
### ViewBag
-   ViewBag is a dynamic object in ASP.NET MVC used to pass data from a controller to a view.
-   It stores data as key-value pairs and is dynamically resolved at runtime (no compile-time type checking).
-   It is useful for transferring small amounts of temporary data (e.g., messages, dropdown lists).<br>

**Features of ViewBag:**
1. Dynamic Property: No need for explicit casting; you can assign any type of data.
2. Short-Lived: Exists only during the current HTTP request (transient).
3. Ease of Use: Requires no complex setup or type declaration.
#### 🧩 Example

```csharp
//Controller Code
public ActionResult Index()
{
 ViewBag.Message = "Hello, World!";
 ViewBag.Number = 42;
 return View();
}
```
```html
//Razor Code
<h1>@ViewBag.Message</h1>
<p>The number is: @ViewBag.Number</p>
```
**Limitations**
-   No compile-time type checking (prone to runtime errors).
-   Not suitable for passing large or complex data.
### Bundling
Bundling refers to the practice of grouping multiple files (typically JavaScript or CSS files) into a single file. The idea is to reduce the number of HTTP requests that the browser needs to make to the server, which is important because each HTTP request involves overhead (such as the time it takes to establish a connection, process the request, etc.).<br>

**Why Use Bundling?**

Reduces the number of HTTP requests: Each file requires a separate HTTP request, so by bundling files together, you minimize the number of requests. It also Improves performance: With fewer HTTP requests, the browser can load resources more efficiently, leading to faster page loading.
#### 🧩 Example

In ASP.NET MVC, bundling is typically defined in the BundleConfig.cs file.

```csharp
public class BundleConfig
{
 public static void RegisterBundles(BundleCollection bundles)
 {
 // Bundle for JavaScript files
 bundles.Add(new ScriptBundle("~/bundles/jquery").Include(
 "~/Scripts/jquery-{version}.js"));
 // Bundle for CSS files
 bundles.Add(new StyleBundle("~/Content/css").Include(
 "~/Content/bootstrap.css",
 "~/Content/site.css"));
 }
}
```
Once the bundles are defined, you can include them in your views like this:

```csharp
@Scripts.Render("~/bundles/jquery")
@Styles.Render("~/Content/css")
```
### Minification
Minification refers to the process of removing unnecessary characters from a file, such as whitespace, comments, and newline characters, without affecting its functionality. This reduces the size of the file, which means less data needs to be transferred over the network, leading to faster page load times.

**Why Use Minification?**
-   **Reduces file size:** By removing unnecessary characters, you make the file smaller, which improves loading time.
-   **Reduces bandwidth usage:** Smaller files mean less data transfer, which is especially useful for mobile devices or users with limited bandwidth.
-   **Improves performance:** The browser needs to download smaller files, and rendering the page becomes faster.
#### 🧩 Example

Explain the example brieflIn ASP.NET MVC, minification is typically automatically done when you enable bundling,
especially when you build the application in Release mode.y here...

```csharp
public static void RegisterBundles(BundleCollection bundles)
{
 // Enable bundling and minification in release mode
 BundleTable.EnableOptimizations = true;
 // Define bundled and minified CSS
 bundles.Add(new StyleBundle("~/Content/css").Include(
 "~/Content/bootstrap.css",
 "~/Content/site.css"));

 // Define bundled and minified JavaScript
 bundles.Add(new ScriptBundle("~/bundles/jquery").Include(
 "~/Scripts/jquery-{version}.js"));
}
```
When you build the application in Release mode, ASP.NET automatically minifies the files. The output will have the unnecessary whitespace and comments removed. For example, a JavaScript file that originally contains spaces and line breaks would have those characters stripped out. 

**Tools for Minification:**
-   CSS Minification: Tools like YUI Compressor, CSSMin, or built-in ASP.NET MVC bundling.
-   JavaScript Minification: Tools like UglifyJS, Google Closure Compiler, or built-in ASP.NET MVC bundling.

Both techniques can be configured in the BundleConfig.cs file in an ASP.NET MVC application. These techniques are commonly enabled for production environments to optimize performance, whereas during development, you may disable them for ease of debugging. 