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