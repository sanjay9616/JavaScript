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

<h1>distinct Operator</h1>

- distinct Operator will give all the values from the source Observable that are distinct when compared with the previous value.

```ts
ngOnInit() {
    from([1, 1, 3, 3, 5, 5, 5, 5, 6, 6])
      .pipe(distinct())
      .subscribe((data) => {
        console.log(data);
      })
}
```
**Output**
```
1
3
5
6
```

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