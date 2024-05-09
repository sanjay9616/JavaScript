### Table of Contents

| No. | Questions                                                                 |
| --- | ------------------------------------------------------------------------- |
| 1   | [What is Hoisting](#What-is-Hoisting)                                     |
| 2   | [What is global execution context](#What-is-global-execution-context)     |
| 3   | [What is function execution context](#What-is-function-execution-context) |

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