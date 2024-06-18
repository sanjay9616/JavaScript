<h1>switchMap Operator</h1>

- The switchMap operator will create a derived observable (called inner observable) from a source observable and emit those values.
- `This operator is used to map each source value to an inner observable, and it only emits the values from the most recent inner observable. If a new source value arrives before the previous inner observable completes, it will switch to the new inner observable and unsubscribe from the previous one.`

```ts
ngOnInit() {
    const $switchMap = from([1, 2, 3, 4]).pipe(switchMap((data) => {
      return of(data).pipe(delay(500))
    }));

    $switchMap.subscribe(data => {
      console.log('switch map data', data); // switch map data 4
    })
}
```
```ts
const $switchMap = from([1, 2, 3, 4])
    .pipe(switchMap((data) => of(data).pipe(delay(500))))
    .subscribe((data) => {
      console.log('switch map data', data); // switch map data 4
  });
```
In this example, sourceObservable emits values every second. For each value emitted, switchMap creates an inner observable using from operator and emits the value from the source observable after a delay of one second. If a new value is emitted before the previous inner observable completes, it switches to the new inner observable and cancels the previous one. Therefore, only the most recent inner observable value will be emitted.

<h1>mergeMap Operator</h1>

- The concatMap operator will create a derived observable (called inner observable) from a source observable and emit those values.
- The concatMap operator is used to flatten the observable sequence of values. It maps each source value to an inner observable and subscribes to them in sequence, waiting for each to complete before subscribing to the next. This makes it particularly useful when you need to retrieve data from multiple APIs in sequence or process observables one after the other.
- `This operator maps each source value to an inner observable and merges the values from multiple inner observables into a single observable. It does not cancel or unsubscribe from any inner observables.`

```ts
const $mergeMap = from([1, 2, 3, 4])
    .pipe(mergeMap((data) => of(data).pipe(delay(500))))
    .subscribe((data) => {
      console.log('switch map data', data); // switch map data 4
  });
```
**Output**
```
switch map data 1
switch map data 2
switch map data 3
switch map data 4
```
In this example, sourceObservable emits three values: 1, 2, and 3. For each value emitted, mergeMap creates an inner observable using of operator and emits the value after a delay of one second. Since mergeMap does not cancel or switch between inner observables, all the values from each inner observable will be merged into a single observable and emitted in the order they complete.

<h1>concatMap Operator</h1>

`This operator maps each source value to an inner observable and concatenates the values from each inner observable sequentially. It waits for each inner observable to complete before moving on to the next one. Use concatMap over mergeMap when order is important for you.`

```ts
const $concatMap = from([1, 2, 3, 4])
  .pipe(concatMap((data) => of(data).pipe(delay(500))))
  .subscribe((data) => {
    console.log('switch map data', data); // switch map data 4
  });
```
**Output**
```
switch map data 1 // after 500 ms
switch map data 2 // after 500 ms
switch map data 3 // after 500 ms
switch map data 4 // after 500 ms
```
In this example, sourceObservable emits three values: 1, 2, and 3. For each value emitted, concatMap creates an inner observable using of operator and emits the value after a delay of one second. It waits for each inner observable to complete before moving on to the next one. Therefore, the values from each inner observable will be emitted sequentially in the order they were mapped.

<h1>exhaustMap Operator</h1>

`The exhaustMap operator works by mapping each source value to an observable, and then subscribing to that observable. It ensures that only one inner observable is active at a time. If a new source value arrives while an inner observable is still active, the new value is ignored until the inner observable completes.`

**Example 1:**

```ts
const $exhaustMap = from([1, 2, 3, 4])
  .pipe(exhaustMap((data) => of(data).pipe(delay(5000))))
  .subscribe((data) => {
    console.log('exhaustMap data', data);
  });
```
**Output**
```
exhaustMap data data 1
```

**Example 1:**

```ts
const $exhaustMap = from([1, 2, 3, 4])
  .pipe(exhaustMap((data) => of(data)))
  .subscribe((data) => {
    console.log('exhaustMap data', data);
  });
```
**Output**
```
exhaustMap data data 1
exhaustMap data data 2
exhaustMap data data 3
exhaustMap data data 4
```

<h1>forkJoin Operator</h1>

`This operator takes an array of observables and waits for all the source observables to complete. Once they all complete, it emits an array of the last emitted values from each observable.`

```ts
const observables = [of(1, 2, 3).pipe(delay(500)), from([10, 11, 12])];
forkJoin(observables).subscribe((data) => {
  console.log('forkjoin data', data); // forkjoin data [3,12]
})
```

In this example, forkJoin takes an array of observables, including two observables that emit ‘A’ and ‘B’ respectively after a delay, and an observable that throws an error after a delay. forkJoin waits for all the observables to complete, and once they complete, it emits an array of the last emitted values from each observable. However, if any of the observables in forkJoin throws an error, the error will be propagated to the error callback of the subscribe method.

<h1>combineLatest Operator</h1>

`This operator combines the latest values from multiple observables into a single observable. It emits an array of the latest values whenever any of the source observables emit a new value.`

**Example 1:**

```ts
const observables = [of(1, 2, 3).pipe(delay(500)), from([10, 11, 12])];
combineLatest(observables).subscribe((data) => {
  console.log('combineLatest data', data);
})
```
**Output**
```
combineLatest data [1, 12]
combineLatest data [2, 12]
combineLatest data [3, 12]
```
The console.log() output from the project function shows that the last emitted value from the first completed observable is used in all calculations. It is combined with each of the second observable values .Hence: if one observable emits values before the others do, then those values are lost.

**Example 2:**

```ts
const observables = [of([1, 2, 3]).pipe(delay(500)), from([10, 11, 12])];
combineLatest(observables).subscribe((data) => {
  console.log('combineLatest data', data);
})
```
**Output**
```
combineLatest data [[1, 2, 3], 12]
```

**Example 3:**

```ts
const observables = [from([1, 2, 3]).pipe(delay(500)), from([10, 11, 12])];
combineLatest(observables).subscribe((data) => {
  console.log('combineLatest data', data);
})
```
**Output**
```
combineLatest data [1, 12]
combineLatest data [2, 12]
combineLatest data [3, 12]
```

<h2>Regarding what happens if any of the requests fail in switchMap, mergeMap, or forkJoin</h2>

- **switchMap**: If any of the inner observables created by switchMap throws an error, the error will be propagated to the error callback of the subscribe method. Additionally, the subscription to the previous inner observable will be canceled, and switchMap will switch to the new inner observable.
- **mergeMap**: If any of the inner observables created by mergeMap throws an error, the error will be propagated to the error callback of the subscribe method. However, the error in one inner observable will not affect the other inner observables. mergeMap will continue to merge values from other inner observables.
- **forkJoin**: If any of the observables passed to forkJoin throws an error, the error will be propagated to the error callback of the subscribe method. In this case, forkJoin will not emit any result value. If you need to handle individual errors of each observable in forkJoin, you can use the catchError operator within each observable before passing them to forkJoin.









<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>