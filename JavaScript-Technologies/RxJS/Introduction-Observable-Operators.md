<h1>What is RxJS (Reactive Extensions for JavaScript)</h1>

`What is RxJS (Reactive Extensions for JavaScript) is a library for reactive programming using observables that make it easier to compose asynchronous or callback based code.`

RxJS is a library for composing asynchronous and event-based programs by using obervable sequence. It provides one core type, the `observables`, `setalite types` (**Observer**, **Schedulers**, **Subjects**) and `operations` inspired by Array-extras (map, filter, reduce, every etc) to allow handling asynchronous events as collections

Rxjs consists of main 3 thing </br>
1. Observable </br>
2. Setalite data type (Observers, Schedulers, Subjects) </br>
3. Operators (Array methods - map, filter, reduce etc) </br>

**Observables:** An observables ia producer of multiple values, "pushing" them to Observer(Consumer).

**Subscriber:** It will listen to the Observable for data changes/updates.

**Reactive Programming:** Reactive programming is an asynchronous programming paradigm concerned with data stream and propogation of change.

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

<h1>Operators</h1>

- Operators are very important part of RxJS.
- Rxjs library provides a lot of useful operators which helps us write clean code and reduce lot of effors in writting custom logic, which leads to many bugs actually.
- An operator is a <a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Functions/README.md">pure fuction</a>.
- An operators takes in observable as Input and Output will also an Observable.

**Types of Operators:**
- Creation
- Mathetical
- Join
- Transforming
- Filtering
- Utility
- Conditional
- Multicasting
- Error handling

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>