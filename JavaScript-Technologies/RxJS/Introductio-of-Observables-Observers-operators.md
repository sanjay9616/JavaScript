<h2>What is RxJS?</h2>

RxJS is a framework for reactive programming that makes use of Observables, making it easy to write asynchronous code. According to the official documentation, this project is a kind of reactive extension to JavaScript with better performance, modularity, and debuggable call stacks, while staying mostly backwards-compatible, with some changes that reduce the API surface. RxJS is the official library used by Angular to handle reactivity, converting pull operations for call-backs into Observables.

Rxjs consists of main 3 thing

1. Observable
2. Setalite data type (Observers, Schedulers, Subjects)
3. Operators (Array methods - map, filter, reduce etc)

In this article, we’ll cover:
- Pull vs Push system
- What is a Stream?
- What are Observables?
- What is an Observer?
- What is an operator?
- Comparing Observables, Observers, and operators in RxJS
- Observers and subscriptions?
- The Observable lifecycle
- Creating Observables and Observer
- The difference between Observables and Promises

<h2>Pull vs Push system</h2>

**Pull System:** In pull system the consumer asks for the data from the producer whenever requires.

```ts
let producer = () => 45;
let consumer = () => { let data = producer() } // 45
```

**Push system:** In push system the producer determines when to send the data to the consumer.

```ts
let producer = () => new Promise((resolve, reject) => {
  let count = 0;
  setInterval(() => {
    resolve(count++);
  }, 1000);
});

let consumer = data => { console.log(data); };

producer().then(consumer) // 0
```

<h2>What is a Stream?</h2>

A stream is a sequence of data values over time. This can range from a simple increment of numbers printed in six seconds (zero, one, two, three, four, five) or coordinates printed over time. This includes even the data value of inputs in form or chat texts passed through WebSockets or API responses. These all represent data values that will be collected over time, hence the name stream.

<h2>What are Observables?</h2>

Streams are important to understand because they are facilitated by RxJS Observables. An Observable is a function that can return a stream of values to an Observer over time, either synchronously or asynchronously. The data values returned can go from zero to an infinite range of values.

<h2>What is an Observer?</h2>

An Observer is an object that receives notifications from an Observable. An Observer has three methods: **next()**, **error()**, and **complete()**. These methods are called, respectively, by the Observable when new values are emitted, when an error occurs during the emission process, and when the Observable completes and will emit no more values.

Observers can be used to consume the values emitted by an Observable and to trigger side effects, such as updating a user interface or performing some computation.

<h2>What is an operator?</h2>

Operators are functions that are used to manipulate and transform Observable streams. Many different types of operators are available in RxJS, each serving a different purpose. Some common types of operators include:

- **Creation operators**: These are used to create new observable streams from scratch, using functions such as Observable.create, from ,interval, and of
- **Transformation operators**: These are used to transform the values emitted by an observable stream into new values, using functions such as map, pluck, scan, and switchMap
- **Filtering operators**: These are used to selectively emit values from an observable stream, based on certain conditions, using functions such as filter, take, skip, and distinct
- **Combination operators**: These are used to combine multiple observable streams into a single stream, using functions such as merge, combineLatest, and concat
Error handling operators: These are used to handle errors that occur in an observable stream, using functions such as catchError, retry, and throwError

Each Operator takes one or more observable streams as input and returns a new observable stream as output. Operators can be chained together to form complex data transformation pipelines, allowing you to manipulate and transform observable streams in powerful ways.

<h2>Comparing Observables, Observers, and operators in RxJS</h2>

Observables, operators, and observers are three fundamental concepts in RxJS that work together to create reactive and asynchronous programming patterns.

Observables represent a stream of data that can be subscribed to, allowing multiple values to be emitted over time. They provide methods for subscribing to the stream and handling its emissions. Observables can be seen as the source of data.

Operators, on the other hand, are functions that can be used to transform, filter, or combine data streams produced by Observables. They allow data modification as it flows through the stream, resulting in a new Observable with the transformed data stream. Operators can be chained together to create a pipeline of transformations on the data stream.

Observers are objects that can listen to an Observable and react to each value emitted by the Observable. They can execute custom logic in response to each emitted value, such as updating the UI or making additional API calls. Observers can be added to an Observable to listen for specific events at different stages of stream processing. Observers can be thought of as consumers of data.

<h2>Observers and subscriptions</h2>

For Observables to work, there need to be Observers and subscriptions. Observables are data source wrappers and then the Observer executes some instructions when there is a new value or a change in data values. The Observable is connected to the Observer who does the execution through subscription. With a subscribe method, the Observer connects to the Observable to execute a code block.

<h2>The Observable lifecycle</h2>

With some help from Observes and subscriptions, the Observable instance passes through these four stages throughout its lifetime:

- Creation
- Subscription
- Execution
- Destruction

<h2>Creating Observables and Observer</h2>

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

<h2>The difference between Observables and Promises</h2>

It’s important to note that while they share some similarities, Observables and Promises also have significant differences.

An Observable is an object that represents a stream of data that can be subscribed to, allowing multiple values to be emitted over time. Observables provide methods for subscribing to the stream and handling its emissions. On the other hand, Operators are functions that can be used to transform, filter, or combine data streams produced by Observables. Operators take an Observable as input and return a new Observable with the transformed data stream.

A Promise is a one-time operation that represents an asynchronous operation’s eventual completion or failure and can only return a single value. Once a Promise is resolved or rejected, its state cannot be changed. Promises are used in Angular for handling HTTP requests and other asynchronous operations.
