<h1>When Use RxJS Subject, BehaviourSubject, ReplaySubject, AsyncSubject, and Void Subject in Angular</h1>
https://dev.to/devbyrayray/when-use-rxjs-subject-behavioursubject-replaysubject-asyncsubject-or-void-subject-in-angular-4pn9

Angular has many types of Observables which you can use. Maybe you've seen Subject, BehaviourSubject, ReplaySubject, or AsyncSubject in Angular examples and wondering what they are and when you can use them.

<h2>What is a Subject?</h2>

An Observable is unicast. An Observer and its Subscriber have a one-to-one relationship. Each subscribed Observer owns an independent execution of the Observable.

<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--4IPZkxA4--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dpvu4v9pi9ifbnipoevd.jpg" alt="not found">

In comparison to a regular Observable, a Subject allows values to be multicasted to many Observers. A Subject and its subscribers have a one-to-many relationship.

A Subject can be an Observable as well as an Observer. They hold a registry of many listeners to multiple Observables.

<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--FW-9IrWm--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qbzuf0seclp885h3kjm8.jpg" alt="not found">

```ts
const observable = new Observable(subscriber => {
    subscriber.next(1);
    subscriber.next(2);
    subscriber.next(3);
    subscriber.complete();
});

console.log('just before subscribe');

// Subscriber 1
observable.subscribe({
    next(x) { console.log('sub1: got value ' + x); },
    error(err) { console.error('sub1: something wrong occurred: ' + err); },
    complete() { console.log('sub1: done'); }
});

// Subscriber 2
observable.subscribe({
    next(x) { console.log('sub2: got value ' + x); },
    error(err) { console.error('sub2: something wrong occurred: ' + err); },
    complete() { console.log('sub2: done'); }
});

console.log('just after subscribe');
```
**Output**
```
just before subscribe
sub1: got value 1
sub1: got value 2
sub1: got value 3
sub1: done
sub2: got value 1
sub2: got value 2
sub2: got value 3
sub2: done
just after subscribe
```
Here, you can see that the data is sent to the first subscriber and will finish before it continues to the next subscriber.

That's why every subscriber is running independently from each other. But the RxJS team offers a way to create "multicasted Obsevables."

```ts
const subject = new Subject();

// Subscriber 1
subject.subscribe({
    next: (v) => console.log(`observerA: ${v}`)
});

subject.next(1);

// Subscriber 2
subject.subscribe({
    next: (v) => console.log(`observerB: ${v}`)
});

subject.next(2);
```
**Output**
```
observerA: 1
observerA: 2
observerB: 2
```
With the Subject, you can see that the Subject takes the lead. It sends messages to both subscribers instead of waiting. In my opinion, this clearly shows the difference between a regular Observable and a Subject.

Internally to the Subject, subscribe does not invoke a new execution that delivers values. It simply registers the given Observer in a list of Observers, similarly to how addListener usually works in other libraries and languages.

<h2>Subject</h2>

We know that a Subject is an Observable. But instead of sending information to one subscriber, they can send their data to multiple subscribers simultaneously (they multicast).

A Subject has three methods which you can use.

- **subscribe** with this method, you can activate the subscription of a new subscriber.
- **next** with this method, you can pass new values. All the current subscribers will receive this.
- **complete** with this method, you close all the subscriptions to the Subject.

A vital detail is that a Subject doesn't have an initial value. Every value passed with the next method will send the values to all the subscribers.

But if the value is already sent before a subscriber is subscribed, it won't receive that data.

```ts
const subject = new Subject();

// Subscriber 1
subject.subscribe({
    next: (v) => console.log(`observerA: ${v}`)
});

subject.next(1);

// Subscriber 2
subject.subscribe({
    next: (v) => console.log(`observerB: ${v}`)
});

subject.next(2);
```

