<h1>take Operator</h2>

- Emits only the first count values emitted by the source Observable.

```ts
import { Component, OnInit } from '@angular/core';
import { interval } from 'rxjs';
import { take } from 'rxjs/operators';
@Component({
  selector: 'app-summary',
  templateUrl: './summary.component.html',
  styleUrls: ['./summary.component.scss']
})
export class SummaryComponent implements OnInit {

  constructor() { }

  ngOnInit() {
    interval(500)
      .pipe(take(2))
      .subscribe((observer: any) => console.log('observer', observer))
  }

}
```
**Output**
```
observer 0 // after 500 ms
observer 1 // after 500 ms
```

<h1>takeWhile Operator</h1>

- Emits values emitted by the source Observable so long as each values satisfies the given predicate, and then completes as soon as this predicate is not satisfied.

```html
<form [formGroup]="formGroup">
  <mat-form-field appearance="outline">
    <mat-label>Seach</mat-label>
    <input matInput formControlName="searchStr" placeholder="Search Here..." autocomplete="off">
  </mat-form-field>
</form>
```
```ts
import { Component, OnInit } from '@angular/core';
import { FormControl, FormGroup } from '@angular/forms';
import { debounceTime, takeWhile } from 'rxjs/operators';
@Component({
  selector: 'app-summary',
  templateUrl: './summary.component.html',
  styleUrls: ['./summary.component.scss']
})
export class SummaryComponent implements OnInit {

  formGroup!: FormGroup;

  constructor() { this.initializeFormGroup() }

  ngOnInit() {
    this.formGroup.get('searchStr')?.valueChanges
      .pipe(
        takeWhile((val: string) => val.length < 20),
        debounceTime(500)
        )
      .subscribe((observer: any) => {
        console.log('observer', observer)
      })
  }

  initializeFormGroup() {
    this.formGroup = new FormGroup({
      searchStr: new FormControl(''),
    });
  }
}
```
`It will emits value until the length of characters less then 20, else stops emiiting the value forever.`

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