### Table of Contents

| No. | Questions                                                                                                                         |
| --- | --------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are the differences between primitives and non-primitives](#What-are-the-differences-between-primitives-and-non-primitives) |
| 2   | [What are primitive data types](#What-are-primitive-data-types)                                                                   |
| 3   | [How do you detect primitive or non primitive value type](#How-do-you-detect-primitive-or-non-primitive-value-type)               |
| 4   | [What is JSON](#What-is-JSON)                                                                                                     |
| 5   | [What is JSON and its common operations](#What-is-JSON-and-its-common-operations)                                                 |
| 6   | [What are the syntax rules of JSON](#What-are-the-syntax-rules-of-JSON)                                                           |
| 7   | [What is the purpose JSON stringify](#What-is-the-purpose-JSON-stringify)                                                         |
| 8   | [How do you parse JSON string](#How-do-you-parse-JSON-string)                                                                     |
| 9   | [Why do you need JSON](#Why-do-you-need-JSON)                                                                                     |
| 10  | [How do you define JSON arrays](#How-do-you-define-JSON-arrays)                                                                   |


<h1><span style="color:blue">InterView Questions and Answers on Basics data types</span></h1>

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

<h1>InterView Questions and Answers based on JSON</h1>

### <h2>What is JSON</h2>

JSON (JavaScript Object Notation) is a lightweight format that is used for data interchanging. It is based on a subset of JavaScript language in the way objects are built in JavaScript.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is JSON and its common operations</h2>

**JSON** is a text-based data format following JavaScript object syntax, which was popularized by `Douglas Crockford`. It is useful when you want to transmit data across a network. It is basically just a text file with an extension of .json, and a MIME type of application/json

**Parsing:** Converting a string to a native object

```javascript
JSON.parse(text);
```

**Stringification:** Converting a native object to a string so that it can be transmitted across the network

```javascript
JSON.stringify(object);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the syntax rules of JSON</h2>

Below are the list of syntax rules of JSON

1. The data is in name/value pairs </br>
2. The data is separated by commas </br>
3. Curly braces hold objects </br>
4. Square brackets hold arrays </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose JSON stringify</h2>

When sending data to a web server, the data has to be in a string format. You can achieve this by converting JSON object into a string using stringify() method.

```javascript
var userJSON = { name: "John", age: 31 };
var userString = JSON.stringify(userJSON);
console.log(userString); //"{"name":"John","age":31}"
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you parse JSON string</h2>

When receiving the data from a web server, the data is always in a string format. But you can convert this string value to a javascript object using parse() method.

```javascript
var userString = '{"name":"John","age":31}';
var userJSON = JSON.parse(userString);
console.log(userJSON); // {name: "John", age: 31}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do you need JSON</h2>

When exchanging data between a browser and a server, the data can only be text. Since JSON is text only, it can easily be sent to and from a server, and used as a data format by any programming language.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you define JSON arrays</h2>

JSON arrays are written inside square brackets and arrays contain javascript objects. For example, the JSON array of users would be as below,

```javascript
"users":[
    {"firstName":"John", "lastName":"Abrahm"},
    {"firstName":"Anna", "lastName":"Smith"},
    {"firstName":"Shane", "lastName":"Warn"}
]
```

**[⬆ Back to Top](#table-of-contents)**