<h1>tap Operator</h1>

- RxJS tap() operator is a utility operator that returns an observable output that is identical to the source observable but performs a side effect for every emission on the source observable.
- In other words, you can say that the RxJS tap() operator is used to intercept each emission on the source observable and runs a function but returns an output that is identical to the source observable as long as it doesn't find any error.
- This operator is generally used for debugging observables for the correct values or performing other side effects.

```ts
ngOnInit() {
    of(1, 2)
      .pipe(
        tap((val: any) => console.log(`BEFORE MAP: ${val}`)),
        map((val: any) => val + 10),
        tap((val: any) => console.log(`AFTER MAP: ${val}`))
      )
      .subscribe((observer: any) => console.log('observer', observer))
}
```
**Output**
```
BEFORE MAP: 1
AFTER MAP: 11
observer 11

BEFORE MAP: 2
AFTER MAP: 12
observer 12
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>
