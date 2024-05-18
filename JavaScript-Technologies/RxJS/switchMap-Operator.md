<h1>switchMap Operator</h1>

- The switchMap operator will create a derived observable (called inner observable) from a source observable and emit those values.

```ts
ngOnInit() {
    of(1, 2, 3)
      .pipe(switchMap(x => of(x, x ** 2, x ** 3)))
      .subscribe((observer: any) => console.log("observer", observer))
}
```
**Output**
```
observer 1
observer 1
observer 1
observer 2
observer 4
observer 8
observer 3
observer 9
observer 27

```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>