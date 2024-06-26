### Table of Contents

| No. | Questions                                                                                                                         |
| --- | --------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is RxJS](#What-is-RxJS)                                                                                                     |
| 2   | [What are the utility functions provided by RxJS](#What-are-the-utility-functions-provided-by-RxJS)                               |
| 3   | [What is subscribing](#What-is-subscribing)                                                                                       |
| 4   | [What are observables](#What-are-observables)                                                                                     |
| 5   | [What is an observer](#What-is-an-observer)                                                                                       |
| 6   | [What are observable creation functions](#What-are-observable-creation-functions)                                                 |
| 7   | [How do you perform error handling in observables](#How-do-you-perform-error-handling-in-observables)                             |
| 8   | [What is the shorthand notation for subscribe method](#What-is-the-shorthand-notation-for-subscribe-method)                       |
| 9   | [What is the difference between promise and observable](#What-is-the-difference-between-promise-and-observable)                   |
| 10  | [What is multicasting](#What-is-multicasting)                                                                                     |
| 11  | [What will happen if you do not supply handler for the observer](#What-will-happen-if-you-do-not-supply-handler-for-the-observer) |
| 12  | [What is an rxjs Subject](#What-is-an-rxjs-Subject)                                                                               |

### <h2>What is RxJS</h2>

RxJS is a library for composing asynchronous and callback-based code in a functional, reactive style using Observables. Many APIs such as  HttpClient produce and consume RxJS Observables and also uses operators for processing observables.

For example, you can import observables and operators for using HttpClient as below,
```javascript
import { Observable, throwError } from 'rxjs';
import { catchError, retry } from 'rxjs/operators';
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the utility functions provided by RxJS</h2>

The RxJS library also provides below utility functions for creating and working with observables.

1. Converting existing code for async operations into observables
2. Iterating through the values in a stream
3. Mapping values to different types
4. Filtering streams
5. Composing multiple streams

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are observables</h2>

Observables are declarative which provide support for passing messages between publishers and subscribers in your application. They are mainly used for event handling, asynchronous programming, and handling multiple values. In this case, you define a function for publishing values, but it is not executed until a consumer subscribes to it. The subscribed consumer then receives notifications until the function completes, or until they unsubscribe.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is subscribing</h2>

An Observable instance begins publishing values only when someone subscribes to it. So you need to subscribe by calling the `subscribe()` method of the instance, passing an observer object to receive the notifications.

Let's take an example of creating and subscribing to a simple observable, with an observer that logs the received message to the console.
```javascript
// Creates an observable sequence of 5 integers, starting from 1
const source = range(1, 5);

// Create observer object
const myObserver = {
    next: x => console.log('Observer got a next value: ' + x),
    error: err => console.error('Observer got an error: ' + err),
    complete: () => console.log('Observer got a complete notification'),
};

// Execute with the observer object and Prints out each item
source.subscribe(myObserver);
// => Observer got a next value: 1
// => Observer got a next value: 2
// => Observer got a next value: 3
// => Observer got a next value: 4
// => Observer got a next value: 5
// => Observer got a complete notification
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an observer</h2>

Observer is an interface for a consumer of push-based notifications delivered by an Observable. It has below structure,

```javascript
interface Observer<T> {
    closed?: boolean;
    next: (value: T) => void;
    error: (err: any) => void;
    complete: () => void;
}
```
A handler that implements the Observer interface for receiving observable notifications will be passed as a parameter for observable as below,

```javascript
myObservable.subscribe(myObserver);
```
**Note:** If you don't supply a handler for a notification type, the observer ignores notifications of that type.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are observable creation functions</h2>

RxJS provides creation functions for the process of creating observables from promises, events, timers and Ajax requests. Let us explain each of them with an example:

1. Create an observable from a promise
  ```javascript
  import { from } from 'rxjs'; // from function
  const data = from(fetch('/api/endpoint')); //Created from Promise
  data.subscribe({
   next(response) { console.log(response); },
   error(err) { console.error('Error: ' + err); },
   complete() { console.log('Completed'); }
  });
  ```
2. Create an observable that creates an AJAX request
  ```javascript
  import { ajax } from 'rxjs/ajax'; // ajax function
  const apiData = ajax('/api/data'); // Created from AJAX request
  // Subscribe to create the request
  apiData.subscribe(res => console.log(res.status, res.response));
  ```
3. Create an observable from a counter
  ```javascript
  import { interval } from 'rxjs'; // interval function
  const secondsCounter = interval(1000); // Created from Counter value
  secondsCounter.subscribe(n =>
    console.log(`Counter value: ${n}`));
  ```
4. Create an observable from an event
  ```javascript
  import { fromEvent } from 'rxjs';
  const el = document.getElementById('custom-element');
  const mouseMoves = fromEvent(el, 'mousemove');
  const subscription = mouseMoves.subscribe((e: MouseEvent) => {
    console.log(`Coordnitaes of mouse pointer: ${e.clientX} * ${e.clientY}`);
    });
  ```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you perform error handling in observables</h2>

You can handle errors by specifying an **error callback** on the observer instead of relying on `try`/`catch`, which are ineffective in asynchronous environment.

For example, you can define error callback as below,

```javascript
myObservable.subscribe({
    next(num) { console.log('Next num: ' + num)},
    error(err) { console.log('Received an errror: ' + err)}
});
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the shorthand notation for subscribe method</h2>

The `subscribe()` method can accept callback function definitions in line, for `next`, `error`, and `complete` handlers. It is known as shorthand notation or Subscribe method with positional arguments.

For example, you can define subscribe method as below,
```javascript
myObservable.subscribe(
    x => console.log('Observer got a next value: ' + x),
    err => console.error('Observer got an error: ' + err),
    () => console.log('Observer got a complete notification')
);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between promise and observable</h2>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is multicasting</h2>

Below are the list of differences between promise and observable:

| Observable                                                                                               | Promise                           |
| -------------------------------------------------------------------------------------------------------- | --------------------------------- |
| Declarative: Computation does not start until subscription, so they can run whenever you need the result | Executes immediately on creation  |
| Provides multiple values over time                                                                       | Provides only one                 |
| Subscribe method is used for error handling that facilitates centralized and predictable error handling  | Push errors to the child promises |
| Provides chaining and subscription to handle complex applications                                        | Uses only `.then()` clause        |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What will happen if you do not supply handler for the observer</h2>

Usually, an observer object can define any combination of `next`, `error`, and `complete` notification type handlers. If you don't supply a handler for a notification type, the observer just ignores notifications of that type.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an rxjs Subject</h2>

An RxJS Subject is a special type of Observable that allows values to be multicasted to many Observers. While plain Observables are unicast (each subscribed Observer owns an independent execution of the Observable), Subjects are multicast.

A Subject is like an Observable, but can multicast to many Observers. Subjects are like EventEmitters: they maintain a registry of many listeners.

``` typescript
import { Subject } from 'rxjs';

const subject = new Subject<number>();

subject.subscribe({
    next: (v) => console.log(`observerA: ${v}`)
});
subject.subscribe({
    next: (v) => console.log(`observerB: ${v}`)
});

subject.next(1);
subject.next(2);
```

**[⬆ Back to Top](#table-of-contents)**

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>












