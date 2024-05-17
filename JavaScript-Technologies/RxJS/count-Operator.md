<h1>count Operator</h1>

- count operator will give count of items taken as input.

```ts
ngOnInit() {
    from([1, 2, 3, 4, 5])
      .pipe(count())
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