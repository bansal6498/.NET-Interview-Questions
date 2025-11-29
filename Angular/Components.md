## Components
Components are the building blocks of an Angular application. Each component has:
-   A template (HTML)
-   A class (logic and data binding)
-   A stylesheet (CSS)
#### 🧩 Example
```typescript
// app.component.ts
import { Component } from '@angular/core';
@Component({
    selector: 'app-root',
    template: '<h1>Welcome to {{ title }}</h1>',
    styleUrls: ['./app.component.css']
})
export class AppComponent {
    title = 'Angular App';
}
```
