### Table of Contents

| No. | Questions                                                                                                                         |
| --- | --------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are the differences between primitives and non-primitives](#What-are-the-differences-between-primitives-and-non-primitives) |
| 2   | [What are primitive data types](#What-are-primitive-data-types)                                                                   |
| 3   | [How do you detect primitive or non primitive value type](#How-do-you-detect-primitive-or-non-primitive-value-type)               |

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
```

If the value is a primitive data type, the Object constructor creates a new wrapper object for the value. But If the value is a non-primitive data type (an object), the Object constructor will give the same object.

**[⬆ Back to Top](#table-of-contents)**
