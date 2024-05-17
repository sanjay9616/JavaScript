<h1>skip Operator</h1>

- skip Operator will give back an Observable that will skip the first occurance of count items taken as input.

```ts
ngOnInit() {
    from([1, 2, 3, 4, 5])
      .pipe(skip(2))
      .subscribe((data) => {
        console.log(data);
      })
}
```
**Output**
```
3
4
5
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>