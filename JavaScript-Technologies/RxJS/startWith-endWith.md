<h1>startWith Operator</h2>

The startWith operator takes an existing Observable and emits specific value immediately.

```ts
of(1, 2, 3)
      .pipe(startWith(0))
      .subscribe((observer: any) => console.log(observer));
```
**Output**
```
0
1
2
3
```

<h1>endWith Operator</h2>

The endWith operator takes an existing Observable and emits specific value after the source observable completes.

```ts
of(1, 2, 3)
      .pipe(endWith(0))
      .subscribe((observer: any) => console.log(observer));
```
**Output**
```
1
2
3
4
```