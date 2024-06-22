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
| 1   | [What is an event flow](#What-is-an-event-flow)                                                                                                       |
| 2   | [What is event bubbling](#What-is-event-bubbling)                                                                                                     |
| 3   | [What is event capturing](#What-is-event-capturing)                                                                                                   |
| 4   | [What is the use of stopPropagation method](#What-is-the-use-of-stopPropagation-method)                                                               |
| 5   | [What is an event delegation](#What-is-an-event-delegation)                                                                                           |
| 6   | [What is call stack](#What-is-call-stack)                                                                                                             |
| 7   | [What is an event queue](#What-is-an-event-queue)                                                                                                     |
| 8   | [What is an event table](#What-is-an-event-table)                                                                                                     |
| 9   | [What is the use of preventDefault method](#What-is-the-use-of-preventDefault-method)                                                                 |
| 10  | [What are events](#What-are-events)                                                                                                                   |
| 11  | [What are server-sent events](#What-are-server-sent-events)                                                                                           |
| 12  | [How do you receive server-sent event notifications](#How-do-you-receive-server-sent-event-notifications)                                             |
| 13  | [How do you check browser support for server-sent events](#How-do-you-check-browser-support-for-server-sent-events)                                   |
| 14  | [What are the events available for server sent events](#What-are-the-events-available-for-server-sent-events)                                         |
| 15  | [What is the difference between document load and DOMContentLoaded events](#What-is-the-difference-between-document-load-and-DOMContentLoaded-events) |
| 16  | [What is BOM](#What-is-BOM)                                                                                                                           |
| 1   | [What are the different ways to deal with Asynchronous Code](#What-are-the-different-ways-to-deal-with-Asynchronous-Code)                             |
| 1   | [What is a callback function](#What-is-a-callback-function)                                                                                           |
| 2   | [Why do we need callbacks](#Why-do-we-need-callbacks)                                                                                                 |
| 3   | [What is a callback hell](#What-is-a-callback-hell)                                                                                                   |
| 4   | [What is callback in callback](#What-is-callback-in-callback)                                                                                         |
| 1   | [What is a promise](#What-is-a-promise)                                                                                                               |
| 2   | [Why do you need a promise](#Why-do-you-need-a-promise)                                                                                               |
| 3   | [What are the three states of promise](#What-are-the-three-states-of-promise)                                                                         |
| 4   | [What are the main rules of promise](#What-are-the-main-rules-of-promise)                                                                             |
| 5   | [What is promise chaining](#What-is-promise-chaining)                                                                                                 |
| 6   | [What is promise.all](#What-is-promise.all)                                                                                                           |
| 7   | [What is the purpose of the race method in promise](#What-is-the-purpose-of-the-race-method-in-promise)                                               |
| 8   | [What are the pros and cons of promises over callbacks](#What-are-the-pros-and-cons-of-promises-over-callbacks)                                       |
| 9   | [What are the differences between promises and observables](#What-are-the-differences-between-promises-and-observables)                               |
| 10  | [How do you prevent promises swallowing errors](#How-do-you-prevent-promises-swallowing-errors)                                                       |
| 11  | [How do you check an object is a promise or not](#How-do-you-check-an-object-is-a-promise-or-not)                                                     |
| 12  | [What is the easiest way to ignore promise errors](#What-is-the-easiest-way-to-ignore-promise-errors)                                                 |
| 13  | [What are asynchronous thunks](#What-are-asynchronous-thunks)                                                                                         |


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

### <h2>What is an event flow</h2>

Event flow is the order in which event is received on the web page. When you click an element that is nested in various other elements, before your click actually reaches its destination, or target element, it must trigger the click event for each of its parent elements first, starting at the top with the global window object.

There are two ways of event flow

1. Top to Bottom(Event Capturing) </h2>
2. Bottom to Top (Event Bubbling)

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is event bubbling</h2>

Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is event capturing</h2>

Event capturing is a type of event propagation where the event is first captured by the outermost element, and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the innermost DOM element.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the use of stopPropagation method</h2>

The stopPropagation method is used to stop the event from bubbling up and capturing up the event chain. For example, the below nested divs with stopPropagation method prevents default event propagation when clicking on nested div(Div1)

```javascript
<p>Click DIV1 Element</p>
<div onclick="secondFunc()">DIV 2
<div onclick="firstFunc(event)">DIV 1</div>
</div>

<script>
function firstFunc(event) {
    alert("DIV 1");
    event.stopPropagation();
}

function secondFunc() {
    alert("DIV 2");
}
</script>
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an event delegation</h2>

Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

For example, if you wanted to detect field changes in inside a specific form, you can use event delegation technique,

```javascript
var form = document.querySelector("#registration-form");

// Listen for changes to fields inside the form
form.addEventListener(
    "input",
    function (event) {
        // Log the field that was changed
        console.log(event.target);
    },
    false
);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is call stack</h2>

Call Stack is a data structure for javascript interpreters to keep track of function calls(creates execution context) in the program. It has two major actions,

1. Whenever you call a function for its execution, you are pushing it to the stack. </br>
2. Whenever the execution is completed, the function is popped out of the stack.</br>

Let's take an example and it's state representation in a diagram format

```javascript
function hungry() {
 eatFruits();
}

function eatFruits() {
 return "I'm eating fruits";
}

// Invoke the `hungry` function
hungry();
```

The above code processed in a call stack as below,

1. Add the `hungry()` function to the call stack list and execute the code. </br>
2. Add the `eatFruits()` function to the call stack list and execute the code. </br>
3. Delete the `eatFruits()` function from our call stack list. </br>
4. Delete the `hungry()` function from the call stack list since there are no items anymore. </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an event queue</h2>

The event queue follows the queue data structure. It stores async callbacks to be added to the call stack. It is also known as the Callback Queue or Macrotask Queue.

Whenever the call stack receives an async function, it is moved into the Web API. Based on the function, Web API executes it and awaits the result. Once it is finished, it moves the callback into the event queue (the callback of the promise is moved into the microtask queue).

The event loop constantly checks whether or not the call stack is empty. Once the call stack is empty and there is a callback in the event queue, the event loop moves the callback into the call stack. But if there is a callback in the microtask queue as well, it is moved first. The microtask queue has a higher priority than the event queue.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an event table</h2>

Event Table is a data structure that stores and keeps track of all the events which will be executed asynchronously like after some time interval or after the resolution of some API requests. i.e Whenever you call a setTimeout function or invoke async operation, it is added to the Event Table.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the use of preventDefault method</h2>

The preventDefault() method cancels the event if it is cancelable, meaning that the default action or behaviour that belongs to the event will not occur. For example, prevent form submission when clicking on submit button and prevent opening the page URL when clicking on hyperlink are some common use cases.

```javascript
document
.getElementById("link")
.addEventListener("click", function (event) {
    event.preventDefault();
});
```

**Note:** Remember that not all events are cancelable.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are events</h2>

Events are "things" that happen to HTML elements. When JavaScript is used in HTML pages, JavaScript can `react` on these events. Some of the examples of HTML events are,

1. Web page has finished loading </br>
2. Input field was changed </br>
3. Button was clicked

Let's describe the behavior of click event for button element,

```javascript
<!doctype html>
<html>
<head>
  <script>
    function greeting() {
      alert('Hello! Good morning');
    }
  </script>
</head>
<body>
  <button type="button" onclick="greeting()">Click me</button>
</body>
</html>
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are server-sent events</h2>

Server-sent events (SSE) is a server push technology enabling a browser to receive automatic updates from a server via HTTP connection without resorting to polling. These are a one way communications channel - events flow from server to client only. This has been used in Facebook/Twitter updates, stock price updates, news feeds etc.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you receive server-sent event notifications</h2>

The EventSource object is used to receive server-sent event notifications. For example, you can receive messages from server as below,

```javascript
if (typeof EventSource !== "undefined") {
    var source = new EventSource("sse_generator.js");
    source.onmessage = function (event) {
    document.getElementById("output").innerHTML += event.data + "<br>";
    };
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check browser support for server-sent events</h2>

You can perform browser support for server-sent events before using it as below,

```javascript
if (typeof EventSource !== "undefined") {
    // Server-sent events supported. Let's have some code here!
} else {
    // No server-sent events supported
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the events available for server sent events</h2>

Below are the list of events available for server sent events

| Event     | Description                                          |
| --------- | ---------------------------------------------------- |
| onopen    | It is used when a connection to the server is opened |
| onmessage | This event is used when a message is received        |
| onerror   | It happens when an error occurs                      |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between document load and DOMContentLoaded events</h2>

The `DOMContentLoaded` event is fired when the initial HTML document has been completely loaded and parsed, without waiting for assets(stylesheets, images, and subframes) to finish loading. Whereas The load event is fired when the whole page has loaded, including all dependent resources(stylesheets, images).

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is BOM</h2>

The Browser Object Model (BOM) allows JavaScript to "talk to" the browser. It consists of the objects navigator, history, screen, location and document which are children of the window. The Browser Object Model is not standardized and can change based on different browsers.


**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the different ways to deal with Asynchronous Code</h2>

Below are the list of different ways to deal with Asynchronous code.

1. Callbacks </br>
2. Promises </br>
3. Async/await </br>
4. Third-party libraries such as async.js,bluebird etc

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a callback function</h2>

A callback function is a function passed into another function as an argument. This function is invoked inside the outer function to complete an action.
Let's take a simple example of how to use callback function

```javascript
function callbackFunction(name) {
    console.log("Hello " + name);
}

function outerFunction(callback) {
    let name = prompt("Please enter your name.");
    callback(name);
}

outerFunction(callbackFunction);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do we need callbacks</h2>

The callbacks are needed because javascript is an event driven language. That means instead of waiting for a response javascript will keep executing while listening for other events.
Let's take an example with the first function invoking an API call(simulated by setTimeout) and the next function which logs the message.

```javascript
function firstFunction() {
    // Simulate a code delay
    setTimeout(function () {
    console.log("First function called");
    }, 1000);
}
function secondFunction() {
    console.log("Second function called");
}
firstFunction();
secondFunction();

Output;
// Second function called
// First function called
```

As observed from the output, javascript didn't wait for the response of the first function and the remaining code block got executed. So callbacks are used in a way to make sure that certain code doesn’t execute until the other code finishes execution.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a callback hell</h2>

Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic. The callback hell looks like below,

```javascript
async1(function(){
    async2(function(){
        async3(function(){
            async4(function(){
                ....
            });
        });
    });
});
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is callback in callback</h2>

You can nest one callback inside in another callback to execute the actions sequentially one by one. This is known as callbacks in callbacks.

```javascript
loadScript("/script1.js", function (script) {
    console.log("first script is loaded");

    loadScript("/script2.js", function (script) {
    console.log("second script is loaded");

    loadScript("/script3.js", function (script) {
        console.log("third script is loaded");
        // after all scripts are loaded
    });
    });
});
```

**[⬆ Back to Top](#table-of-contents)**

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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
