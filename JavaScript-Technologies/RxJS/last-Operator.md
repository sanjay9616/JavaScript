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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>