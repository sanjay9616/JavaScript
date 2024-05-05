### Table of Contents

| No. | Questions                                                                 |
| --- | ------------------------------------------------------------------------- |
| 1   | [What is throttling](#What-is-throttling)                                 |
| 2   | [What is minimum timeout throttling](#What-is-minimum-timeout-throttling) |

### <h2>What is throttling</h2>

Throttling is a technique used to limit the execution of an event handler function, even when this event triggers continuously due to user actions. The common use cases are browser resizing, window scrolling etc.

The below example creates a throttle function to reduce the number of events for each pixel change and trigger scroll event for each 100ms except for the first event.

```js
const throttle = (func, limit) => {
    let inThrottle;
        return (...args) => {
            if (!inThrottle) {
            func.apply(this, args);
            inThrottle = true;
            setTimeout(() => (inThrottle = false), limit);
            }
        };
    };
    window.addEventListener("scroll", () => {
    throttle(handleScrollAnimation, 100);
});
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is minimum timeout throttling</h2>

Both browser and NodeJS javascript environments throttles with a minimum delay that is greater than 0ms. That means even though setting a delay of 0ms will not happen instantaneously. </br>
**Browsers:** They have a minimum delay of 4ms. This throttle occurs when successive calls are triggered due to callback nesting(certain depth) or after a certain number of successive intervals. </br>
Note: The older browsers have a minimum delay of 10ms.</br>
**Nodejs:** They have a minimum delay of 1ms. This throttle happens when the delay is larger than 2147483647 or less than 1.
The best example to explain this timeout throttling behavior is the order of below code snippet.

```javascript
function runMeFirst() {
    console.log("My script is initialized");
}
setTimeout(runMeFirst, 0);
console.log("Script loaded");
```

and the output would be in

```cmd
Script loaded
My script is initialized
```

If you don't use `setTimeout`, the order of logs will be sequential.

```javascript
function runMeFirst() {
    console.log("My script is initialized");
}
runMeFirst();
console.log("Script loaded");
```

and the output is,

```cmd
My script is initialized
Script loaded
```

**[⬆ Back to Top](#table-of-contents)**