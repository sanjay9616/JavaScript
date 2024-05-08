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
<h1>isFinite Function</h1>
<h1>compareFunction Function</h1>
<h1>Thunk Function</h1>
<h1>async Function</h1>
<h1>Compose and Pipe Function</h1>
<h1>uneval and eval Function</h1>