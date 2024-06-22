<h1>Number</h1>

JavaScript has only one type of number. Numbers can be written with or without decimals.

### Table of Contents

| No. | Topic                                                               |
| --- | ------------------------------------------------------------------- |
| 1   | [Integer Precision](#Integer-Precision)                             |
| 2   | [Adding Numbers and Strings](#Adding-Numbers-and-Strings)           |
| 3   | [Numeric Strings](#Numeric-Strings)                                 |
| 4   | [NaN - Not a Number](#NaN---Not-a-Number)                           |
| 5   | [Infinity](#Infinity)                                               |
| 6   | [Hexadecimal](#Hexadecimal)                                         |
| 7   | [JavaScript Numbers as Objects](#JavaScript-Numbers-as-Objects)     |
| 8   | [Number Methods](#Number-Methods)                                   |
| 9   | [Number Properties](#Number-Properties)                             |

```javascript
let x = 3.14;    // A number with decimals
let y = 3;       // A number without decimals
```

Extra large or extra small numbers can be written with scientific (exponent) notation:

```javascript
let x = 123e5;    // 12300000
let y = 123e-5;   // 0.00123
```

JavaScript Numbers are Always 64-bit Floating Point, Unlike many other programming languages, JavaScript does not define different types of numbers, like integers, short, long, floating-point etc.

### <h2>Integer Precision</h2>

Integers (numbers without a period or exponent notation) are accurate up to 15 digits.

```javascript
let x = 999999999999999;   // x will be 999999999999999
let y = 9999999999999999;  // y will be 10000000000000000
```

**Floating Precision:**

```javascript
let x = 0.2 + 0.1; // Floating point arithmetic is not always 100% accurate
console.log(x) // 0.30000000000000004

let x = (0.2 * 10 + 0.1 * 10) / 10; // To solve the problem above, it helps to multiply and divide
console.log(x) // 0.3
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Adding Numbers and Strings</h2>

JavaScript uses the + operator for both addition and concatenation, Numbers are added. Strings are concatenated.

If you add two numbers, the result will be a number:

```javascript
let x = 10;
let y = 20;
let z = x + y;
console.log(z) // 30
```

If you add two strings, the result will be a string concatenation:

```javascript
let x = "10";
let y = "20";
let z = x + y;
console.log(z) // 1020
```

If you add a number and a string, the result will be a string concatenation:

```javascript
let x = 10;
let y = "20";
let z = x + y;
console.log(z) // 1020
```

If you add a string and a number, the result will be a string concatenation:

```javascript
let x = "10";
let y = 20;
let z = x + y;
console.log(z) // 1020
```

A common **mistake** is to expect this result to be 30:

```javascript
let x = 10;
let y = 20;
let z = "The result is: " + x + y;
console.log(z) // The result is: 1020
```

A common mistake is to expect this result to be 102030:

```javascript
let x = 10;
let y = 20;
let z = "30";
let result = x + y + z;
console.log(result) // 3030
```

The JavaScript interpreter works from left to right.

First 10 + 20 is added because x and y are both numbers.

Then 30 + "30" is concatenated because z is a string.

**[⬆ Back to Top](#table-of-contents)**

### <h2>Numeric Strings</h2>

JavaScript strings can have numeric content

JavaScript will try to convert strings to numbers in all numeric operations:

```javascript
let x = "100";
let y = "10";
let z = x / y;
console.log(z) // 10

let x = "100";
let y = "10";
let z = x * y;
console.log(z) // 1000

let x = "100";
let y = "10";
let z = x - y;
console.log(z) // 90

// But this will not work:

let x = "100";
let y = "10";
let z = x + y;
console.log(z) // 10010
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>NaN - Not a Number</h2>

NaN is a JavaScript reserved word indicating that a number is not a legal number, Trying to do arithmetic with a non-numeric string will result in NaN (Not a Number):

```javascript
let x = 100 / "Apple";
console.log(x) // NaN

let x = 100 / "10"; // However, if the string is numeric, the result will be a number
console.log(x) // 10
```

You can use the global JavaScript function isNaN() to find out if a value is a not a number:

```javascript
let x = 100 / "Apple";
console.log(isNaN(x)) // true

let x = NaN;
let y = 5;
let z = x + y;
console.log(z) // NaN

let x = NaN;
let y = "5";
let z = x + y; // Or the result might be a concatenation like NaN5
console.log(z) // NaN5

console.log(typeof NaN) // number
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Infinity</h2>

Infinity (or -Infinity) is the value JavaScript will return if you calculate a number outside the largest possible number

```javascript
let myNumber = 2;
// Execute until Infinity
while (myNumber != Infinity) {
  myNumber = myNumber * myNumber;
  console.log(myNumber)
}

// Output
4
16
256
65536
4294967296
18446744073709552000
3.402823669209385e+38
1.157920892373162e+77
1.3407807929942597e+154
Infinity

let x =  2 / 0;
let y = -2 / 0;
console.log(x, y) // Infinity -Infinity

console.log(typeof Infinity) // number
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Hexadecimal</h2>

JavaScript interprets numeric constants as hexadecimal if they are preceded by 0x.

```javascript
let x = 0xFF;
console.log(x) // 255

// By default, JavaScript displays numbers as base 10 decimals.
// But you can use the toString() method to output numbers from base 2 to base 36.
// Hexadecimal is base 16. Decimal is base 10. Octal is base 8. Binary is base 2.

let myNumber = 32;
console.log(myNumber.toString(32)) // 10
console.log(myNumber.toString(12)) // 28
console.log(myNumber.toString(10)) // 32
console.log(myNumber.toString(8)) // 40
console.log(myNumber.toString(2)) // 100000
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JavaScript Numbers as Objects</h2>

Normally JavaScript numbers are primitive values created from literals

```javascript
let x = 123;
let y = new Number(123); // The new keyword complicates the code and slows down execution speed.Number Objects can produce unexpected results:
console.log(typeof(x), typeof(y)) // number object

let x = 500;
let y = new Number(500);
console.log(x == y, x === y) // true, false

let x = new Number(500);
let y = new Number(500);
console.log(x == y, x === y) // false, false // Comparing two JavaScript objects always returns false.
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Number Methods</h2>

These number methods can be used on all JavaScript numbers

| Method          | Description                                        |
| --------------- | -------------------------------------------------- |
| toString()      | Returns a number as a string                       |
| toExponential() | Returns a number written in exponential notation   |
| toFixed()       | Returns a number written with a number of decimals |
| toPrecision()   | Returns a number written with a specified length   |
| valueOf()       | Returns a number as a number                       |

```javascript
console.log((123).toString()); // 123
console.log((100 + 23).toString()); // 123

let x = 9.656;
let res1 = x.toExponential(2);
let res2 = x.toExponential(4);
let res3 = x.toExponential(6);
console.log(res1, res2, res3) // 9.66e+0 9.6560e+0 9.656000e+0

let x = 9.656;
let res1 = x.toFixed(0);
let res2 = x.toFixed(2);
let res3 = x.toFixed(4);
let res4 = x.toFixed(6);
console.log(res1, res2, res3, res4) // 10 9.66 9.6560 9.656000

let x = 9.656;
let res1 = x.toPrecision();
let res2 = x.toPrecision(2);
let res3 = x.toPrecision(4);
let res4 = x.toPrecision(6);
console.log(res1, res2, res3, res4) // 9.656 9.7 9.656 9.65600

let x = 123;
let res1 = x.valueOf();
let res2 = (123).valueOf();
let res3 = (100 + 23).valueOf();
console.log(res1, res2, res3) // 123, 123, 123
```

**Converting Variables to Numbers:**

| Method       | Description                                             |
| ------------ | ------------------------------------------------------- |
| Number()     | Returns a number converted from its argument.           |
| parseFloat() | Parses its argument and returns a floating point number |
| parseInt()   | Parses its argument and returns a whole number          |

```javascript
console.log(Number(true)); // 1
console.log(Number(false)); // 0
console.log(Number("10")); // 10
console.log(Number("  10")); // 10
console.log(Number("10  ")); // 10
console.log(Number(" 10  ")); // 10
console.log(Number("10.33")); // 10.33
console.log(Number("10,33")); // NaN
console.log(Number("10 33")); // Nan
console.log(Number("John")); // NaN

// Number() can also convert a date to a number - The Date() method returns the number of milliseconds since 1.1.1970.
// The number of milliseconds between 1970-01-02 and 1970-01-01 is 86400000
console.log(Number(new Date("1970-01-01"))) // 0
console.log(Number(new Date("1970-01-02"))) // 86400000
console.log(Number(new Date("2017-09-30"))) // 1506729600000
console.log((new Date("2017-09-30")).getTime()) // 1506729600000

// parseInt() parses a string and returns a whole number. Spaces are allowed. Only the first number is returned:
console.log(parseInt("-10")); // -10
console.log(parseInt("-10.33")); // -10
console.log(parseInt("10")); // 10
console.log(parseInt("10.33")); // 10
console.log(parseInt("10 20 30")); // 10
console.log(parseInt("10 years")); // 10
console.log(parseInt("years 10")); // NaN

// parseFloat() parses a string and returns a number. Spaces are allowed. Only the first number is returned:
console.log(parseFloat("10")); // 10
console.log(parseFloat("10.33")); // 10.33
console.log(parseFloat("10 20 30")); // 10
console.log(parseFloat("10 years")); // 10
console.log(parseFloat("years 10")); // NaN
```

**Number Object Methods**

| Method                 | Description                                    |
| ---------------------- | ---------------------------------------------- |
| Number.isInteger()     | Returns true if the argument is an integer     |
| Number.isSafeInteger() | Returns true if the argument is a safe integer |
| Number.parseFloat()    | Converts a string to a number                  |
| Number.parseInt()      | Converts a string to a whole number            |

```javascript
console.log(Number.isInteger(10)); // true
console.log(Number.isInteger(10.5)); // false

// A safe integer is an integer that can be exactly represented as a double precision number.
// Safe integers are all integers from -(253 - 1) to +(253 - 1).
// This is safe: 9007199254740991. This is not safe: 9007199254740992.
console.log(Number.isSafeInteger(10)); // true
console.log(Number.isSafeInteger(12345678901234567890)); // false

//Spaces are allowed. Only the first number is returned
console.log(Number.parseFloat("10")); // 10
console.log(Number.parseFloat("10.33")); // 10.33
console.log(Number.parseFloat("10 20 30")); // 10
console.log(Number.parseFloat("10 years")); // 10
console.log(Number.parseFloat("years 10")); // NaN

console.log(Number.parseInt("-10")); // -10
console.log(Number.parseInt("-10.33")); // -10
console.log(Number.parseInt("10")); // 10
console.log(Number.parseInt("10.33")); // 10
console.log(Number.parseInt("10 20 30")); // 10
console.log(Number.parseInt("10 years")); // 10
console.log(Number.parseInt("years 10")); // NaN
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Number Properties</h2>

| Property          | Description                                           |
| ----------------- | ----------------------------------------------------- |
| EPSILON           | The difference between 1 and the smallest number > 1. |
| MAX_VALUE         | The largest number possible in JavaScript             |
| MIN_VALUE         | The smallest number possible in JavaScript            |
| MAX_SAFE_INTEGER  | The maximum safe integer (2^53 - 1)                   |
| MIN_SAFE_INTEGER  | The minimum safe integer -(2^53 - 1)                  |
| POSITIVE_INFINITY | Infinity (returned on overflow)                       |
| NEGATIVE_INFINITY | Negative infinity (returned on overflow)              |
| NaN               | A "Not-a-Number" value                                |

```javascript
let x = Number.EPSILON;
console.log(x) // 2.220446049250313e-16

let x = Number.MAX_VALUE;
console.log(x) // 1.7976931348623157e+308

let x = 6;
console.log(x.MAX_VALUE) // undefined

let x = Number.MIN_VALUE;
console.log(x) // 5e-324

let x = Number.MAX_SAFE_INTEGER;
console.log(x) // 9007199254740991

let x = Number.MIN_SAFE_INTEGER;
console.log(x) // -9007199254740991

let x = Number.POSITIVE_INFINITY;
console.log(x) // Infinity

let x = 1 / 0;
console.log(x) // Infinity

let x = Number.NEGATIVE_INFINITY;
console.log(x) // -Infinity

let x = -1 / 0;
console.log(x) // -Infinity

let x = Number.NaN;
console.log(x) // NaN

let x = 100 / "Apple";
console.log(x) // NaN
```

**[⬆ Back to Top](#table-of-contents)**

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>