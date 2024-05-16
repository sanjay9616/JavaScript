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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>