### Table of Contents

| No. | Questions                                                                                                                                             |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the difference between Call Apply and Bind](#What-is-the-difference-between-Call-Apply-and-Bind)                                             |
| 1   | [How do you create your own bind method using either call or apply method](#How-do-you-create-your-own-bind-method-using-either-call-or-apply-method) |
| 1   | [What is debouncing](#What-is-debouncing)                                                                                                             |
| 1   | [What is throttling](#What-is-throttling)                                                                                                             |
| 2   | [What is minimum timeout throttling](#What-is-minimum-timeout-throttling)                                                                             |
| 1   | [What is Hoisting](#What-is-Hoisting)                                                                                                                 |
| 2   | [What is global execution context](#What-is-global-execution-context)                                                                                 |
| 3   | [What is function execution context](#What-is-function-execution-context)                                                                             |
| 1   | [What are closures](#What-are-closures)                                                                                                               |
| 1   | [What is the currying function](#What-is-the-currying-function)                                                                                       |
| 1   | [What is memoization](#What-is-memoization)                                                                                                           |

### <h2>What is the difference between Call, Apply and Bind</h2>

The difference between Call, Apply and Bind can be explained with below examples,

<h3>Call:</h3>

The call() method invokes a function with a given `this` value and arguments provided one by one.

**Example**

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2);
}

invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How are you?
invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

<h3>Apply:</h3>

Invokes the function with a given `this` value and allows you to pass in arguments as an array.

**Example**

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2);
}

invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
```

<h3>Bind:</h3>

Returns a new function, allowing you to pass any number of arguments.

**Example**

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2);
}

var inviteEmployee1 = invite.bind(employee1);
var inviteEmployee2 = invite.bind(employee2);
inviteEmployee1("Hello", "How are you?"); // Hello John Rodson, How are you?
inviteEmployee2("Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

Call and Apply are pretty much interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.

Bind creates a new function that will have `this` set to the first parameter passed to bind().

### <h2>How do you create your own bind method using either call or apply method</h2>

The custom bind function needs to be created on Function prototype inorder to use it as other builtin functions. This custom function should return a function similar to original bind method and the implementation of inner function needs to use apply method call.

The function which is going to bind using custom `myOwnBind` method act as the attached function(`boundTargetFunction`) and argument as the object for `apply` method call.

```js
Function.prototype.myOwnBind = function (whoIsCallingMe) {
if (typeof this !== "function") {
    throw new Error(this + "cannot be bound as it's not callable");
}
const boundTargetFunction = this;
return function () {
    boundTargetFunction.apply(whoIsCallingMe, arguments);
};
};
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is debouncing</h2>

Debouncing is a programming pattern that allows delaying execution of some piece of code until a specified time to avoid unnecessary _CPU cycles, API calls and improve performance_. The debounce function make sure that your code is only triggered once per user input. The common usecases are Search box suggestions, text-field auto-saves, and eliminating double-button clicks.

Let's say you want to show suggestions for a search query, but only after a visitor has finished typing it. So here you write a debounce function where the user keeps writing the characters with in 500ms then previous timer cleared out using `clearTimeout` and reschedule API call/DB query for a new time—300 ms in the future.

```js
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

**[⬆ Back to Top](#table-of-contents)**

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

### <h2>What is Hoisting</h2>

Hoisting is a JavaScript mechanism where variables, function declarations and classes are moved to the top of their scope before code execution. Remember that JavaScript only hoists declarations, not initialisation.
Let's take a simple example of variable hoisting,

```javascript
console.log(message); //output : undefined
var message = "The variable Has been hoisted";
```

The above code looks like as below to the interpreter,

```javascript
var message;
console.log(message);
message = "The variable Has been hoisted";
```

In the same fashion, function declarations are hoisted too

```javascript
message("Good morning"); //Good morning

function message(name) {
    console.log(name);
}
```

This hoisting makes functions to be safely used in code before they are declared.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is global execution context</h2>

The global execution context is the default or first execution context that is created by the JavaScript engine before any code is executed(i.e, when the file first loads in the browser). All the global code that is not inside a function or object will be executed inside this global execution context. Since JS engine is single threaded there will be only one global environment and there will be only one global execution context.

For example, the below code other than code inside any function or object is executed inside the global execution context.

```javascript
var x = 10;

function A() {
    console.log("Start function A");
    function B() {
        console.log("In function B");
    }
    B();
}
A();

console.log("GlobalContext");
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is function execution context</h2>

Whenever a function is invoked, the JavaScript engine creates a different type of Execution Context known as a Function Execution Context (FEC) within the Global Execution Context (GEC) to evaluate and execute the code within that function.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are closures</h2>

A closure is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function’s variables. The closure has three scope chains

1. Own scope where variables defined between its curly brackets
2. Outer function’s variables
3. Global variables

Let's take an example of closure concept,

```javascript
function Welcome(name) {
    var greetingInfo = function (message) {
        console.log(message + " " + name);
    };
    return greetingInfo;
}
var myFunction = Welcome("John");
myFunction("Welcome "); //Output: Welcome John
myFunction("Hello Mr."); //output: Hello Mr.John
```

As per the above code, the inner function(i.e, greetingInfo) has access to the variables in the outer function scope(i.e, Welcome) even after the outer function has returned.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the currying function</h2>

Currying is the process of taking a function with multiple arguments and turning it into a sequence of functions each with only a single argument. Currying is named after a mathematician **Haskell Curry**. By applying currying, an n-ary function turns into a unary function.

Let's take an example of n-ary function and how it turns into a currying function,

```javascript
const multiArgFunction = (a, b, c) => a + b + c;
console.log(multiArgFunction(1, 2, 3)); // 6

const curryUnaryFunction = (a) => (b) => (c) => a + b + c;
curryUnaryFunction(1); // returns a function: b => c =>  1 + b + c
curryUnaryFunction(1)(2); // returns a function: c => 3 + c
curryUnaryFunction(1)(2)(3); // returns the number 6
```

Curried functions are great to improve **code reusability** and **functional composition**.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is memoization</h2>

Memoization is a functional programming technique which attempts to increase a function’s performance by caching its previously computed results. Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. Otherwise the function is executed and then the result is added to the cache.
Let's take an example of adding function with memoization,

```javascript
const memoizAddition = () => {
    let cache = {};
    return (value) => {
        if (value in cache) {
            console.log("Fetching from cache");
            return cache[value]; // Here, cache.value cannot be used as property name starts with the number which is not a valid JavaScript  identifier. Hence, can only be accessed using the square bracket notation.
        } else {
            console.log("Calculating result");
            let result = value + 20;
            cache[value] = result;
            return result;
        }
    };
};
// returned function from memoizAddition
const addition = memoizAddition();
console.log(addition(20)); //output: 40 calculated
console.log(addition(20)); //output: 40 cached
```

**[⬆ Back to Top](#table-of-contents)**

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
