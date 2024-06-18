<h1>of Operator</h1>

- Make Observable from a string or array or an object.
- Whenever we want to paas a variable which has to be Observable instead of Array or String, we use Of Operator.

```ts
viewers: Observables<string[]> = of(["welcome", "to", "my", "github", "repository"]);
```

**Example**
```ts
import { Component, OnInit } from '@angular/core';
import { Observable, of } from 'rxjs';

@Component({
  selector: 'app-rxjs',
  templateUrl: './rxjs.component.html',
  styleUrls: ['./rxjs.component.scss']
})
export class RxjsComponent implements OnInit {

  studentList: Observable<string[]> = of(["Ram", "Sita", "Gita"])

  constructor() { }

  ngOnInit(): void {
    this.studentList.subscribe((data: string[]) => {
      console.log(data);
    })
  }

}
```
**Output**
```
["Ram", "Sita", "Gita"]
```

<h1>from Operator</h1>

- From Operator will create an observable from an array, an array-like object, an iterable object, or observable-like object.
- Rememer it will always take an Array or Array like.

```ts
students: Observable<string> = from(["Ram", "Sita", "Gita"]);
```
**Example**
```ts
import { Component, OnInit } from '@angular/core';
import { Observable, from } from 'rxjs';

@Component({
  selector: 'app-rxjs',
  templateUrl: './rxjs.component.html',
  styleUrls: ['./rxjs.component.scss']
})
export class RxjsComponent implements OnInit {

  studentList: Observable<string> = from(["Ram", "Sita", "Gita"]);

  constructor() { }

  ngOnInit(): void {
    this.studentList.subscribe((data: string) => {
      console.log(data);
    })
  }

}
```
**Output**
```
Ram
Sita
Gita
```

<h1>fromEvent Operator</h1>

- Creates an Observable that emits events of a specific type coming from the given event target.
- We can bind Target Elements and methods to make sure we got Observable as output.
- **Angular Specific-** We will use ViewChild, NativeElement as target element and bind event.

```html
<button #buttonId>I am a Button</button>
```
```ts
import { Component, ViewChild, OnInit, ElementRef } from '@angular/core';
import { fromEvent } from 'rxjs';

@Component({
  selector: 'app-rxjs',
  templateUrl: './rxjs.component.html',
  styleUrls: ['./rxjs.component.scss']
})
export class RxjsComponent implements OnInit {

  @ViewChild('buttonId') buttonIdVar!: ElementRef;

  constructor() { }

  ngOnInit(): void { }

  ngAfterViewInit() {
    fromEvent(this.buttonIdVar.nativeElement, 'click').subscribe((observer: any) => console.log('Button is Clicked!'));
    fromEvent(this.buttonIdVar.nativeElement, 'mouseover').subscribe((observer: any) => console.log('Hover Me!'));
    fromEvent(this.buttonIdVar.nativeElement, 'mouseout').subscribe((observer: any) => console.log('Hover Removed!'));
  }
}
```


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Technologies/RxJS/README.md"> 🔙 Back</a></h2>
