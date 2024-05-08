### Table of Contents

| No. | Questions                                                                                                                 |
| --- | ------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are lambda or arrow functions](#What-are-lambda-or-arrow-functions)                                                 |
| 2   | [What is a first class function](#What-is-a-first-class-function)                                                         |
| 3   | [What is a first order function](#What-is-a-first-order-function)                                                         |
| 4   | [What is a higher order function](#What-is-a-higher-order-function)                                                       |
| 5   | [What is a unary function](#What-is-a-unary-function)                                                                     |
| 6   | [What is a pure function](#What-is-a-pure-function)                                                                       |
| 7   | [What are the differences between pure and impure functions](#What-are-the-differences-between-pure-and-impure-functions) |
| 8   | [What is IIFE(Immediately Invoked Function Expression)](#What-is-IIFE(Immediately-Invoked-Function-Expression))           |
| 9   | [What is a thunk function](#What-is-a-thunk-function)                                                                     |
| 10  | [What is an Asynchronous Thunks](#What-is-an-Asynchronous-Thunks)                                                         |
| 11  | [What is async function](#What-is-async-function)                                                                         |
| 12  | [How to use await outside of async function prior to ES2022](#How-to-use-await-outside-of-async-function-prior-to-ES2022) |

### <h2>What are lambda or arrow functions</h2>

`An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.`

```js
const addTwo = (a, b) => {
    return a + b;
}
console.log(addTwo(4, 5)) // 9

// ########### OR ########### //

const addTwo = (a, b) => (a + b) // if you use () then don't need return statement
console.log(addTwo(4, 5)) // 9
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a first class function</h2>

In Javascript, functions are first class objects. First-class functions means when functions in that language are treated like any other variable.

For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable. For example, in the below example, handler functions assigned to a listener

```javascript
const handler = () => console.log("This is a click handler function");
document.addEventListener("click", handler);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a first order function</h2>

A first-order function is a function that doesn’t accept another function as an argument and doesn’t return a function as its return value.

```javascript
const firstOrder = () => console.log("I am a first order function!");
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a higher order function</h2>

A higher-order function is a function that accepts another function as an argument or returns a function as a return value or both.

```javascript
const firstOrderFunc = () => console.log("Hello, I am a First order function");
const higherOrder = (ReturnFirstOrderFunc) => ReturnFirstOrderFunc();
higherOrder(firstOrderFunc);
```
**Example**

```js
firstOrderFunc = (name) => {
	return `Hi!! ${name} `;
}

higherOrder = (greeting, message, name) => {
	console.log(`${greeting(name)} ${message}`);
}

higherOrder(firstOrderFunc, 'Welcome To GeeksForGeeks', 'Geeks'); // Hi!! Geeks  Welcome To GeeksForGeeks
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a unary function</h2>

A unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for a single argument accepted by a function.

Let us take an example of unary function,

```javascript
const unaryFunction = (a) => console.log(a + 10); // Add 10 to the given argument and display the value
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a pure function</h2>

`A Pure Function is a function that always produces the same output for the same input` with multiple calls (out doesn't chaned with multiple calls), without any side effect.

```js
const add = (a, b) => { // Pure Function
    return a + b
}
console.log(add(3, 4)) // 7
console.log(add(3, 4)) // 7
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between pure and impure functions</h2>

**Pure Function:** `A Pure Function is a function that always produces the same output for the same input` with multiple calls (out doesn't chaned with multiple calls), without any side effect.

```js
const add = (a, b) => { // Pure Function
    return a + b
}
console.log(add(3, 4)) // 7
console.log(add(3, 4)) // 7
```

**Impure Function:** `An Impure Function is a function that produces the different output for the same input` with multiple calls (output changed with multiple calls), It has side effect.

```js
let total = 0
const addToTotal = (a, b) => { // Impure Function
    total = a + b + total
    return total
}
console.log(addToTotal(3, 4)) // 7
console.log(addToTotal(3, 4)) // 14
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is IIFE(Immediately Invoked Function Expression)</h2>

Immediately Invoked Function Expressions (IIFE) are JavaScript functions that are executed immediately after they are defined. They are typically used to create a local scope for variables to prevent them from polluting the global scope.

```js
(function abc() {
    console.log('DB Connected')
})();
```
**OR**
```js
(() => {
    console.log('DB Connected')
})();
```
```js
((dbName) => { // with parameter
    console.log(`${dbName} is Connected`)
})('UserDetails');
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a thunk function</h2>

A thunk is just a function which delays the evaluation of the value. It doesn’t take any arguments but gives the value whenever you invoke the thunk. i.e, It is used not to execute now but it will be sometime in the future. Let's take a synchronous example,

```javascript
const add = (x, y) => x + y;

const thunk = () => add(2, 3);

thunk(); // 5
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an Asynchronous Thunks</h2>

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

### <h2>What is async function</h2>

An async function is a function declared with the `async` keyword which enables asynchronous, promise-based behavior to be written in a cleaner style by avoiding promise chains. These functions can contain zero or more `await` expressions.

Let's take a below async function example,

```javascript
async function logger() {
let data = await fetch("http://someapi.com/users"); // pause until fetch returns
console.log(data);
}
logger();
```

It is basically syntax sugar over ES2015 promises and generators.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How to use await outside of async function prior to ES2022</h2>

Prior to ES2022, if you attempted to use an await outside of an async function resulted in a SyntaxError.

```javascript
await Promise.resolve(console.log("Hello await")); // SyntaxError: await is only valid in async function
```

But you can fix this issue with an alternative IIFE (Immediately Invoked Function Expression) to get access to the feature.

```javascript
(async function () {
    await Promise.resolve(console.log("Hello await")); // Hello await
})();
```

In ES2022, you can write top-level await without writing any hacks.

```javascript
await Promise.resolve(console.log("Hello await")); //Hello await
```

**[⬆ Back to Top](#table-of-contents)**









