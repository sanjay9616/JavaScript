<h1>Debouncing in Javascript</h2>

`Debouncing is a technique used to improve the performance of a feature by controlling the frequency of function calls. It delays the execution of a function until a certain amount of time has passed since the last invocation`.

Debouncing is a programming pattern that allows delaying execution of some piece of code until a specified time to avoid unnecessary _CPU cycles, API calls and improve performance_. The debounce function make sure that your code is only triggered once per user input. The common usecases are Search box suggestions, text-field auto-saves, and eliminating double-button clicks.

Let's say you want to show suggestions for a search query, but only after a visitor has finished typing it. So here you write a debounce function where the user keeps writing the characters with in 500ms then previous timer cleared out using `clearTimeout` and reschedule API call/DB query for a new time—300 ms in the future.

```javascript
function debounce(func, timeout = 500) {
    let timer;
    return (...args) => {
        clearTimeout(timer);
        timer = setTimeout(() => {
            func.apply(this, args);
        }, timeout);
    };
}
function fetchResults() {
    console.log("Fetching input suggestions");
}
const processChange = debounce(() => fetchResults());
```

The _debounce()_ function can be used on input, button and window events

**Input:**

```html
<input type="text" onkeyup="processChange()" />
```

**Button:**

```html
<button onclick="processChange()">Click me</button>
```

**Windows event:**

```html
window.addEventListener("scroll", processChange);
```

**In Angular you can use from rxjs library**
```typescript
import { debounceTime, distinctUntilChanged } from "rxjs";

.pipe(
    debounceTime(400),
    distinctUntilChanged((prev, next) => JSON.stringify(prev) === JSON.stringify(next))
)
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>