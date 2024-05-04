### Table of Contents

| No. | Questions                                                                                                               |
| --- | ----------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is a promise](#What-is-a-promise)                                                                                 |
| 2   | [Why do you need a promise](#Why-do-you-need-a-promise)                                                                 |
| 3   | [What are the three states of promise](#What-are-the-three-states-of-promise)                                           |
| 4   | [What are the main rules of promise](#What-are-the-main-rules-of-promise)                                               |
| 5   | [What is promise chaining](#What-is-promise-chaining)                                                                   |
| 6   | [What is promise.all](#What-is-promise.all)                                                                             |
| 7   | [What is the purpose of the race method in promise](#What-is-the-purpose-of-the-race-method-in-promise)                 |
| 8   | [What are the pros and cons of promises over callbacks](#What-are-the-pros-and-cons-of-promises-over-callbacks)         |
| 9   | [What are the differences between promises and observables](#What-are-the-differences-between-promises-and-observables) |
| 10  | [How do you prevent promises swallowing errors](#How-do-you-prevent-promises-swallowing-errors)                         |
| 11  | [How do you check an object is a promise or not](#How-do-you-check-an-object-is-a-promise-or-not)                       |
| 12  | [What is the easiest way to ignore promise errors](#What-is-the-easiest-way-to-ignore-promise-errors)                   |
| 13  | [What are asynchronous thunks](#What-are-asynchronous-thunks)                                                           |

### <h2>What is a promise</h2>

The Promise represents the completion of an asynchronous operation. It returns a single value based on the operation being rejected or resolved. There are mainly three stages of the Promise, which are shown below:

**Pending**: It is the initial state of each Promise. It represents that the result has not been computed yet.</br>
**Fulfilled**: It means that the operation has completed.</br>
**Rejected**: It represents a failure that occurs during computation.</br>

The syntax of Promise creation looks like below,


```javascript
const promise = new Promise(function (resolve, reject) {
    // promise description
});
```

The usage of a promise would be as below,

```javascript
const promise = new Promise(
    (resolve) => {
    setTimeout(() => {
        resolve("I'm a Promise!");
    }, 5000);
    },
    (reject) => {}
);

promise.then((value) => console.log(value));
```

### <h2>Why do you need a promise</h2>

Promises are used to handle asynchronous operations. They provide an alternative approach for callbacks by reducing the callback hell and writing the cleaner code.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the three states of promise</h2>

Promises have three states:

1. **Pending:** This is an initial state of the Promise before an operation begins </br>
2. **Fulfilled:** This state indicates that the specified operation was completed. </br>
3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the main rules of promise</h2>

A promise must follow a specific set of rules:

1. A promise is an object that supplies a standard-compliant `.then()` method </br>
2. A pending promise may transition into either fulfilled or rejected state </br>
3. A fulfilled or rejected promise is settled and it must not transition into any other state. </br>
4. Once a promise is settled, the value must not change.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is promise chaining</h2>

The process of executing a sequence of asynchronous tasks one after another using promises is known as Promise chaining. Let's take an example of promise chaining for calculating the final result,

```javascript
new Promise(function (resolve, reject) {
    setTimeout(() => resolve(1), 1000);
})
    .then(function (result) {
    console.log(result); // 1
    return result * 2;
    })
    .then(function (result) {
    console.log(result); // 2
    return result * 3;
    })
    .then(function (result) {
    console.log(result); // 6
    return result * 4;
    });
```

In the above handlers, the result is passed to the chain of .then() handlers with the below work flow,

1. The initial promise resolves in 1 second,
2. After that `.then` handler is called by logging the result(1) and then return a promise with the value of result \* 2. </br>
3. After that the value passed to the next `.then` handler by logging the result(2) and return a promise with result \* 3. </br>
4. Finally the value passed to the last `.then` handler by logging the result(6) and return a promise with result \* 4. </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is promise.all</h2>

Promise.all is a promise that takes an array of promises as an input (an iterable), and it gets resolved when all the promises get resolved or any one of them gets rejected. For example, the syntax of promise.all method is below,

```javascript
Promise.all([Promise1, Promise2, Promise3]) .then(result) => {   console.log(result) }) .catch(error => console.log(`Error in promises ${error}`))
```

**Note:** Remember that the order of the promises(output the result) is maintained as per input order.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of the race method in promise</h2>

Promise.race() method will return the promise instance which is firstly resolved or rejected. Let's take an example of race() method where promise2 is resolved first

```javascript
var promise1 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 500, "one");
});
var promise2 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 100, "two");
});

Promise.race([promise1, promise2]).then(function (value) {
    console.log(value); // "two" // Both promises will resolve, but promise2 is faster
});
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the pros and cons of promises over callbacks</h2>

Below are the list of pros and cons of promises over callbacks,

**Pros:**

1. It avoids callback hell which is unreadable </br>
2. Easy to write sequential asynchronous code with .then() </br>
3. Easy to write parallel asynchronous code with Promise.all() </br>
4. Solves some of the common problems of callbacks(call the callback too late, too early, many times and swallow errors/exceptions)

**Cons:**

1. It makes little complex code </br>
2. You need to load a polyfill if ES6 is not supported

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between promises and observables</h2>

Some of the major difference in a tabular form

| Promises                                                           | Observables                                                                              |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| Emits only a single value at a time                                | Emits multiple values over a period of time(stream of values ranging from 0 to multiple) |
| Eager in nature; they are going to be called immediately           | Lazy in nature; they require subscription to be invoked                                  |
| Promise is always asynchronous even though it resolved immediately | Observable can be either synchronous or asynchronous                                     |
| Doesn't provide any operators                                      | Provides operators such as map, forEach, filter, reduce, retry, and retryWhen etc        |
| Cannot be canceled                                                 | Canceled by using unsubscribe() method                                                   |

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you prevent promises swallowing errors</h2>

While using asynchronous code, JavaScript’s ES6 promises can make your life a lot easier without having callback pyramids and error handling on every second line. But Promises have some pitfalls and the biggest one is swallowing errors by default.

Let's say you expect to print an error to the console for all the below cases,

```javascript
Promise.resolve("promised value").then(function () {
throw new Error("error");
});

Promise.reject("error value").catch(function () {
throw new Error("error");
});

new Promise(function (resolve, reject) {
throw new Error("error");
});
```

But there are many modern JavaScript environments that won't print any errors. You can fix this problem in different ways,

1. **Add catch block at the end of each chain:** You can add catch block to the end of each of your promise chains

```javascript
Promise.resolve("promised value")
    .then(function () {
    throw new Error("error");
    })
    .catch(function (error) {
    console.error(error.stack);
    });
```

But it is quite difficult to type for each promise chain and verbose too.

2. **Add done method:** You can replace first solution's then and catch blocks with done method

```javascript
Promise.resolve("promised value").done(function () {
    throw new Error("error");
});
```

Let's say you want to fetch data using HTTP and later perform processing on the resulting data asynchronously. You can write `done` block as below,

```javascript
getDataFromHttp()
    .then(function (result) {
    return processDataAsync(result);
    })
    .done(function (processed) {
    displayData(processed);
    });
```

In future, if the processing library API changed to synchronous then you can remove `done` block as below,

```javascript
getDataFromHttp().then(function (result) {
    return displayData(processDataAsync(result));
});
```

and then you forgot to add `done` block to `then` block leads to silent errors.

3. **Extend ES6 Promises by Bluebird:**
Bluebird extends the ES6 Promises API to avoid the issue in the second solution. This library has a “default” onRejection handler which will print all errors from rejected Promises to stderr. After installation, you can process unhandled rejections

```javascript
Promise.onPossiblyUnhandledRejection(function (error) {
    throw error;
});
```

and discard a rejection, just handle it with an empty catch

```javascript
Promise.reject("error value").catch(function () {});
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check an object is a promise or not</h2>

If you don't know if a value is a promise or not, wrapping the value as `Promise.resolve(value)` which returns a promise

```javascript
function isPromise(object) {
    if (Promise && Promise.resolve) {
        return Promise.resolve(object) == object;
    } else {
        throw "Promise not supported in your environment";
    }
}

var i = 1;
var promise = new Promise(function (resolve, reject) {
resolve();
});

console.log(isPromise(i)); // false
console.log(isPromise(promise)); // true
```

Another way is to check for `.then()` handler type

```javascript
function isPromise(value) {
    return Boolean(value && typeof value.then === "function");
}
var i = 1;
var promise = new Promise(function (resolve, reject) {
    resolve();
});

console.log(isPromise(i)); // false
console.log(isPromise(promise)); // true
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the easiest way to ignore promise errors</h2>

The easiest and safest way to ignore promise errors is void that error. This approach is ESLint friendly too.

```js
await promise.catch((e) => void e);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are asynchronous thunks</h2>

The asynchronous thunks are useful to make network requests. Let's see an example of network requests,

```javascript
function fetchData(fn) {
fetch("https://jsonplaceholder.typicode.com/todos/1")
    .then((response) => response.json())
    .then((json) => fn(json));
}

const asyncThunk = function () {
    return fetchData(function getData(data) {
        console.log(data);
    });
};

asyncThunk();
```

The `getData` function won't be called immediately but it will be invoked only when the data is available from API endpoint. The setTimeout function is also used to make our code asynchronous. The best real time example is redux state management library which uses the asynchronous thunks to delay the actions to dispatch.

**[⬆ Back to Top](#table-of-contents)**
