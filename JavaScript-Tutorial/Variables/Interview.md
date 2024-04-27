### Table of Contents

| No. | Questions                                                                                                                           |
| --- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How to verify if a variable is an array](#How-to-verify-if-a-variable-is-an-array)                                                 |
| 2   | [Is const variable makes the value immutable](#Is-const-variable-makes-the-value-immutable)                                         |
| 3   | [What is the precedence order between local and global variables](#What-is-the-precedence-order-between-local-and-global-variables) |
| 4   | [How do you assign default values to variables](#How-do-you-assign-default-values-to-variables)                                     |
| 5   | [What are the benefits of keeping declarations at the top](#What-are-the-benefits-of-keeping-declarations-at-the-top)               |
| 6   | [What is the purpose of the let keyword](#What-is-the-purpose-of-the-let-keyword)                                                   |
| 7   | [What is the reason to choose the name let as a keyword](#What-is-the-reason-to-choose-the-name-let-as-a-keyword)                   |
| 8   | [Can I redeclare let and const variables](#Can-I-redeclare-let-and-const-variables)                                                 |
| 9   | [What are global variables](#What-are-global-variables)                                                                             |
| 10  | [What are the problems with global variables](#What-are-the-problems-with-global-variables)                                         |

### <h2>How to verify if a variable is an array<h2>

It is possible to check if a variable is an array instance using 3 different ways,

**1. Array.isArray() method:**

The `Array.isArray(value)` utility function is used to determine whether value is an array or not. This function returns a true boolean value if the variable is an array and a false value if it is not.

```javascript
const numbers = [1, 2, 3];
const user = { name: "John" };
Array.isArray(numbers); // true
Array.isArray(user); //false
```

**2. instanceof operator:**

The instanceof operator is used to check the type of an array at run time. It returns true if the type of a variable is an Array other false for other type.

```javascript
const numbers = [1, 2, 3];
const user = { name: "John" };
console.log(numbers instanceof Array); // true
console.log(user instanceof Array); // false
```

**3. Checking constructor type:**

The constructor property of the variable is used to determine whether the variable Array type or not.

```javascript
const numbers = [1, 2, 3];
const user = { name: "John" };
console.log(numbers.constructor === Array); // true
console.log(user.constructor === Array); // false
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Is const variable makes the value immutable</h2>

No, the const variable doesn't make the value immutable. But it disallows subsequent assignments(i.e, You can declare with assignment but can't assign another value later)

```javascript
const userList = [];
userList.push("John"); // Can mutate even though it can't re-assign
console.log(userList); // ['John']
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the precedence order between local and global variables</h2>

A local variable takes precedence over a global variable with the same name. Let's see this behavior in an example.

```javascript
var msg = "Good morning";
function greeting() {
msg = "Good Evening";
console.log(msg); // Good Evening
}
greeting();
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you assign default values to variables</h2>

You can use the logical or operator `||` in an assignment expression to provide a default value. The syntax looks like as below,

```javascript
var a = b || c;
```

As per the above expression, variable 'a 'will get the value of 'c' only if 'b' is falsy (if is null, false, undefined, 0, empty string, or NaN), otherwise 'a' will get the value of 'b'.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the benefits of keeping declarations at the top</h2>

It is recommended to keep all declarations at the top of each script or function. The benefits of doing this are,

1. Gives cleaner code
2. It provides a single place to look for local variables
3. Easy to avoid unwanted global variables
4. It reduces the possibility of unwanted re-declarations

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of the let keyword</h2>

The `let` statement declares a **block scope local variable**. Hence the variables defined with let keyword are limited in scope to the block, statement, or expression on which it is used. Whereas variables declared with the `var` keyword used to define a variable globally, or locally to an entire function regardless of block scope.

Let's take an example to demonstrate the usage,

```javascript
let counter = 30;
if (counter === 30) {
    let counter = 31;
    console.log(counter); // 31
}
console.log(counter); // 30 (because the variable in if block won't exist here)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the reason to choose the name let as a keyword</h2>

`let` is a mathematical statement that was adopted by early programming languages like **Scheme** and **Basic**. It has been borrowed from dozens of other languages that use `let` already as a traditional keyword as close to `var` as possible.

**[⬆ Back to Top](#table-of-contents)**

### <h2>Can I redeclare let and const variables</h2>

No, you cannot redeclare let and const variables. If you do, it throws below error

```bash
Uncaught SyntaxError: Identifier 'someVariable' has already been declared
```

**Explanation:** The variable declaration with `var` keyword refers to a function scope and the variable is treated as if it were declared at the top of the enclosing scope due to hoisting feature. So all the multiple declarations contributing to the same hoisted variable without any error. Let's take an example of re-declaring variables in the same scope for both var and let/const variables.

```javascript
var name = "John";
function myFunc() {
    var name = "Nick";
    var name = "Abraham"; // Re-assigned in the same function block
    alert(name); // Abraham
}
myFunc();
alert(name); // John
```

The block-scoped multi-declaration throws syntax error,

```javascript
let name = "John";
function myFunc() {
    let name = "Nick";
    let name = "Abraham"; // Uncaught SyntaxError: Identifier 'name' has already been declared
    alert(name);
}

myFunc();
alert(name);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are global variables</h2>

Global variables are those that are available throughout the length of the code without any scope. The var keyword is used to declare a local variable but if you omit it then it will become global variable

```javascript
msg = "Hello"; // var is missing, it becomes global variable
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the problems with global variables</h2>

The problem with global variables is the conflict of variable names of local and global scope. It is also difficult to debug and test the code that relies on global variables.

**[⬆ Back to Top](#table-of-contents)**