### Table of Contents

| No. | Questions                                                                                                                                     |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you redeclare variables in switch block without an error](#How-do-you-redeclare-variables-in-switch-block-without-an-error)           |
| 2   | [What are the pros and cons of for loop](#What-are-the-pros-and-cons-of-for-loop)                                                             |
| 3   | [What are break and continue statements](#What-are-break-and-continue-statements)                                                             |
| 4   | [What are js labels](#What-are-js-labels)                                                                                                     |
| 5   | [What are the conventions to be followed for the usage of switch case](#What-are-the-conventions-to-be-followed-for-the-usage-of-switch-case) |
| 6   | [What is the purpose of switch-case](#What-is-the-purpose-of-switch-case)                                                                     |
| 7   | [What are the two types of loops in javascript](#What-are-the-two-types-of-loops-in-javascript)                                               |
| 8   | [What is an empty statement and purpose of it](#What-is-an-empty-statement-and-purpose-of-it)                                                 |
| 9   | [What is an event loop](#What-is-an-event-loop)                                                                                               |
| 10  | [How do you create an infinite loop](#How-do-you-create-an-infinite-loop)                                                                     |
| 11  | [Why do you need to avoid with statement](#Why-do-you-need-to-avoid-with-statement)                                                           |
| 12  | [What is the output of below for loops](#What-is-the-output-of-below-for-loops)                                                               |
| 13  | [What is for...of statement](#What-is-for...of-statement)                                                                                     |
| 14  | [What are tasks in event loop](#What-are-tasks-in-event-loop)                                                                                 |
| 15  | [What are different event loops](#What-are-different-event-loops)                                                                             |
| 16  | [What are the differences between for...of and for...in statements](#What-are-the-differences-between-for...of-and-for...in-statements)       |

### <h2>How do you redeclare variables in switch block without an error</h2>

If you try to redeclare variables in a `switch block` then it will cause errors because there is only one block. For example, the below code block throws a syntax error as below,

```javascript
let counter = 1;
switch (x) {
    case 0:
        let name;
        break;
    case 1:
        let name; // SyntaxError for redeclaration.
        break;
}
```

To avoid this error, you can create a nested block inside a case clause and create a new block scoped lexical environment.

```javascript
let counter = 1;
switch (x) {
    case 0: {
        let name;
        break;
    }
    case 1: {
        let name; // No SyntaxError for redeclaration.
        break;
    }
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the pros and cons of for loop</h2>

The for-loop is a commonly used iteration syntax in javascript. It has both pros and cons

#### Pros

1. Works on every environment
2. You can use break and continue flow control statements

#### Cons

1. Too verbose
2. Imperative
3. You might face one-by-off errors

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are break and continue statements</h2>

The break statement is used to "jump out" of a loop. i.e, It breaks the loop and continues executing the code after the loop.

```javascript
for (i = 0; i < 10; i++) {
    if (i === 5) {
        break;
    }
    text += "Number: " + i + "<br>";
}
```

The continue statement is used to "jump over" one iteration in the loop. i.e, It breaks one iteration (in the loop), if a specified condition occurs, and continues with the next iteration in the loop.

```javascript
for (i = 0; i < 10; i++) {
    if (i === 5) {
        continue;
    }
    text += "Number: " + i + "<br>";
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are js labels</h2>

The label statement allows us to name loops and blocks in JavaScript. We can then use these labels to refer back to the code later. For example, the below code with labels avoids printing the numbers when they are same,

```javascript
var i, j;

loop1: for (i = 0; i < 3; i++) {
loop2: for (j = 0; j < 3; j++) {
    if (i === j) {
    continue loop1;
    }
    console.log("i = " + i + ", j = " + j);
}
}

// Output is:
//   "i = 1, j = 0"
//   "i = 2, j = 0"
//   "i = 2, j = 1"
```

```javascript
let sum = 0, a = 1;
outerloop: while (true) { // Label for outer loop
	a = 1;
	innerloop: while (a < 3) { // Label for inner loop
		sum += a;
		if (sum > 12) {
			break outerloop; // Break outer loop from inner loop
		}
		console.log("sum = " + sum);
		a++;
	}
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the conventions to be followed for the usage of switch case</h2>

Below are the list of conventions should be taken care,

1. The expression can be of type either number or string. </br>
2. Duplicate values are not allowed for the expression. </br>
3. The default statement is optional. If the expression passed to switch does not match with any case value then the statement within default case will be executed. </br>
4. The break statement is used inside the switch to terminate a statement sequence. </br>
5. The break statement is optional. But if it is omitted, the execution will continue on into the next case. </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of switch-case</h2>

The switch case statement in JavaScript is used for decision making purposes. In a few cases, using the switch case statement is going to be more convenient than if-else statements. The syntax would be as below,

```javascript
switch (expression)
{
    case value1:
        statement1;
        break;
    case value2:
        statement2;
        break;
    .
    .
    case valueN:
        statementN;
        break;
    default:
        statementDefault;
}
```

The above multi-way branch statement provides an easy way to dispatch execution to different parts of code based on the value of the expression.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the two types of loops in javascript</h2>

1. **Entry Controlled loops:** In this kind of loop type, the test condition is tested before entering the loop body. For example, For Loop and While Loop comes under this category.

2. **Exit Controlled Loops:** In this kind of loop type, the test condition is tested or evaluated at the end of the loop body. i.e, the loop body will execute at least once irrespective of test condition true or false. For example, do-while loop comes under this category.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an empty statement and purpose of it</h2>

The empty statement is a semicolon (;) indicating that no statement will be executed, even if JavaScript syntax requires one. Since there is no action with an empty statement you might think that it's usage is quite less, but the empty statement is occasionally useful when you want to create a loop that has an empty body. For example, you can initialize an array with zero values as below,

```javascript
// Initialize an array a
for (let i = 0; i < a.length; a[i++] = 0);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an event loop</h2>

The event loop is a process that continuously monitors both the call stack and the event queue and checks whether or not the call stack is empty. If the call stack is empty and there are pending events in the event queue, the event loop dequeues the event from the event queue and pushes it to the call stack. The call stack executes the event, and any additional events generated during the execution are added to the end of the event queue.

**Note:** The event loop allows Node.js to perform non-blocking I/O operations, even though JavaScript is single-threaded, by offloading operations to the system kernel whenever possible. Since most modern kernels are multi-threaded, they can handle multiple operations executing in the background.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you create an infinite loop</h2>

You can create infinite loops using for and while loops without using any expressions. The for loop construct or syntax is better approach in terms of ESLint and code optimizer tools,

```javascript
for (;;) {}
while (true) {}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do you need to avoid with statement</h2>

JavaScript's with statement was intended to provide a shorthand for writing recurring accesses to objects. So it can help reduce file size by reducing the need to repeat a lengthy object reference without performance penalty. Let's take an example where it is used to avoid redundancy when accessing an object several times.

```javascript
a.b.c.greeting = "welcome";
a.b.c.age = 32;
```

Using `with` it turns this into:

```javascript
with (a.b.c) {
greeting = "welcome";
age = 32;
}
```

But this `with` statement creates performance problems since one cannot predict whether an argument will refer to a real variable or to a property inside the with argument.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the output of below for loops</h2>

```javascript
for (var i = 0; i < 4; i++) {
    setTimeout(() => console.log(i)); // global scope
}

for (let i = 0; i < 4; i++) {
    setTimeout(() => console.log(i)); // block scope
}
```

The output of the above for loops is 4 4 4 4 and 0 1 2 3

**Explanation:** Due to the event queue/loop of javascript, the `setTimeout` callback function is called after the loop has been executed. Since the variable i is declared with the `var` keyword it became a global variable and the value was equal to 4 using iteration when the time `setTimeout` function is invoked. Hence, the output of the first loop is `4 4 4 4`.

Whereas in the second loop, the variable i is declared as the `let` keyword it becomes a block scoped variable and it holds a new value(0, 1 ,2 3) for each iteration. Hence, the output of the first loop is `0 1 2 3`.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is for...of statement</h2>

The for...of statement creates a loop iterating over iterable objects or elements such as built-in String, Array, Array-like objects (like arguments or NodeList), TypedArray, Map, Set, and user-defined iterables. The basic usage of for...of statement on arrays would be as below,

```javascript
let arrayIterable = [10, 20, 30, 40, 50];

for (let value of arrayIterable) {
    value++;
    console.log(value); // 11 21 31 41 51
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are tasks in event loop</h2>

A task is any javascript code/program which is scheduled to be run by the standard mechanisms such as initially starting to run a program, run an event callback, or an interval or timeout being fired. All these tasks are scheduled on a task queue.
Below are the list of use cases to add tasks to the task queue,

1. When a new javascript program is executed directly from console or running by the `<script>` element, the task will be added to the task queue. </br>
2. When an event fires, the event callback added to task queue </br>
3. When a setTimeout or setInterval is reached, the corresponding callback added to task queue </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are different event loops</h2>

In JavaScript, there are multiple event loops that can be used depending on the context of your application. The most common event loops are:

1. The Browser Event Loop </br>
2. The Node.js Event Loop </br>


- Browser Event Loop: The Browser Event Loop is used in client-side JavaScript applications and is responsible for handling events that occur within the browser environment, such as user interactions (clicks, keypresses, etc.), HTTP requests, and other asynchronous actions.

- The Node.js Event Loop is used in server-side JavaScript applications and is responsible for handling events that occur within the Node.js runtime environment, such as file I/O, network I/O, and other asynchronous actions.

**[⬆ Back to Top](#table-of-contents)**

### </h2>What are the differences between for...of and for...in statements</h2>

Both for...in and for...of statements iterate over js data structures. The only difference is over what they iterate:

1. for..in iterates over all enumerable property keys of an object </br>
2. for..of iterates over the values of an iterable object. <br>

Let's explain this difference with an example,

```javascript
let arr = ["a", "b", "c"];

arr.newProp = "newVlue";

// key are the property keys
for (let key in arr) {
 console.log(key); // 0, 1, 2 & newValue
}

// value are the property values
for (let value of arr) {
 console.log(value); // a, b, c
}
```

Since for..in loop iterates over the keys of the object, the first loop logs 0, 1, 2 and newProp while iterating over the array object. The for..of loop iterates over the values of a arr data structure and logs a, b, c in the console.

**[⬆ Back to Top](#table-of-contents)**

