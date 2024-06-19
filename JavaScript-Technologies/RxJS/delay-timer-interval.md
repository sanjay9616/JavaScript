<h1>delay Operator</h1>

Delays the emission of items from the source Observable.

```ts
of(1, 2, 3)
      .pipe(delay(2000))
      .subscribe(value => console.log(`Received value: ${value}`));
```
**Output**
```
Received value: 1
Received value: 2
Received value: 3
```
In this example, the observable will emit the values 1, 2, and 3, each delayed by 2 seconds, and print at one time.

<h1>timer Operator</h1>

Creates an Observable that starts emitting after a given time and emits increasing numbers after each period of time thereafter. There is no source/input Observable here.

```ts
timer(5000, 500).subscribe((observer: any) => console.log("observer", observer));
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

<h1>interval Operator</h1>

Creates an Observable that emits sequential numbers every specified interval of time. There is no source/input Observable here as well.

```ts
interval(500).subscribe((observer: any) => console.log('interval', observer));
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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>