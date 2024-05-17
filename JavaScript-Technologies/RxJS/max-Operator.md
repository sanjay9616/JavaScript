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