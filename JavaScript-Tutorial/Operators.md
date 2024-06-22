<h1>Operators in JS:</h1>

### Table of Contents

| No. | Topics                                        |
| --- | --------------------------------------------- |
| 1   | [Arithmetic Operators](#Arithmetic-Operators) |
| 2   | [Assignment Operators](#Assignment-Operators) |
| 3   | [Comparison Operators](#Comparison-Operators) |
| 4   | [String Operators](#String-Operators)         |
| 5   | [Logical Operators](#Logical-Operators)       |
| 6   | [Bitwise Operators](#Bitwise-Operators)       |
| 7   | [Type Operators](#Type-Operators)             |
| 8   | [Spread Operators](#Spread-Operators)         |
| 9   | [Rest Operators](#Rest-Operators)             |

### <h2>Arithmetic Operators</h2>

Arithmetic Operators are used to perform arithmetic on numbers:

| Operator | Description                  |
| -------- | ---------------------------- |
| +        | Addition                     |
| -        | Subtraction                  |
| *        | Multiplication               |
| **       | Exponentiation (ES2016)      |
| /        | Division                     |
| %        | Modulus (Division Remainder) |
| ++       | Increment                    |
| --       | Decrement                    |

**Examples:**

```javascript
let a = 3;
let x = (100 + 50) * a;
console.log(x) // 450
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Assignment Operators</h2>

Assignment operators assign values to JavaScript variables.

| Operator | Example | Same As    |
| -------- | ------- | ---------- |
| =        | x = y   | x = y      |
| +=       | x += y  | x = x + y  |
| -=       | x -= y  | x = x - y  |
| *=       | x *= y  | x = x * y  |
| /=       | x /= y  | x = x / y  |
| %=       | x %= y  | x = x % y  |
| **=      | x **= y | x = x ** y |

**Examples:**

```javascript
let x = 10;
x += 5;
console.log(x) // 15
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Comparison Operators</h2>

Arithmetic Operators are used to perform arithmetic on numbers:

| Operator | Description                       |
| -------- | --------------------------------- |
| ==       | equal to                          |
| ===      | equal value and equal type        |
| !=       | not equal                         |
| !==      | not equal value or not equal type |
| >        | greater than                      |
| <        | less than                         |
| >=       | greater than or equal to          |
| <=       | less than or equal to             |
| ?        | ternary operator                  |

**Examples:**

```javascript
//strings are compared alphabetically
let text1 = "A";
let text2 = "B";
let result = text1 < text2;
console.log(result) // true

let text1 = "20";
let text2 = "5";
let result = text1 < text2;
console.log(result) // true
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>String Operators</h2>

```javascript
let text1 = "John";
let text2 = "Doe";
let text3 = text1 + " " + text2; // The + can also be used to add (concatenate) strings:
console.log(text3) // John Doe

let text1 = "What a very ";
text1 += "nice day"; // The += assignment operator can also be used to add (concatenate) strings
console.log(text1) // What a very nice day

// Adding two numbers, will return the sum, but adding a number and a string will return a string:
let x = 5 + 5; // 10
let y = "5" + 5; // 55
let z = "Hello" + 5; // Hello5
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Logical Operators</h2>

| Operator   | Description |
| ---------- | ----------- |
| &&         | logical and |
| logical or | logical or  |
| !          | logical not |

**[⬆ Back to Top](#table-of-contents)**

### <h2>Bitwise Operators</h2>

Bit operators work on 32 bits numbers, Any numeric operand in the operation is converted into a 32 bit number. The result is converted back to a JavaScript number.

| Operator | Description          | Example | Same as      | Result | Decimal |
| -------- | -------------------- | ------- | ------------ | ------ | ------- |
| &        | AND                  | 5 & 1   | 0101 & 0001  | 0001   | 1       |
| OR       | OR                   | 5 OR 1  | 0101 OR 0001 | 0101   | 5       |
| ~        | NOT                  | ~ 5     | ~0101        | 1010   | 10      |
| ^        | XOR                  | 5 ^ 1   | 0101 ^ 0001  | 0100   | 4       |
| <<       | left shift           | 5 << 1  | 0101 << 1    | 1010   | 10      |
| >>       | right shift          | 5 >> 1  | 0101 >> 1    | 0010   | 2       |
| >>>      | unsigned right shift | 5 >>> 1 | 0101 >>> 1   | 0010   | 2       |

**[⬆ Back to Top](#table-of-contents)**

### <h2>Type Operators</h2>

| Operator   | Description                                                |
| ---------- | ---------------------------------------------------------- |
| typeof     | Returns the type of a variable                             |
| instanceof | Returns true if an object is an instance of an object type |

**[⬆ Back to Top](#table-of-contents)**

### <h2>Spread Operators</h2>

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

### <h2>Rest Operators</h2>

The rest(...) parameter is converse to the spread operator. while the spread operator expands elements of an iterable, the rest operator compresses them, and allows a function to accept an indefinite number of arguments as an array.

```javascript
sum = (...values) => {
    console.log(values)
    let total = 0
    for(const val of values) {
        total += val
    }
    return total
}
console.log(sum(1, 2, 3)); //Output: 6
console.log(sum(1, 2, 3, 4)); //Output: 10
```

**[⬆ Back to Top](#table-of-contents)**


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>