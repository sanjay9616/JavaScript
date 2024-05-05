<h1>Throttling</h2>

Throttling is a technique used to limit the execution of an event handler function, even when this event triggers continuously due to user actions. The common use cases are browser resizing, window scrolling etc.

Throttling is used to call a function after every particular interval of time only the first event is triggers immediately.

The below example creates a throttle function to reduce the number of events for each pixel change and trigger scroll event for each 100ms except for the first event.

```js
const throttle = (func, limit = 1000) => {
    let inThrottle;
    return (...args) => {
        if (!inThrottle) {
            func.apply(this, args);
            inThrottle = true;
            setTimeout(() => (inThrottle = false), limit);
        }
    };
};
function fetchResults() {
    console.log("Fetching input suggestions");
}
window.addEventListener("scroll", throttle(() => fetchResults()));
```

**[⬆ Back to Top](#table-of-contents)**