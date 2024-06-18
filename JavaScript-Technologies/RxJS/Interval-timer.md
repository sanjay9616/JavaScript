<h1>interval Operator</h1>

- Creates an Observable that emits sequential numbers every specified interval of time, on a specified SchedulerLike.
- Hands On Example `let numbers = interval(500);`

```ts
import { Component, OnInit } from '@angular/core';
import { interval } from 'rxjs';

@Component({
  selector: 'app-rxjs',
  templateUrl: './rxjs.component.html',
  styleUrls: ['./rxjs.component.scss']
})
export class RxjsComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
    interval(500).subscribe((observer: any) => console.log('interval', observer));
  }

}
```
**Output**
```
interval 0
interval 1 // after 500 ms
interval 2 // after 500 ms
interval 3 // after 500 ms
.
.
.

```

<h1>timer Operator</h1>

- Creates an Observable that emits sequential numbers after a delay, every specified interval of time, on a specified SchedulerLike.
- Hands On Example `let numbers = timer(5000, 500);`

```ts
ngOnInit() {
    timer(5000, 500).subscribe((observer: any) => console.log("observer", observer));
}
```
**Output**
```
observer 0 // after 5 sec
observer 0 // after 5 ms
observer 0 // after 5 ms
.
.
.
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>