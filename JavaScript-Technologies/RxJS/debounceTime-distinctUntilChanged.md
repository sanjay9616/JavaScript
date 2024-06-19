<h1><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Debouncing/README.md">debounceTime</a> Operator</h1>

- Emits a notification from the source Observable only after a particular time span has passed without another source emission.

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
import { debounceTime } from 'rxjs/operators';
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
      .pipe(debounceTime(500))
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

<h1>distinctUntilChanged Operator</h1>

- Emits a notification from the source Observable only after detect changes source emission(if they are distinct in comparison to the last value the result observable emitted).

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
import { debounceTime } from 'rxjs/operators';
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
      .pipe(debounceTime(500))
      .distinctUntilChanged((prev, next) => JSON.stringify(prev) === JSON.stringify(next))
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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>