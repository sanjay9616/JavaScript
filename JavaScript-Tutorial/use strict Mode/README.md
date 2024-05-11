<h1>use-strict Mode in JS</h1>

The "use strict" directive was new in ECMAScript version 5.

It is not a statement, but a literal expression, ignored by earlier versions of JavaScript.

The purpose of "use strict" is to indicate that the code should be executed in "strict mode".

With strict mode, you can not, for example, use undeclared variables.

**Example**

```js
"use strict";
x = 3.14;       // This will cause an error because x is not declared
```
```js
"use strict";
myFunction();

function myFunction() {
  y = 3.14;   // This will also cause an error because y is not declared
}
```
```js
"use strict";
x = {p1:10, p2:20};      // This will cause an error
```
```js
"use strict";
let x = 3.14;
delete x;                // This will cause an error
```
```js
"use strict";
function x(p1, p2) {};
delete x;                // This will cause an error 
```
```js
"use strict";
function x(p1, p1) {};   // This will cause an error
```
```js
"use strict"; // Octal numeric literals are not allowed:
let x = 010;             // This will cause an error
```
```js
"use strict";
let x = "\010";            // This will cause an error
```
```js
"use strict"; // Octal escape characters are not allowed:
x = 3.14;       // This will cause an error because x is not declared
```
```js
"use strict";
const obj = {}; // Writing to a read-only property is not allowed:
Object.defineProperty(obj, "x", {value:0, writable:false});

obj.x = 3.14;            // This will cause an error
```
```js
"use strict";
delete Object.prototype; // This will cause an error
```