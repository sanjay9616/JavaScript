<h1>take Operator</h2>

- Emits only the first count values emitted by the source Observable.

```ts
import { Component, OnInit } from '@angular/core';
import { interval } from 'rxjs';
import { take } from 'rxjs/operators';
@Component({
  selector: 'app-summary',
  templateUrl: './summary.component.html',
  styleUrls: ['./summary.component.scss']
})
export class SummaryComponent implements OnInit {

  constructor() { }

  ngOnInit() {
    interval(500)
      .pipe(take(2))
      .subscribe((observer: any) => console.log('observer', observer))
  }

}
```
**Output**
```
observer 0 // after 500 ms
observer 1 // after 500 ms
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>