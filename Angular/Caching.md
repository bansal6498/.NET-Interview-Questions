## Cache
Caching in Angular refers to the process of storing data temporarily to reduce the need for repeated requests or to improve performance. Caching helps in optimizing the loading time of applications by avoiding redundant operations, such as making multiple HTTP requests for the same data or performing complex calculations repeatedly.
### Types of Caching in Angular:
1.  HTTP Cache (API Response Caching):
    -   This involves caching HTTP responses so that the application doesn't repeatedly request the same data from a server.
    -   You can use HttpClient to make HTTP requests and cache responses locally, reducing the load on the server and improving performance.
2. Browser Cache (LocalStorage / SessionStorage / Cookies):
-   Browser caching allows you to store data directly in the browser using `LocalStorage`, `SessionStorage`, or `Cookies`.
    -   **LocalStorage** stores data persistently until explicitly removed.
    -   **SessionStorage** stores data for the duration of the session (until the browser is closed).
    -   **Cookies** store small pieces of data (typically less than 4KB) and can have an expiration time.
3. In-Memory Cache (Service-based caching):
-   In-memory cache is typically implemented within Angular services. The data is stored temporarily in a service (as an object or array) to avoid making repeated API calls during the lifecycle of a component.
#### What are the ways to Store Data in Angular?
**Answer:**
1.  In Memory Storage (Service Based Cache)
2.  Local Storage
3.  Session Storage
4.  Cookies
### In-Memory Storage (Service-based Cache):
-   The data is stored in the application memory for the current session. It is cleared when the page is refreshed or when the component is destroyed.
-   Example Use Case: Storing form data during navigation between pages in a single session.
-   A service is used to store and manage temporary data in the application's memory. This is suitable for data that only needs to exist during the current session or while navigating between components.
#### 🧩 Example
```ts
import { Injectable } from '@angular/core';
@Injectable({
    providedIn: 'root'
})
export class DataService {
        private tempData: any;
        setTempData(data: any) {
        this.tempData = data;
    }
    getTempData() {
        return this.tempData;
    }
    clearTempData() {
        this.tempData = null;
    }
}
```
#### Usage in a component:
```ts
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';
@Component({
selector: 'app-example',
templateUrl: './example.component.html'
})
export class ExampleComponent implements OnInit {
    constructor(private dataService: DataService) { }
    ngOnInit() {
        this.dataService.setTempData({ name: 'John Doe', age: 30 });
    }
    getData() {
    console.log(this.dataService.getTempData());
    }
    clearData() {
        this.dataService.clearTempData();
    }
}
```
###  Local Storage
-   The data is persistent and remains stored even if the browser is closed and reopened. It can be used for storing user preferences, themes, or non-sensitive data.
-   Example Use Case: Storing user authentication tokens or last session information.
-   `LocalStorage` allows you to store key-value pairs that persist even after the page is reloaded. It can hold up to 5MB of data per domain.
#### Example
```ts
// Set item in LocalStorage
localStorage.setItem('user', JSON.stringify({ name: 'John Doe', age: 30 }));
// Get item from LocalStorage
const user = JSON.parse(localStorage.getItem('user') || '{}');
console.log(user);
// Remove item from LocalStorage
localStorage.removeItem('user');
```
### SessionStorage
-   Similar to `LocalStorage`, but the data is cleared when the browser session ends (i.e., when the browser or tab is closed).
-   Example Use Case: Storing temporary data that should only be available during the current session, such as search filters.
-   `SessionStorage` is similar to `LocalStorage`, but the data is only available for the duration of the session. Once the browser tab is closed, the data is cleared.
#### Example
```ts
// Set item in SessionStorage
sessionStorage.setItem('sessionData', JSON.stringify({ key: 'value' }));
// Get item from SessionStorage
const sessionData = JSON.parse(sessionStorage.getItem('sessionData') || '{}');
console.log(sessionData);
// Remove item from SessionStorage
sessionStorage.removeItem('sessionData');
```
### Cookies
-   Cookies can store small pieces of data (like authentication tokens) that are sent to the server with each HTTP request. They are useful for stateful applications.
-   Example Use Case: Storing authentication tokens or other small user-specific data.
-   Cookies can store small amounts of data (usually up to 4KB) that is sent to the server with each HTTP request. They are typically used for storing authentication tokens or other small data that needs to persist across browser sessions.
```js
document.cookie = "username=JohnDoe; expires=Fri, 31 Dec 2024 23:59:59 GMT";
// Retrieve cookie
const cookies = document.cookie.split(';');
cookies.forEach(cookie => {
console.log(cookie);
});
// Delete cookie
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC";
```
For working with cookies in Angular, you can use libraries like `ngx-cookie-service`.
#### When to Use Each Storage Mechanism?
**Answer:**
-   **In-Memory Cache (Service-based)**: Use this for data that should only exist during the user session or within a specific view/component, e.g., form data.
-   **LocalStorage**: Use this for data that should persist even after the page is reloaded, such as user preferences or caching large datasets.
-   **SessionStorage**: Use this for data that should persist during the session but should not survive after the browser is closed, like shopping cart items.
-   **Cookies**: Use cookies for small, critical pieces of data that need to be shared with the server, like authentication tokens.
