### Table of Contents

| No. | Questions                                                                                                                                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are the differences between primitives and non-primitives](#What-are-the-differences-between-primitives-and-non-primitives)           |
| 2   | [What are primitive data types](#What-are-primitive-data-types)                                                                             |
| 3   | [How do you detect primitive or non primitive value type](#How-do-you-detect-primitive-or-non-primitive-value-type)                         |
| 4   | [What is the difference between null and undefined](#What-is-the-difference-between-null-and-undefined)                                     |
| 5   | [What are the differences between undeclared and undefined variables](#What-are-the-differences-between-undeclared-and-undefined-variables) |
| 6   | [What is the difference between isNaN and Number.isNaN](#What-is-the-difference-between-isNaN-and-Number.isNaN)                             |

### <h2>What are the differences between primitives and non-primitives</h2>

JavaScript language has both primitives and non-primitives but there are few differences between them as below,

| Primitives                 | Non-primitives       |
| -------------------------- | -------------------- |
| These types are predefined | Created by developer |
| These are immutable        | Mutable              |
| Compare by value           | Compare by reference |
| Stored in Stack            | Stored in heap       |
| Contain certain value      | Can contain NULL too |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are primitive data types</h2>

A primitive data type is data that has a primitive value (which has no properties or methods). There are 7 types of primitive data types.

1. string </br>
2. number </br>
3. boolean </br>
4. null </br>
5. undefined </br>
6. bigint </br>
7. symbol </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you detect primitive or non primitive value type</h2>

In JavaScript, primitive types include boolean, string, number, BigInt, null, Symbol and undefined. Whereas non-primitive types include the Objects. But you can easily identify them with the below function,

```javascript
function isPrimitive(val) {
    return Object(val) !== val;
}
console.log(isPrimitive(30));  // true
console.log(isPrimitive({})); // false
console.log(Object({}) !== {}) // **Warning** - true
```

If the value is a primitive data type, the Object constructor creates a new wrapper object for the value. But If the value is a non-primitive data type (an object), the Object constructor will give the same object.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between null and undefined</h2>

Below are the main differences between null and undefined,

| Null                                                                                            | Undefined                                                                                               |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| It is an assignment value which indicates that variable points to no object.                    | It is not an assignment value where a variable has been declared but has not yet been assigned a value. |
| Type of null is object                                                                          | Type of undefined is undefined                                                                          |
| The null value is a primitive value that represents the null, empty, or non-existent reference. | The undefined value is a primitive value used when a variable has not been assigned a value.            |
| Indicates the absence of a value for a variable                                                 | Indicates absence of variable itself                                                                    |
| Converted to zero (0) while performing primitive operations                                     | Converted to NaN while performing primitive operations                                                  |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between undeclared and undefined variables</h2>

Below are the major differences between undeclared(not defined) and undefined variables,

| undeclared                                                                                  | undefined                                                                              |
| ------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| These variables do not exist in a program and are not declared                              | These variables declared in the program but have not assigned any value                |
| If you try to read the value of an undeclared variable, then a runtime error is encountered | If you try to read the value of an undefined variable, an undefined value is returned. |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between isNaN and Number.isNaN</h2>

1. **isNaN**: The global function `isNaN` converts the argument to a Number and returns true if the resulting value is NaN. </br>
2. **Number.isNaN**: This method does not convert the argument. But it returns true when the type is a Number and value is NaN. </br>

Let's see the difference with an example,

```javascript
isNaN(‘hello’);   // true
Number.isNaN('hello'); // false
```

**[⬆ Back to Top](#table-of-contents)**