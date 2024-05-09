### Table of Contents

| No. | Questions                                                                                                                                           |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are lambda or arrow functions](#What-are-lambda-or-arrow-functions)                                                                           |
| 2   | [What is a first class function](#What-is-a-first-class-function)                                                                                   |
| 3   | [What is a first order function](#What-is-a-first-order-function)                                                                                   |
| 4   | [What is a higher order function](#What-is-a-higher-order-function)                                                                                 |
| 5   | [What is a unary function](#What-is-a-unary-function)                                                                                               |
| 6   | [What is a pure function](#What-is-a-pure-function)                                                                                                 |
| 7   | [What are the differences between pure and impure functions](#What-are-the-differences-between-pure-and-impure-functions)                           |
| 8   | [What is IIFE(Immediately Invoked Function Expression)](#What-is-IIFE(Immediately-Invoked-Function-Expression))                                     |
| 9   | [How to invoke an IIFE without any extra brackets](#How-to-invoke-an-IIFE-without-any-extra-brackets)                                               |
| 10  | [What is a thunk function](#What-is-a-thunk-function)                                                                                               |
| 11  | [What is an Asynchronous Thunks](#What-is-an-Asynchronous-Thunks)                                                                                   |
| 12  | [What is async function](#What-is-async-function)                                                                                                   |
| 13  | [How to use await outside of async function prior to ES2022](#How-to-use-await-outside-of-async-function-prior-to-ES2022)                           |
| 14  | [What is an anonymous function](#What-is-an-anonymous-function)                                                                                     |
| 15  | [What are compose and pipe functions](#What-are-compose-and-pipe-functions)                                                                         |
| 16  | [What is the purpose of uneval](#What-is-the-purpose-of-uneval)                                                                                     |
| 17  | [What is the difference between uneval and eval](#What-is-the-difference-between-uneval-and-eval)                                                   |
| 18  | [Can we define properties for functions](#Can-we-define-properties-for-functions)                                                                   |
| 19  | [What is the way to find the number of parameters expected by a function](#What-is-the-way-to-find-the-number-of-parameters-expected-by-a-function) |
| 20  | [What are the function parameter rules](#What-are-the-function-parameter-rules)                                                                     |
| 21  | [What is the difference between a parameter and an argument](#What-is-the-difference-between-a-parameter-and-an-argument)                           |
| 22  | [What are default parameters](#What-are-default-parameters)                                                                                         |
| 23  | [What is the output of below function calls](#What-is-the-output-of-below-function-calls)                                                           |

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

### <h2>How to invoke an IIFE without any extra brackets</h2>

Immediately Invoked Function Expressions(IIFE) requires a pair of parenthesis to wrap the function which contains set of statements.

```js
(function (dt) {
    console.log(dt.toLocaleTimeString());
})(new Date());
```

Since both IIFE and void operator discard the result of an expression, you can avoid the extra brackets using `void operator` for IIFE as below,

```js
void (function (dt) {
    console.log(dt.toLocaleTimeString());
})(new Date());
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

### <h2>What is an anonymous function</h2>

```javascript
function () { // Synax Error

}
```
`An anonymous function is a function without a name!` Anonymous functions are commonly assigned to a variable name or used as a callback function. The syntax would be as below,

```javascript
function (optionalParameters) {
    //do something
}

const myFunction = function(){ //Anonymous function assigned to a variable
    //do something
};

[1, 2, 3].map(function(element){ //Anonymous function used as a callback function
    //do something
});
```

Let's see the above anonymous function in an example,

```javascript
var x = function (a, b) {
    return a * b;
};
var z = x(5, 10);
console.log(z); // 50
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are compose and pipe functions</h2>

The "compose" and "pipe" are two techniques commonly used in functional programming to simplify complex operations and make code more readable. They are not native to JavaScript and higher-order functions. the `compose()` applies right to left any number of functions to the output of the previous function.

```js
const addTwo = (a) => a + 2;
const substractThree = (a) => a - 3;
const multiplyByFive = (a) => a * 5;

const res = multiplyByFive(substractThree(addTwo(4)))
console.log(res) // 15

// To get compose order from Right to Left - we need reduceRight
const compose = (...fns) => val => fns.reduceRight((prev, fn) => fn(prev), val)
const composeRes = compose(multiplyByFive, substractThree, addTwo)(4);
console.log(composeRes) // 15

// To get same, but compose function from Left to Right - we need reduce
const compose = (...fns) => val => fns.reduce((prev, fn) => fn(prev), val)
const composeRes = compose(multiplyByFive, substractThree, addTwo)(4);
console.log(composeRes) // 19
```

```js
const addTwo = (a) => a + 2;
const substractThree = (a) => a - 3;
const multiplyByFive = (a) => a * 5;
const divideBy = (a, b) => a / b;

const compose = (...fns) => val => fns.reduce((prev, fn) => fn(prev), val)
pipeRes = compose(multiplyByFive, substractThree, addTwo, x => divideBy(x, 2))(4);
console.log(pipeRes) // 9.5
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of uneval</h2>

The uneval() is an inbuilt function which is used to create a string representation of the source code of an Object. It is a top-level function and is not associated with any object. Let's see the below example to know more about it's functionality,

```javascript
var a = 1;
uneval(a); // returns a String containing 1
uneval(function user() {}); // returns "(function user(){})"
```

The `uneval()` function has been deprecated. It is recommended to use `toString()` for functions and `JSON.toStringify()` for other cases.

```javascript
function user() {}
console.log(user.toString()); // returns "(function user(){})"
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between uneval and eval</h2>

The `uneval` function returns the source of a given object; whereas the `eval` function does the opposite, by evaluating that source code in a different memory area. Let's see an example to clarify the difference,

```javascript
var msg = uneval(function greeting() {
    return "Hello, Good morning";
});
var greeting = eval(msg);
greeting(); // returns "Hello, Good morning"
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Can we define properties for functions</h2>

Yes, We can define properties for functions because functions are also objects.

```javascript
fn = function (x) {
    //Function code goes here
};

fn.name = "John";

fn.profile = function (y) {
    //Profile code goes here
};
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the way to find the number of parameters expected by a function</h2>

You can use `function.length` syntax to find the number of parameters expected by a function. Let's take an example of `sum` function to calculate the sum of numbers,

```javascript
function sum(num1, num2, num3, num4) {
    return num1 + num2 + num3 + num4;
}
sum.length; // 4 is the number of parameters expected.
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the function parameter rules</h2>

JavaScript functions follow below rules for parameters,

1. The function definitions do not specify data types for parameters. </br>
2. Do not perform type checking on the passed arguments.</br>
3. Do not check the number of arguments received. </br>
i.e, The below function follows the above rules,

```javascript
function functionName(parameter1, parameter2, parameter3) {
    console.log(parameter1); // 1
}
functionName(1);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between a parameter and an argument</h2>

Parameter is the variable name of a function definition whereas an argument represents the value given to a function when it is invoked. Let's explain this with a simple function

```js
function a(param1, param2) { // parameters
    console.log(param1 + param2)
}
a(1, 2) // arguments
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are default parameters</h2>

In ES5, we need to depend on logical OR operators to handle default values of function parameters. Whereas in ES6, Default function parameters feature allows parameters to be initialized with default values if no value or undefined is passed. Let's compare the behavior with an examples,

```javascript
//ES5
var calculateArea = function (height, width) {
    height = height || 50;
    width = width || 60;

    return width * height;
};
console.log(calculateArea()); //300
```

The default parameters makes the initialization more simpler,

```javascript
//ES6
var calculateArea = function (height = 50, width = 60) {
    return width * height;
};

console.log(calculateArea()); //300
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the output of below function calls</h2>

**Code snippet:**

```javascript
const circle = {
    radius: 20,
    diameter() {
        return this.radius * 2;
    },
    perimeter: () => 2 * Math.PI * this.radius,
};
```

```javascript
console.log(circle.diameter());
console.log(circle.perimeter());
```

**Output:**

The output is 40 and NaN. Remember that diameter is a regular function, whereas the value of perimeter is an arrow function. The `this` keyword of a regular function(i.e, diameter) refers to the surrounding scope which is a class(i.e, Shape object). Whereas this keyword of perimeter function refers to the surrounding scope which is a window object. Since there is no radius property on window objects it returns an undefined value and the multiple of number value returns NaN value.

**[⬆ Back to Top](#table-of-contents)**















