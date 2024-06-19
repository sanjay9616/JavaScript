<h1>first Operator</h1>

- First Operator will give thefirst value emitted by the source Observable.

```ts
ngOnInit() {
    range(1, 100)
    .pipe(first())
    .subscribe((data) => {
      console.log(data);
    })
}
```
**Output**
```
1
```

<h1>last Operator</h1>

- last Operator will give the last value emitted by the source Observable.

```ts
ngOnInit() {
    range(1, 100)
    .pipe(last())
    .subscribe((data) => {
      console.log(data);
    })
}
```
**Output**
```
100
```

<h1>elementAt Operator</h1>

- elementAt Operator will give a single value from the souce Observable based upon the index given.
- **Remember** its an array index, means it will always start with 0.

```ts
ngOnInit() {
    range(1, 100)
    .pipe(elementAt(0))
    .subscribe((data) => {
      console.log(data);
    })
}
```
**Output**
```
1
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>
