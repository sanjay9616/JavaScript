<h1>Funtion Statement or Function Declaration</h1>

`A Function Statement also known as a Function Declaration declares a function with a function keyword`. The function declaration must have a function name. Function declaration does not require a variable assignment as they are standalone constructs and they cannot be nested inside a functional block.

```javascript
function a() { // memory creaed

}
```

<h1>Funtion Expression</h1>

```javascript
var b = function () { // treated like a variable

}
```

<h1>Named Function Expressions</h1>

`Function Expression with function name`

```javascript
var b = function xyz() {

}
```

<h1>Anonymous Function</h1>

`Functions without name`

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

<h1>Parameters vs Arguments</h1>

Parameter is the variable name of a function definition whereas an argument represents the value given to a function when it is invoked. Let's explain this with a simple function

```js
function a(param1, param2) { // parameters
    console.log(param1 + param2)
}
a(1, 2) // arguments
```

<h1>Lambda or Arrow Function</h1>

**Definiion:** `An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.`

```js
const addTwo = (a, b) => {
    return a + b;
}
console.log(addTwo(4, 5)) // 9

// ########### OR ########### //

const addTwo = (a, b) => (a + b) // if you use () then don't need return statement
console.log(addTwo(4, 5)) // 9
```

<h1>First Class Function</h1>

In Javascript, functions are first class objects. First-class functions means when functions in that language are treated like any other variable.

For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable. For example, in the below example, handler functions assigned to a listener

```javascript
const handler = () => console.log("This is a click handler function");
document.addEventListener("click", handler);
```

<h1>First Order Function</h1>

A first-order function is a function that doesn’t accept another function as an argument and doesn’t return a function as its return value.

```javascript
const firstOrder = () => console.log("I am a first order function!");
```

<h1>Higher Order Function</h1>

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

<h1>Unary Function</h1>

A unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for a single argument accepted by a function.

Let us take an example of unary function,

```javascript
const unaryFunction = (a) => console.log(a + 10); // Add 10 to the given argument and display the value
```

<h1>Pure and Impure Function</h1>

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

<h1>IIFE(Immediately Invoked Function Expression)</h1>

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

<h1>Thunk Function</h1>

A thunk is just a function which delays the evaluation of the value. It doesn’t take any arguments but gives the value whenever you invoke the thunk. i.e, It is used not to execute now but it will be sometime in the future. Let's take a synchronous example,

```javascript
const add = (x, y) => x + y;

const thunk = () => add(2, 3);

thunk(); // 5
```

<h1>async Function</h1>

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

<h1>Asynchronous Thunks</h1>

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

<h1>Compose and Pipe Function</h1>

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
<h1>uneval and eval Function</h1>

**eval():** The eval function evaluates or executes an argument. If the argument is an expression, eval() evaluates the expression. If the argument is one or more javascript statements, eval() executes the statements.

The `uneval` function returns the source of a given object; whereas the `eval` function does the opposite, by evaluating that source code in a different memory area. Let's see an example to clarify the difference,

```js
console.log(eval(2+2), typeof eval(2+2)) // 4 number
console.log(eval(2+'2'), typeof eval(2+'2')) // 22 number
```
```javascript
var msg = uneval(function greeting() {
    return "Hello, Good morning";
});
var greeting = eval(msg);
greeting(); // returns "Hello, Good morning"
```

**uneval():** The uneval() is an inbuilt function which is used to create a string representation of the source code of an Object. It is a top-level function and is not associated with any object. Let's see the below example to know more about it's functionality,

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

<h1>Generators</h1>
<h1>module pattern</h1>
<h1>referential transparency</h1>
<h1>hidden classes</h1>
<h1>pass by value and pass by reference</h1>
<h1>What is Function Composition</h1>
<h1>enum</h1>

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>