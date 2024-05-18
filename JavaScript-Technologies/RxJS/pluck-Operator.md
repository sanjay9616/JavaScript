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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>