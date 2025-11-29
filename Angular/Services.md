## Services
Services in Angular are used for business logic, data fetching, and other tasks that are shared across multiple components.
### Implementation:
-   Services are injected into components using Angular's dependency injection.
#### 🧩 Example
```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
@Injectable({
    providedIn: 'root'
})
export class DataService {
    constructor(private http: HttpClient) {}
    getData() {
        return this.http.get('https://api.example.com/data');
    }
}
```
### Usage in Component:
#### 🧩 Example
```ts
mport { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';
@Component({
    selector: 'app-data',
    templateUrl: './data.component.html',
    styleUrls: ['./data.component.css']
})
export class DataComponent implements OnInit 
{
    data: any;
    constructor(private dataService: DataService) {}
    ngOnInit() 
    {
        this.dataService.getData().subscribe((response) => {
        this.data = response;
    });
    }
}
```
