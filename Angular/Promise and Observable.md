## Promise and Observable
### Promise
A Promise is a representation of an asynchronous operation that will eventually return a value or an error. It is a one-time event that either resolves or rejects. Promises are often used for operations that return a single value (like fetching data from an API).
-   **Pending**: The initial state before the asynchronous operation finishes.
-   **Resolved**: The operation completed successfully.
-   **Rejected**: The operation failed.
```ts
const promise = new Promise((resolve, reject) => {
    let success = true;
    if(success) {
        resolve("Data fetched successfully");
    } else {
        reject("Data fetch failed");
    }
});
promise.then((message) => {
    console.log(message); // Will log "Data fetched successfully"
}).catch((error) => {
    console.log(error); // Will log "Data fetch failed"
});
```
### Observable
-   An Observable is a more powerful mechanism than a Promise for handling asynchronous operations, especially for multiple values over time (like streams of data).
-   Observables support operators like `map`, `filter`, `mergeMap`, etc., which allows more complex transformations.
-   Observables are lazy, meaning they don’t start emitting values until they are subscribed to.
```ts
import { Observable } from 'rxjs';
const observable = new Observable((observer) => {
    observer.next("Data 1");
    observer.next("Data 2");
    observer.complete();
});
observable.subscribe({
    next: (data) => console.log(data),
    complete: () => console.log("Completed")
});
```
### Promises vs Observable
-   **Single vs Multiple Values:** Promises emit a single value, while Observables can emit multiple values over time.
-   **Lazy vs Eager:** Observables are lazy, meaning they start emitting data only when subscribed to, whereas Promises begin execution immediately.
-   **Operators**: Observables provide operators like map, filter, and mergeMap for more flexible data transformations.