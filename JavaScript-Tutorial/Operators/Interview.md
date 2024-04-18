### Table of Contents

| No. | Questions                                                                                                                               |
| --- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the purpose of double exclamation](#What-is-the-purpose-of-double-exclamation)                                                 |
| 2   | [What is a comma operator and their Advantagess](#What-is-a-comma-operator-and-their-Advantagess)                                       |
| 3   | [Is the '!--' notation represents a special operator](#Is-the-'!--'-notation-represents-a-special-operator)                             |
| 4   | [What is the purpose of double tilde operator](#What-is-the-purpose-of-double-tilde-operator)                                           |
| 5   | [What is nullish coalescing operator (??)?](#What-is-nullish-coalescing-operator-(??)?)                                                 |
| 6   | [What is a conditional operator in javascript](#What-is-a-conditional-operator-in-javascript)                                           |
| 7   | [Can you apply chaining on conditional operator](#Can-you-apply-chaining-on-conditional-operator)                                       |
| 8   | [What is the purpose of the delete operator](#What-is-the-purpose-of-the-delete-operator)                                               |
| 9   | [What is typeof operator](#What-is-typeof-operator)                                                                                     |
| 10  | [What is a void operator](#What-is-a-void-operator)                                                                                     |
| 11  | [What is an Unary operator](#What-is-an-Unary-operator)                                                                                 |
| 12  | [What is the output of below console statement with unary operator](#What-is-the-output-of-below-console-statement-with-unary-operator) |
| 13  | [How do you create self string using special characters](#How-do-you-create-self-string-using-special-characters)                       |
| 14  | [What is the output of prepend additive operator on falsy values](#What-is-the-output-of-prepend-additive-operator-on-falsy-values)     |
| 15  | [What is a spread operator](#What-is-a-spread-operator)                                                                                 |

### <h2>What is the purpose of double exclamation</h2>

The double exclamation or negation(!!) ensures the resulting type is a boolean. If it was falsey (e.g. 0, null, undefined, etc.), it will be false, otherwise, it will be true.
For example, you can test IE version using this expression as below,

```javascript
let isIE8 = false;
isIE8 = !!navigator.userAgent.match(/MSIE 8.0/);
console.log(isIE8); // returns true or false
```

If you don't use this expression then it returns the original value.

```javascript
console.log(navigator.userAgent.match(/MSIE 8.0/)); // returns either an Array or null
```

**Note:** The expression !! is not an operator, but it is just twice of ! operator.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a comma operator and their Advantagess</h2>

The comma operator is used to evaluate each of its operands from left to right and returns the value of the last operand. This is totally different from comma usage within arrays, objects, and function arguments and parameters. For example, the usage for numeric expressions would be as below,

```javascript
var x = 1;
x = (x++, x);

console.log(x); // 2
```

**Advantage**

It is normally used to include multiple expressions in a location that requires a single expression. One of the common usages of this comma operator is to supply multiple parameters in a `for` loop. For example, the below for loop uses multiple expressions in a single location using comma operator,

```javascript
for (var a = 0, b =10; a <= 10; a++, b--)
```

You can also use the comma operator in a return statement where it processes before returning.

```javascript
function myFunction() {
var a = 1;
return (a += 10), a; // 11
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Is the '!--' notation represents a special operator</h2>

No,that's not a special operator. But it is a combination of 2 standard operators one after the other,

1. A logical not (!) </br>
2. A prefix decrement (--)

At first, the value decremented by one and then tested to see if it is equal to zero or not for determining the truthy/falsy value.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of double tilde operator</h2>

The double tilde operator(~~) is known as double NOT bitwise operator. This operator is a slightly quicker substitute for Math.floor().

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is nullish coalescing operator (??)?</h2>

It is a logical operator that returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand. This can be contrasted with the logical OR (||) operator, which returns the right-hand side operand if the left operand is any falsy value, not only null or undefined.

```js
console.log(null ?? true); // true
console.log(false ?? true); // false
console.log(undefined ?? true); // true
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a conditional operator in javascript</h2>

The conditional (ternary) operator is the only JavaScript operator that takes three operands which acts as a shortcut for if statements.

```javascript
var isAuthenticated = false;
console.log(
isAuthenticated ? "Hello, welcome" : "Sorry, you are not authenticated"
); //Sorry, you are not authenticated
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Can you apply chaining on conditional operator</h2>

Yes, you can apply chaining on conditional operators similar to if … else if … else if … else chain. The syntax is going to be as below,

```javascript
function traceValue(someParam) {
return condition1
    ? value1
    : condition2
    ? value2
    : condition3
    ? value3
    : value4;
}

// The above conditional operator is equivalent to:

function traceValue(someParam) {
if (condition1) {
    return value1;
} else if (condition2) {
    return value2;
} else if (condition3) {
    return value3;
} else {
    return value4;
}
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of the delete operator</h2>

The delete operator is used to delete the property as well as its value.

```javascript
var user = { firstName: "John", lastName:"Doe", age: 20 };
delete user.age;

console.log(user); // {firstName: "John", lastName:"Doe"}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is typeof operator</h2>

You can use the JavaScript typeof operator to find the type of a JavaScript variable. It returns the type of a variable or an expression.

```javascript
typeof "John Abraham"; // Returns "string"
typeof (1 + 2); // Returns "number"
typeof [1, 2, 3]; // Returns "object" because all arrays are also objects
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a void operator</h2>

The `void` operator used to evaluates the given expression and then returns undefined(i.e, without returning value). The syntax would be as below,

```javascript
void expression;
void(expression);
```

Let's display a message without any redirection or reload

```javascript
function foo() {
    return void 10;
}
console.log(foo()); // undefined
```

**Note:** This operator is often used to obtain the undefined primitive value, using "void(0)".

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an Unary operator</h2>

| Operator           | Description                                                          |
| ------------------ | -------------------------------------------------------------------- |
| Unary plus (+)     | Tries to convert the operand into a number                           |
| Unary negation (-) | Tries to convert the operand into a number and negates after         |
| Increment (++)     | Adds one to its operand                                              |
| Decrement (--)     | Decrements by one from its operand                                   |
| Logical NOT (!)    | Converts to boolean value then negates it                            |
| typeof             | Returns a string which is the type of the operand                    |
| delete             | Deletes specific index of an array or specific property of an object |
| void               | Discards a return value of an expression.                            |

A unary operation is an operation with only one operand. This operand comes either before or after the operator.

The unary(+) operator is used to convert a variable to a number.If the variable cannot be converted, it will still become a number but with the value NaN. Let's see this behavior in an action.

```javascript
var x = "100";
var y = +x;
console.log(typeof x, typeof y); // string, number

var a = "Hello";
var b = +a;
console.log(typeof a, typeof b, b); // string, number, NaN
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the output of below console statement with unary operator</h2>

Let's take console statement with unary operator as given below,

```javascript
console.log(+"Hello");
```

The output of the above console log statement returns NaN. Because the element is prefixed by the unary operator and the JavaScript interpreter will try to convert that element into a number type. Since the conversion fails, the value of the statement results in NaN value.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you create self string using special characters</h2>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the output of prepend additive operator on falsy values</h2>

If you prepend the additive(+) operator on falsy values(null, undefined, NaN, false, ""), the falsy value converts to a number value zero. Let's display them on browser console as below,

```javascript
console.log(+null); // 0
console.log(+undefined); // NaN
console.log(+false); // 0
console.log(+NaN); // NaN
console.log(+""); // 0
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a spread operator</h2>

The spread operator and rest parameter have the same syntax which is three dots(…). Even though they have the same syntax they differ in functions

The spread operator helps us expand an iterable ( arrays / objects / strings ) and allows us to quickly copy all or part of an existing array or object into another array or object

```javascript
l=[1,2,3]
console.log([...l]) // [ 1, 2, 3 ]

const numbersOne = [1, 2, 3];
const numbersTwo = [4, 5, 6];
const numbersCombined = [...numbersOne, ...numbersTwo];
console.log(numbersCombined) // [ 1, 2, 3, 4, 5, 6 ]
```

**[⬆ Back to Top](#table-of-contents)**