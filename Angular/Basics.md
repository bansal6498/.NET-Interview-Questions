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
