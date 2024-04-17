### Table of Contents

| No. | Questions                                                                                                                           |
| --- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How to verify if a variable is an array](#How-to-verify-if-a-variable-is-an-array)                                                 |
| 2   | [Is const variable makes the value immutable](#Is-const-variable-makes-the-value-immutable)                                         |
| 3   | [What is the precedence order between local and global variables](#What-is-the-precedence-order-between-local-and-global-variables) |
| 4   | [How do you assign default values to variables](#How-do-you-assign-default-values-to-variables)                                     |
| 5   | [What are the benefits of keeping declarations at the top](#What-are-the-benefits-of-keeping-declarations-at-the-top)               |

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

### <h2>How do you assign default values to variables<h2>

You can use the logical or operator `||` in an assignment expression to provide a default value. The syntax looks like as below,

```javascript
var a = b || c;
```

As per the above expression, variable 'a 'will get the value of 'c' only if 'b' is falsy (if is null, false, undefined, 0, empty string, or NaN), otherwise 'a' will get the value of 'b'.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the benefits of keeping declarations at the top<h2>

It is recommended to keep all declarations at the top of each script or function. The benefits of doing this are,

1. Gives cleaner code
2. It provides a single place to look for local variables
3. Easy to avoid unwanted global variables
4. It reduces the possibility of unwanted re-declarations

**[⬆ Back to Top](#table-of-contents)**