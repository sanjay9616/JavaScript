<h1>exhaustMap Operator</h1>

- The exhaustMap operator will create a derived observable (called inner observable) from a source observable and emit those values.
- The exhaustMap operator is used to flatten the observable sequence of values. It maps each source value to an inner observable and subscribes to them in sequence, waiting for each to complete before subscribing to the next. This makes it particularly useful when you need to retrieve data from multiple APIs in sequence or process observables one after the other.

```ts
ngOnInit() {
    of(1, 2, 3)
      .pipe(exhaustMap(x => of(x, x ** 2, x ** 3)))
      .subscribe((observer: any) => console.log("observer", observer))
}
```
**Output**
```
observer 1
observer 1
observer 1
observer 2
observer 4
observer 8
observer 3
observer 9
observer 27
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>