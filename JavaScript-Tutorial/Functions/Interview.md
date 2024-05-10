### Table of Contents

| No. | Questions                                                                                                                                                     |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are lambda or arrow functions](#What-are-lambda-or-arrow-functions)                                                                                     |
| 2   | [What is a first class function](#What-is-a-first-class-function)                                                                                             |
| 3   | [What is a first order function](#What-is-a-first-order-function)                                                                                             |
| 4   | [What is a higher order function](#What-is-a-higher-order-function)                                                                                           |
| 5   | [What is a unary function](#What-is-a-unary-function)                                                                                                         |
| 6   | [What is a pure function](#What-is-a-pure-function)                                                                                                           |
| 7   | [What are the differences between pure and impure functions](#What-are-the-differences-between-pure-and-impure-functions)                                     |
| 8   | [What is IIFE(Immediately Invoked Function Expression)](#What-is-IIFE(Immediately-Invoked-Function-Expression))                                               |
| 9   | [How to invoke an IIFE without any extra brackets](#How-to-invoke-an-IIFE-without-any-extra-brackets)                                                         |
| 10  | [What is a thunk function](#What-is-a-thunk-function)                                                                                                         |
| 11  | [What is an Asynchronous Thunks](#What-is-an-Asynchronous-Thunks)                                                                                             |
| 12  | [What is async function](#What-is-async-function)                                                                                                             |
| 13  | [How to use await outside of async function prior to ES2022](#How-to-use-await-outside-of-async-function-prior-to-ES2022)                                     |
| 14  | [What is an anonymous function](#What-is-an-anonymous-function)                                                                                               |
| 15  | [What are compose and pipe functions](#What-are-compose-and-pipe-functions)                                                                                   |
| 16  | [What is the purpose of uneval](#What-is-the-purpose-of-uneval)                                                                                               |
| 17  | [What is the difference between uneval and eval](#What-is-the-difference-between-uneval-and-eval)                                                             |
| 18  | [Can we define properties for functions](#Can-we-define-properties-for-functions)                                                                             |
| 19  | [What is the way to find the number of parameters expected by a function](#What-is-the-way-to-find-the-number-of-parameters-expected-by-a-function)           |
| 20  | [What are the function parameter rules](#What-are-the-function-parameter-rules)                                                                               |
| 21  | [What is the difference between a parameter and an argument](#What-is-the-difference-between-a-parameter-and-an-argument)                                     |
| 22  | [What are default parameters](#What-are-default-parameters)                                                                                                   |
| 23  | [What is the output of below function calls](#What-is-the-output-of-below-function-calls)                                                                     |
| 24  | [What is the difference between Function constructor and function declaration](#What-is-the-difference-between-Function-constructor-and-function-declaration) |
| 25  | [What is a Proper Tail Call](#What-is-a-Proper-Tail-Call)                                                                                                     |
| 26  | [How to detect if a function is called as constructor](#How-to-detect-if-a-function-is-called-as-constructor)                                                 |
| 27  | [What are the different kinds of generators](#What-are-the-different-kinds-of-generators)                                                                     |
| 28  | [How do you define instance and non-instance properties](#How-do-you-define-instance-and-non-instance-properties)                                             |
| 29  | [What is pass by value and pass by reference](#What-is-pass-by-value-and-pass-by-reference)                                                                   |
| 30  | [What are hidden classes](#What-are-hidden-classes)                                                                                                           |
| 31  | [What is referential transparency](#What-is-referential-transparency)                                                                                         |
| 32  | [What is module pattern](#What-is-module-pattern)                                                                                                             |
| 33  | [What is Function Composition](#What-is-Function-Composition)                                                                                                 |
| 34  | [What is the purpose of the this keyword in JavaScript](#What-is-the-purpose-of-the-this-keyword-in-JavaScript)                                               |
| 35  | [What Is Obfuscation in javascript](#What-Is-Obfuscation-in-javascript)                                                                                       |
| 36  | [Why do you need Obfuscation](#Why-do-you-need-Obfuscation)                                                                                                   |
| 37  | [What is Minification](#What-is-Minification)                                                                                                                 |
| 38  | [What are the advantages of minification](#What-are-the-advantages-of-minification)                                                                           |
| 39  | [What are the differences between Obfuscation and Encryption](#What-are-the-differences-between-Obfuscation-and-Encryption)                                   |
| 40  | [What are the common tools used for minification](#What-are-the-common-tools-used-for-minification)                                                           |
| 41  | [How do you perform form validation using javascript](#How-do-you-perform-form-validation-using-javascript)                                                   |
| 42  | [How do you perform form validation without javascript](#How-do-you-perform-form-validation-without-javascript)                                               |
| 43  | [What are the DOM methods available for constraint validation](#What-are-the-DOM-methods-available-for-constraint-validation)                                 |
| 44  | [What are the available constraint validation DOM properties](#What-are-the-available-constraint-validation-DOM-properties)                                   |
| 45  | [What are the list of validity properties](#What-are-the-list-of-validity-properties)                                                                         |
| 46  | [Give an example usage of rangeOverflow property](#Give-an-example-usage-of-rangeOverflow-property)                                                           |
| 47  | [What is an enum](#What-is-an-enum)                                                                                                                           |
| 48  | [Is enums feature available in javascript](#Is-enums-feature-available-in-javascript)                                                                         |
| 49  | [How do you extend classes](#How-do-you-extend-classes)                                                                                                       |

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

### <h2>What is the difference between Function constructor and function declaration</h2>

The functions which are created with `Function constructor` do not create closures to their creation contexts but they are always created in the global scope. i.e, the function can access its own local variables and global scope variables only. Whereas function declarations can access outer function variables(closures) too.

Let's see this difference with an example,

**Function Constructor:**

```javascript
var a = 100;
function createFunction() {
    var a = 200;
    return new Function("return a;");
}
console.log(createFunction()()); // 100
```

**Function declaration:**

```javascript
var a = 100;
function createFunction() {
    var a = 200;
    return function func() {
        return a;
    };
}
console.log(createFunction()()); // 200
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a Proper Tail Call</h2>

First, we should know about tail call before talking about "Proper Tail Call". A tail call is a subroutine or function call performed as the final action of a calling function. Whereas **Proper tail call(PTC)** is a technique where the program or code will not create additional stack frames for a recursion when the function call is a tail call.

For example, the below classic or head recursion of factorial function relies on stack for each step. Each step need to be processed upto `n * factorial(n - 1)`

```javascript
function factorial(n) {
    if (n === 0) {
        return 1;
    }
return n * factorial(n - 1);
}
console.log(factorial(5)); //120
```

But if you use Tail recursion functions, they keep passing all the necessary data it needs down the recursion without relying on the stack.

```javascript
function factorial(n, acc = 1) {
    if (n === 0) {
        return acc;
    }
    return factorial(n - 1, n * acc);
}
console.log(factorial(5)); //120
```

The above pattern returns the same output as the first one. But the accumulator keeps track of total as an argument without using stack memory on recursive calls.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How to detect if a function is called as constructor</h2>

You can use `new.target` pseudo-property to detect whether a function was called as a constructor(using the new operator) or as a regular function call.

1. If a constructor or function invoked using the new operator, new.target returns a reference to the constructor or function. </br>
2. For function calls, new.target is undefined.

```javascript
function Myfunc() {
 if (new.target) {
   console.log("called with new");
 } else {
   console.log("not called with new");
 }
}

new Myfunc(); // called with new
Myfunc(); // not called with new
Myfunc.call({}); // not called with new
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the different kinds of generators</h2>

There are five kinds of generators,

**1. Generator function declaration:**

  ```javascript
  function* myGenFunc() {
    yield 1;
    yield 2;
    yield 3;
  }
  const genObj = myGenFunc();
  ```

**2. Generator function expressions:**

  ```javascript
  const myGenFunc = function* () {
    yield 1;
    yield 2;
    yield 3;
  };
  const genObj = myGenFunc();
  ```

**3. Generator method definitions in object literals:**

  ```javascript
  const myObj = {
    *myGeneratorMethod() {
      yield 1;
      yield 2;
      yield 3;
    },
  };
  const genObj = myObj.myGeneratorMethod();
  ```

**4. Generator method definitions in class:**

  ```javascript
  class MyClass {
    *myGeneratorMethod() {
      yield 1;
      yield 2;
      yield 3;
    }
  }
  const myObject = new MyClass();
  const genObj = myObject.myGeneratorMethod();
  ```

**5. Generator as a computed property:**

  ```javascript
  const SomeObj = {
    *[Symbol.iterator]() {
      yield 1;
      yield 2;
      yield 3;
    },
  };

  console.log(Array.from(SomeObj)); // [ 1, 2, 3 ]
  ```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you define instance and non-instance properties</h2>

The Instance properties must be defined inside of class methods. For example, name and age properties defined inside constructor as below,

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}
```

But Static(class) and prototype data properties must be defined outside of the ClassBody declaration. Let's assign the age value for Person class as below,

```javascript
Person.staticAge = 30;
Person.prototype.prototypeAge = 40;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is pass by value and pass by reference</h2>

Pass-by-value creates a new space in memory and makes a copy of a value. Primitives such as string, number, boolean etc will actually create a new copy. Hence, updating one value doesn't impact the other value. i.e, The values are independent of each other.

```javascript
let a = 5;
let b = a;

b++;
console.log(a, b); //5, 6
```

In the above code snippet, the value of `a` is assigned to `b` and the variable `b` has been incremented. Since there is a new space created for variable `b`, any update on this variable doesn't impact the variable `a`.

Pass by reference doesn't create a new space in memory but the new variable adopts a memory address of an initial variable. Non-primitives such as objects, arrays and functions gets the reference of the initiable variable. i.e, updating one value will impact the other variable - **Mutable**.

```javascript
let user1 = {
    name: "John",
    age: 27,
};
let user2 = user1;
user2.age = 30;

console.log(user1.age, user2.age); // 30, 30
```

In the above code snippet, updating the `age` property of one object will impact the other property due to the same reference.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are hidden classes</h2>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is referential transparency</h2>

An expression in javascript that can be replaced by its value without affecting the behaviour of the program is called referential transparency. Pure functions are referentially transparent.

```javascript
const add = (x, y) => x + y;
const multiplyBy2 = (x) => x * 2;

//Now add (2, 3) can be replaced by 5.

multiplyBy2(add(2, 3));
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is module pattern</h2>

Module pattern is a designed pattern used to wrap a set of variables and functions together in a single scope returned as an object. JavaScript doesn't have access specifiers similar to other languages(Java, Python, etc) to provide private scope. It uses IIFE (Immediately invoked function expression) to allow for private scopes. i.e., a closure that protect variables and methods.

The module pattern looks like below,

```javascript
(function () {
// Private variables or functions goes here.

return {
    // Return public variables or functions here.
};
})();
```

Let's see an example of a module pattern for an employee with private and public access,

```javascript
const createEmployee = (function () {
// Private
const name = "John";
const department = "Sales";
const getEmployeeName = () => name;
const getDepartmentName = () => department;

// Public
return {
    name,
    department,
    getName: () => getEmployeeName(),
    getDepartment: () => getDepartmentName(),
};
})();

console.log(createEmployee.name);
console.log(createEmployee.department);
console.log(createEmployee.getName());
console.log(createEmployee.getDepartment());
```

**Note:** It mimic the concepts of classes with private variables and methods.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is Function Composition</h2>

 It is an approach where the result of one function is passed on to the next function, which is passed to another until the final function is executed for the final result.

```javascript
//example
const double = (x) => x * 2;
const square = (x) => x * x;

var output1 = double(2);
var output2 = square(output1);
console.log(output2);

var output_final = square(double(2));
console.log(output_final);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of the this keyword in JavaScript</h2>

The `this` keyword in JavaScript is a special variable that is used within a function to refer to the object on which the function is invoked. The value of this depends on how the function is called. It allows functions to access and interact with the object they are bound to.

The this keyword in JavaScript is a reference to the object that owns or invokes the current function. Its value is determined by the calling context.

**Example 1: this in a Global Context**

```javascript
console.log(this);
```

In a global context, this refers to the global object (e.g., window in a browser).

**Example 2: this in a Function**

```javascript
function displayThis() {
  console.log(this);
}

displayThis();
```

In a regular function, this refers to the global object.

**Example 3: this in a Method**

```javascript
const person = {
  name: 'John',
  greet: function() {
    console.log('Hello, ' + this.name);
  }
};

person.greet();
```

In a method, this refers to the object that owns the method (person in the case).

**Example 4: this in an Event Handler**

```javascript
document.getElementById('myButton').addEventListener('click', function() {
  console.log(this);
});
```

In an event handler, this refers to the element that triggered the event (the button in this case).

**[⬆ Back to Top](#table-of-contents)**

### <h2>What Is Obfuscation in javascript</h2>

Obfuscation is the deliberate act of creating obfuscated javascript code(i.e, source or machine code) that is difficult for humans to understand. It is something similar to encryption, but a machine can understand the code and execute it.
Let's see the below function before Obfuscation,

```javascript
function greeting() {
console.log("Hello, welcome to JS world");
}
```

And after the code Obfuscation, it would be appeared as below,

```javascript
eval(
(function (p, a, c, k, e, d) {
    e = function (c) {
    return c;
    };
    if (!"".replace(/^/, String)) {
    while (c--) {
        d[c] = k[c] || c;
    }
    k = [
        function (e) {
        return d[e];
        },
    ];
    e = function () {
        return "\\w+";
    };
    c = 1;
    }
    while (c--) {
    if (k[c]) {
        p = p.replace(new RegExp("\\b" + e(c) + "\\b", "g"), k[c]);
    }
    }
    return p;
})(
    "2 1(){0.3('4, 7 6 5 8')}",
    9,
    9,
    "console|greeting|function|log|Hello|JS|to|welcome|world".split("|"),
    0,
    {}
)
);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do you need Obfuscation</h2>

Below are the few reasons for Obfuscation,

1. The Code size will be reduced. So data transfers between server and client will be fast. </br>
2. It hides the business logic from outside world and protects the code from others </br>
3. Reverse engineering is highly difficult </br>
4. The download time will be reduced </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is Minification</h2>

Minification is the process of removing all unnecessary characters(empty spaces are removed) and variables will be renamed without changing it's functionality. It is also a type of obfuscation .

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the advantages of minification</h2>

Normally it is recommended to use minification for heavy traffic and intensive requirements of resources. It reduces file sizes with below benefits,

1. Decreases loading times of a web page </br>
2. Saves bandwidth usages </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between Obfuscation and Encryption</h2>

Below are the main differences between Obfuscation and Encryption,

| Feature            | Obfuscation                                     | Encryption                                                              |
| ------------------ | ----------------------------------------------- | ----------------------------------------------------------------------- |
| Definition         | Changing the form of any data in any other form | Changing the form of information to an unreadable format by using a key |
| A key to decode    | It can be decoded without any key               | It is required                                                          |
| Target data format | It will be converted to a complex form          | Converted into an unreadable format                                     |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the common tools used for minification</h2>

There are many online/offline tools to minify the javascript files,

1. Google's Closure Compiler </br>
2. UglifyJS2 </br>
3. jsmin </br>
4. javascript-minifier.com/ </br>
5. prettydiff.com </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you perform form validation using javascript</h2>

JavaScript can be used to perform HTML form validation. For example, if the form field is empty, the function needs to notify, and return false, to prevent the form being submitted.
Lets' perform user login in an html form,

```html
<form name="myForm" onsubmit="return validateForm()" method="post">
User name: <input type="text" name="uname" />
<input type="submit" value="Submit" />
</form>
```

And the validation on user login is below,

```javascript
function validateForm() {
var x = document.forms["myForm"]["uname"].value;
if (x == "") {
    alert("The username shouldn't be empty");
    return false;
}
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you perform form validation without javascript</h2>

You can perform HTML form validation automatically without using javascript. The validation enabled by applying the `required` attribute to prevent form submission when the input is empty.

```html
<form method="post">
<input type="text" name="uname" required />
<input type="submit" value="Submit" />
</form>
```

**Note:** Automatic form validation does not work in Internet Explorer 9 or earlier.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the DOM methods available for constraint validation</h2>

The below DOM methods are available for constraint validation on an invalid input,

1. checkValidity(): It returns true if an input element contains valid data. </br>
2. setCustomValidity(): It is used to set the validationMessage property of an input element. </br>
  Let's take an user login form with DOM validations

```javascript
function myFunction() {
 var userName = document.getElementById("uname");
 if (!userName.checkValidity()) {
   document.getElementById("message").innerHTML =
     userName.validationMessage;
 } else {
   document.getElementById("message").innerHTML =
     "Entered a valid username";
 }
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the available constraint validation DOM properties</h2>

Below are the list of some of the constraint validation DOM properties available,

1. validity: It provides a list of boolean properties related to the validity of an input element. </br>
2. validationMessage: It displays the message when the validity is false. </br>
3. willValidate: It indicates if an input element will be validated or not.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the list of validity properties</h2>

The validity property of an input element provides a set of properties related to the validity of data.

1. customError: It returns true, if a custom validity message is set. </br>
2. patternMismatch: It returns true, if an element's value does not match its pattern attribute. </br>
3. rangeOverflow: It returns true, if an element's value is greater than its max attribute. </br>
4. rangeUnderflow: It returns true, if an element's value is less than its min attribute. </br>
5. stepMismatch: It returns true, if an element's value is invalid according to step attribute. </br>
6. tooLong: It returns true, if an element's value exceeds its maxLength attribute. </br>
7. typeMismatch: It returns true, if an element's value is invalid according to type attribute. </br>
8. valueMissing: It returns true, if an element with a required attribute has no value.
9. valid: It returns true, if an element's value is valid.

**[⬆ Back to Top](#table-of-contents)**

### <h2>Give an example usage of rangeOverflow property</h2>

If an element's value is greater than its max attribute then rangeOverflow property returns true. For example, the below form submission throws an error if the value is more than 100,

```html
<input id="age" type="number" max="100" />
<button onclick="myOverflowFunction()">OK</button>
```

```javascript
function myOverflowFunction() {
    if (document.getElementById("age").validity.rangeOverflow) {
        alert("The mentioned age is not allowed");
    }
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an enum</h2>

An enum is a type restricting variables to one value from a predefined set of constants. JavaScript has no enums but typescript provides built-in enum support.

```javascript
enum Color {
    RED, GREEN, BLUE
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Is enums feature available in javascript</h2>

No, javascript does not natively support enums. But there are different kinds of solutions to simulate them even though they may not provide exact equivalents. For example, you can use freeze or seal on object,

```javascript
var DaysEnum = Object.freeze({"monday":1, "tuesday":2, "wednesday":3, ...})
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you extend classes</h2>

The `extends` keyword is used in class declarations/expressions to create a class which is a child of another class. It can be used to subclass custom classes as well as built-in objects. The syntax would be as below,

```javascript
class ChildClass extends ParentClass { ... }
```

Let's take an example of Square subclass from Polygon parent class,

```javascript
class Square extends Rectangle {
    constructor(length) {
        super(length, length);
        this.name = "Square";
    }

    get area() {
        return this.width * this.height;
    }

    set area(value) {
        this.area = value;
    }
}
```

**[⬆ Back to Top](#table-of-contents)**














