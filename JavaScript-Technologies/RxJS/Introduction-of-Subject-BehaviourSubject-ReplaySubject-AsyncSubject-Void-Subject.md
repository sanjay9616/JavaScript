<h1>Introduction of RxJS Subject, BehaviourSubject, ReplaySubject, AsyncSubject, and Void Subject</h1>

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

<h2>BehaviourSubject</h2>

The BehaviourSubject is a variant of the Subject. This variant knows about the current value, which a normal Subject doesn't.

When there has already been sent data to the current subscribers, this Subject becomes very useful. But another subscriber get's introduced at a later moment. Sometimes you want to pass the current value to that subscriber. With the BehaviourSubject you can do that.

```ts
const subject = new BehaviorSubject(0); // 0 is the initial value

subject.subscribe({
    next: (v) => console.log(`observerA: ${v}`)
});

subject.next(1);
subject.next(2);

subject.subscribe({
    next: (v) => console.log(`observerB: ${v}`)
});

subject.next(3);
```
**Output**
```
observerA: 0
observerA: 1
observerA: 2
observerB: 2
observerA: 3
observerB: 3
```
So use the BehaviourSubject to give a subscriber the last known value of the Observable. But, what if you want a bit more than the previous value?

<h2>ReplaySubject</h2>

The ReplaySubject does what it says. It can replay a fixed amount of values to new subscribers.

```ts
const subject = new ReplaySubject(2); // buffer 3 values for new subscribers

subject.subscribe({
    next: (v) => console.log(`observerA: ${v}`)
});

subject.next(1);
subject.next(2);
subject.next(3);

subject.subscribe({
    next: (v) => console.log(`observerB: ${v}`)
});

subject.next(4);
subject.next(5);
```
**Output**
```
observerA: 1
observerA: 2
observerA: 3
observerB: 2
observerB: 3
observerA: 4
observerB: 4
observerA: 5
observerB: 5
```
As you can see, at the creation of the ReplaySubject(2), I passed the number 2, which tells the Subject that it needs to send the last two values to every new subscriber.

When that new subscriber received the passed values, it will stay in sync with the other subscriber, which is excellent.

But to make sure that the ReplaySubject(10000) won't pass constant values to every new subscriber, we can give it a time limit. The example below defines that it can keep a hundred values in memory and pass it to new subscribers, but those values are valid for 500 milliseconds.

`const subject = new ReplaySubject(100, 500);` This feature gives a lot of possibilities, so be smart with it.

<h2>AsyncSubject</h2>

When I saw the AsyncSubject and saw that it only sends the latest value to subscribers when it's completed.

So this gave an idea that an AsyncSubject is a great candidate for Ajax requests. Because with most GET requests, you're only going to wait for one response, right.

```ts
const subject = new AsyncSubject();

subject.subscribe({
    next: (v) => console.log(`observerA: ${v}`)
});

subject.next(1);
subject.next(2);
subject.next(3);
subject.next(4);

subject.subscribe({
    next: (v) => console.log(`observerB: ${v}`)
});

subject.next(5);
subject.complete();
```
**Output**
```
observerA: 5
observerB: 5
```
When you click the "run" button above, you will see that the AsyncSubject will pass multiple values, but only the last value before the complete() method is called will give to the subscribers.

<h2>Void Subject</h2>

In most of the scenarios where you use a Subject with subscribers, it's relevant that you get access to the value that has passed. But what if you don't need an actual value but only want to hook into the event and don't need a value. That's when you use a void subject.

```ts
const subject = new Subject(); // Shorthand for Subject<void>

subject.subscribe({
  next: () => console.log('One second has passed')
});

setTimeout(() => subject.next(), 1000);
```
This will not print anything

<h2>Conclusion</h2>

Let's wrap this up and conclude when you need a regular Observable or one of the Subject types.

**Use a Observable when..**: A regular Observable should be used when you only need one subscriber. Or you don't care that the subscriber that comes first will be finished first until the second will get its values.

**Use a Subject when..**: When you need multiple subscribers and care that all the subscribers are getting their new values simultaneously, you need a Subject.
- Use a **BehaviourSubject** when you need the last given value.
- Use a **ReplaySubject** when you need more than the last given value. (For example, the previous five values) Or you want to set a time window for the values can be validly sent to subscribers.
- Use an **AsyncSubject** when you only want the last value to be passed to the subscribers.
- Use a **Void Subject** if you don't want to pass any value but just want to hook into the event.

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>


