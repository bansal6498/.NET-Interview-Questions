### Explain Object Call Bind in Angular
In Angular, Object Binding typically refers to **two-way binding** or **one-way binding**.
-   **One-way binding**: Data flows in one direction, either from the component to the view (`{{expression}}` in the template) or from the view to the component (`[(ngModel)]` for forms).
#### 🧩 Example
```html
<div>{{ name }}</div> <!-- One-way data binding -->
```
-   **Two-way binding:** This allows data to flow in both directions: from the component to the view, and from the view to the component. This is achieved using the ngModel directive.
#### 🧩 Example
```html
<input [(ngModel)]="name" /> <!-- Two-way data binding -->
```
### Binding in Angular:
-   **Property Binding:** Binds properties of HTML elements to component properties.
#### 🧩 Example
```html
<img [src]="imageUrl" />
```
-   **Event Binding:** Binds an event to a method.
#### 🧩 Example
```html
<button (click)="handleClick()">Click Me</button>
```
-   **Two-way Binding:** Combines property and event binding for form elements like inputs.
#### 🧩 Example
```html
<input [(ngModel)]="name" />
```
### ng run vs ng build vs ng serve
| 🔹 **Feature** | **ng run** | **ng build** | **ng serve** |
|----------------|----------------|----------------| ---------------|
| Purpose | Runs a specific architect target for a project, as defined in the angular.json file. | Compiles the application into static files that can be deployed to a web server. | Builds the app in memory and serve it using a local development server (with hot reloading) |
| When to Use | Used for custom configurations or executing a specific task, such as deploying an application or building it with specific options. | Used to prepare app for production by creating the `dist` folder with optimized, minified files. | Used for local development to view changes immediately in browser without needing to manually rebuild or restart the server. |
#### Conclusion
1. Use ng build:
    -   When preparing the app for deployment.
    -   To create optimized, production-ready static files.
2. Use ng serve:
    -   For local development and debugging.
    -   To take advantage of hot-reloading for faster iteration.
3. Use ng run:
    -   For running custom tasks, such as deploying the app or testing with specific configurations.
