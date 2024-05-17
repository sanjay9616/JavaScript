<h1>filter Operator</h1>

- filter Operator will give the values from source Observable based on the predicate function given.
- Very important operator and you will find yourself using this very often.

```ts
ngOnInit() {
    range(1, 10)
    .pipe(filter((v) => v % 2 == 0))
    .subscribe((data) => {
      console.log(data);
    })
}
```
**OR**
```ts
ngOnInit() {
    from([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
      .pipe(filter((v) => v % 2 == 0))
      .subscribe((data) => {
        console.log(data);
      })
}
```

**Output**
```
2
4
6
8
10
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>