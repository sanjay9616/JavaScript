### Table of Contents

| No. | Questions                                                                                                                                                   |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is a strict mode in javascript](#What-is-a-strict-mode-in-javascript)                                                                                 |
| 2   | [Why do you need strict mode](#Why-do-you-need-strict-mode)                                                                                                 |
| 3   | [How do you declare strict mode](#How-do-you-declare-strict-mode)                                                                                           |
| 4   | [What are the list of cases error thrown from non-strict mode to strict mode](#What-are-the-list-of-cases-error-thrown-from-non-strict-mode-to-strict-mode) |

### <h2>What is a strict mode in javascript</h2>


Strict Mode is a new feature in ECMAScript 5 that allows you to place a program, or a function, in a “strict” operating context. This way it prevents certain actions from being taken and throws more exceptions. The literal expression `"use strict";` instructs the browser to use the javascript code in the Strict mode.

Strict Mode in Javascript is something that I always hear about in various forums but never actually implemented it. Well, I thought this is a good opportunity to do some research on.

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do you need strict mode</h2>

Strict mode is useful to write "secure" JavaScript by notifying "bad syntax" into real errors. For example, it eliminates accidentally creating a global variable by throwing an error and also throws an error for assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing variable, or a non-existing object.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you declare strict mode</h2>

The strict mode is declared by adding "use strict"; to the beginning of a script or a function.
If declared at the beginning of a script, it has global scope.

```javascript
"use strict";
x = 3.14; // This will cause an error because x is not declared
```

and if you declare inside a function, it has local scope

```javascript
x = 3.14; // This will not cause an error.
myFunction();

function myFunction() {
    "use strict";
    y = 3.14; // This will cause an error
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the list of cases error thrown from non-strict mode to strict mode</h2>

When you apply 'use strict'; syntax, some of the below cases will throw a SyntaxError before executing the script

1. When you use Octal syntax

```javascript
var n = 022;
```

2. Using `with` statement </br>
3. When you use delete operator on a variable name </br>
4. Using eval or arguments as variable or function argument name </br>
5. When you use newly reserved keywords </br>
6. When you declare a function in a block </br>

```javascript
if (someCondition) {
function f() {}
}
```

Hence, the errors from above cases are helpful to avoid errors in development/production environments.

**[⬆ Back to Top](#table-of-contents)**