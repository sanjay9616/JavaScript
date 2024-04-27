### Table of Contents

| No. | Questions                                                                         |
| --- | --------------------------------------------------------------------------------- |
| 1   | [What is JSON](#What-is-JSON)                                                     |
| 2   | [What is JSON and its common operations](#What-is-JSON-and-its-common-operations) |
| 3   | [What are the syntax rules of JSON](#What-are-the-syntax-rules-of-JSON)           |
| 4   | [What is the purpose JSON stringify](#What-is-the-purpose-JSON-stringify)         |
| 5   | [How do you parse JSON string](#How-do-you-parse-JSON-string)                     |
| 6   | [Why do you need JSON](#Why-do-you-need-JSON)                                     |
| 7   | [How do you define JSON arrays](#How-do-you-define-JSON-arrays)                   |

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