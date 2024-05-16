<h1>takeLast Operator</h1>

- Waits for the source to complete, then emits the last N values from the source, as specified y the count arguments.

**Example 1**

```ts
ngOnInit() {
    from(["Ram", "Sita", "Gita"])
      .pipe(takeLast(2))
      .subscribe((data) => {
        console.log(data);
      })
  }
```
**Output**
```
Sita
Gita
```
**Example 2**

```ts
ngOnInit() {
    range(1, 100)
    .pipe(takeLast(2))
    .subscribe((data) => {
      console.log(data);
    })
  }
```
**Output**
```
99
100
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>