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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>