<h1>max Operator</h1>

- Max Operator will take an Observable with all values and return an Observable with the max value.

```ts
ngOnInit() {
    from([1, 2, 3, 4, 5])
      .pipe(max())
      .subscribe((data) => {
        console.log(data);
      })
}
```
**Output**
```
5
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>