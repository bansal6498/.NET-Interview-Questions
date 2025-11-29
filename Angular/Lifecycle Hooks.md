## Lifecycle Hooks
Angular provides a series of lifecycle hooks that allow developers to tap into key moments during the lifecycle of a component or directive. These hooks give you the ability to perform specific actions when Angular creates, updates, or destroys a component or directive.

Here are the main Angular lifecycle hooks:
1. **ngOnChanges:**
-   **When it’s called**: This hook is triggered whenever an input property of the component or directive changes.
-   **Purpose**: To respond to changes in input properties.
-   **Parameters**: It takes a SimpleChanges object that contains the previous and current values of the input properties.
```typescript
ngOnChanges(changes: SimpleChanges): void {
    console.log(changes);
}
```
2.  **ngOnInit:**
-   **When it’s called**: This hook is called once after the component's inputs are initialized.
-   **Purpose**: To perform any initialization logic that needs to occur once the component is created and inputs are bound.
```ts
ngOnInit(): void {
    console.log('Component initialized');
}
```
3. **ngDoCheck:**
-   **When it’s called:** This hook is called during every change detection cycle, even if there are no changes to input properties.
-   **Purpose:** To implement custom change detection logic.
```ts
ngDoCheck(): void {
    console.log('Change detection cycle');
}
```
4. **ngAfterContentInit:**
-   **When it’s called:** This hook is called once after Angular initializes content projected into the component (i.e., content inside `<ng-content>`).
-   **Purpose**: To respond to changes after content projection is complete.
```ts
ngAfterContentInit(): void {
    console.log('Content initialized');
}
```
5. **ngAfterContentChecked:**
-   **When it’s called:** This hook is called after Angular checks the content projected into the component.
-   **Purpose**: To perform any actions after content has been checked.
```ts
ngAfterContentChecked(): void {
    console.log('Content checked');
}
```
6. **ngAfterViewInit:**
-   **When it’s called**: This hook is called once after Angular initializes the component's views (i.e., after Angular first displays the component's template).
-   **Purpose**: To perform actions after the view (template) is initialized.
```ts
ngAfterViewInit(): void {
    console.log('View initialized');
}
```
7. **ngAfterViewChecked:**
-   **When it’s called**: This hook is called after Angular checks the component's views.
-   **Purpose**: To perform actions after the view has been checked for changes.
```ts
ngAfterViewChecked(): void {
    console.log('View checked');
}
```
8. **ngOnDestroy:**
-   **When it’s called**: This hook is called just before Angular destroys the component or directive.
-   **Purpose**: To perform cleanup tasks such as unsubscribing from observables, detaching event listeners, or cancelling any outstanding HTTP requests.
```ts
ngOnDestroy(): void {
    console.log('Component destroyed');
}
```
#### What is the lifecycle of a directive in Angular?
**Answer:**
The lifecycle of a directive is similar to that of a component. The main lifecycle hooks for a directive are:
-   **ngOnChanges:** Called when the directive’s input properties change.
-   **ngOnInit**: Called once the directive is initialized.
-   **ngDoCheck**: Called to check for changes in the directive.
-   **ngAfterViewInit**: Called after the directive's view has been initialized.
-   **ngOnDestroy**: Called when the directive is destroyed.</br>
These lifecycle hooks help manage the behaviour of the directive and react to changes in input properties, view initialization, and cleanup.