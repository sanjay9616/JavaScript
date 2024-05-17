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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>
