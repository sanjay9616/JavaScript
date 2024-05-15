<h1>From Operator</h1>

- From Operator will create an observable from an array, an array-like object, an iterable object, or observable-like object.
- Rememer it will always take an Array or Array like.

```ts
students: Observable<string> = from(["Ram", "Sita", "Gita"]);
```
**Example**
```ts
import { Component, OnInit } from '@angular/core';
import { Observable, from } from 'rxjs';

@Component({
  selector: 'app-rxjs',
  templateUrl: './rxjs.component.html',
  styleUrls: ['./rxjs.component.scss']
})
export class RxjsComponent implements OnInit {

  studentList: Observable<string> = from(["Ram", "Sita", "Gita"]);

  constructor() { }

  ngOnInit(): void {
    this.studentList.subscribe((data: string) => {
      console.log(data);
    })
  }

}
```
**Output**
```
Ram
Sita
Gita
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>
