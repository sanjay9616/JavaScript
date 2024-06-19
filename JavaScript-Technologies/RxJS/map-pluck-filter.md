<h1>map Operator</h1>

- Creates an Observable that map each values from the emitted values.

```ts
ngOnInit() {
    from([1, 2, 3, 4, 5])
      .pipe(map((v) => v * 2))
      .subscribe((observer: any) => console.log('observer', observer))

}
```
```
observer 2
observer 4
observer 6
observer 8
observer 10
```

<h1>pluck Operator</h1>

- Like map , but meant only for picking one of the nested properties of every emitted value. Given a list of strings or numbers describing a path to a property, retrieves the value of a specified nested property from all values in the source Observable

```ts
ngOnInit() {
    from([
      { name: 'Joe', age: 30 },
      { name: 'Sarah', age: 35 }
    ])
      .pipe(pluck('name'))
      .subscribe((observer: any) => console.log('observer', observer))

}
```
**Output**
```
observer Joe
observer Sarah
```

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