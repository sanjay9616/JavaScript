<h1>Observable</h1>

- Observable emits data over a period of time.
- Observable needs to be subscribed else it won't do anything on its own!
- An Observer has 3 methods namely - **next**, **complete**, and **error**.

```ts
const observer = {
  next: x => console.log('Observer got a next value: ' + x),
  error: err => console.error('Observer got an error: ' + err),
  complete: () => console.log('Observer got a complete notification'),
};
```

```ts
import { Component, OnInit } from '@angular/core';
import { Observable } from 'rxjs';

@Component({
  selector: 'app-rxjs',
  templateUrl: './rxjs.component.html',
  styleUrls: ['./rxjs.component.scss']
})
export class RxjsComponent implements OnInit {

  agents!: Observable<string>;

  constructor() { }

  ngOnInit(): void {

    this.agents = new Observable((observer: any) => {
      try {
        observer.next("Ram");
        observer.next("Shyam");
        observer.next("Sita");
      } catch (err: any) {
        observer.error(err);
      }
    })

    this.agents.subscribe((data: any) => {
      console.log(data)
    })
  }

}
```
**Output:**
```
Ram
Shyam
Sita
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>