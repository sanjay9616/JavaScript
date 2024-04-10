<h1>String</h1>

Strings are written with quotes. You can use single or double quotes:

### Table of Contents

| No. | Topic                                                               |
| --- | ------------------------------------------------------------------- |
| 1   | [String Methods](#String-Methods)                                   |
| 2   | [String Search Methods](#String-Search-Methods)                     |
| 3   | [Template Strings](#Template-Strings)                               |
| 4   | [Interview Questions and Answers](#Interview-Questions-and-Answers) |

### <h2>String Methods</h2>

| String Methods        | Description                                                                                                                                 |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| length                | returns the length of a string                                                                                                              |
| at(position)          | returns the character at a specified index (position) in a string (ES2022)                                                                  |
| charAt(position)      | returns the character at a specified index (position) in a string                                                                           |
| charCodeAt(position)  | returns the code of the character at a specified index in a string                                                                          |
| slice(start, end)     | returns the extracted part in a new string. The method takes 2 parameters: start position, and end position (end not included).             |
| substring(start, end) | substring() is similar to slice(). The difference is that start and end values less than 0 are treated as 0 in substring()                  |
| substr(start, length) | substr() is similar to slice().The difference is that the second parameter specifies the length of the extracted part.                      |
| toUpperCase()         | A string is converted to upper case                                                                                                         |
| toLowerCase()         | A string is converted to lower case                                                                                                         |
| concat()              | joins two or more strings. The concat() method can be used instead of the plus operator.                                                    |
| trim()                | removes whitespace from both sides of a string                                                                                              |
| trimStart()           | The trimStart() method works like trim(), but removes whitespace only from the start of a string                                            |
| trimEnd()             | The trimEnd() method works like trim(), but removes whitespace only from the end of a string                                                |
| padStart()            | method pads a string from the start.It pads a string with another string (multiple times) until it reaches a given length (ECMAScript 2017) |
| padEnd()              | method pads a string from the end. It pads a string with another string (multiple times) until it reaches a given length ECMAScript 2017    |
| repeat()              | rmethod returns a string with a number of copies of a string (Immutable - ES6)                                                              |
| replace()             | method replaces a specified value with another value in a string, By default, the replace() method replaces only the first match            |
| replaceAll()          | method allows you to specify a regular expression instead of a string to be replaced                                                        |
| split()               | A string can be converted to an array with the split() method                                                                               |
| length                | returns the length of a string                                                                                                              |
| length                | returns the length of a string                                                                                                              |

**Examples:**

```javascript
let text = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
let length = text.length;
console.log(length) // 26

let text = "HELLO WORLD";
let char = text.charAt(0);
console.log(char) // H

let text = "HELLO WORLD";
let char = text.charCodeAt(0);
console.log(char) // 72

const name = "W3Schools";
let letter = name.at(2);
console.log(letter) // S

const name = "W3Schools";
let letter = name[2];
console.log(letter) // S

let text = "HELLO WORLD";
text[0] = "A";    // Gives no error, but does not work
console.log(text) // HELLO WORLD

let text = "Apple, Banana, Kiwi";
let part = text.slice(7, 13);
console.log(part) // Banana

let text = "Apple, Banana, Kiwi";
let part = text.slice(7);
console.log(part) // Banana, Kiwi

let text = "Apple, Banana, Kiwi";
let part = text.slice(-12);
console.log(part) // Banana, Kiwi

let text = "Apple, Banana, Kiwi";
let part = text.slice(-12, -6);
console.log(part) // Banana

let str = "Apple, Banana, Kiwi";
let part = str.substring(7, 13);
console.log(part) // Banana

let str = "Apple, Banana, Kiwi";
let part = str.substr(7, 6);
console.log(part) // Banana

let str = "Apple, Banana, Kiwi";
let part = str.substr(7);
console.log(part) // Banana, Kiwi

let str = "Apple, Banana, Kiwi";
let part = str.substr(-4);
console.log(part) // Kiwi

let text1 = "Hello World!";
let text2 = text1.toUpperCase();
console.log(text2) // HELLO WORLD!

let text1 = "Hello World!";       // String
let text2 = text1.toLowerCase();  // text2 is text1 converted to lower
console.log(text2) // hello world!

let text1 = "Hello";
let text2 = "World";
let text3 = text1.concat(" ", text2);
console.log(text3) // Hello World

text = "Hello" + " " + "World!";
text = "Hello".concat(" ", "World!");
console.log(text) // Hello World!

let text1 = "      Hello World!      ";
let text2 = text1.trim();
console.log(text2, text2.length) // Hello World! 12

let text1 = "     Hello World!     ";
let text2 = text1.trimStart();
console.log(text2, text2.length) // Hello World!      17

let text = "5";
let padded = text.padStart(4,"0");
console.log(padded) // 0005

let text = "5";
let padded = text.padStart(4,"x");
console.log(padded) // xxx5

let numb = 5;
let text = numb.toString();
let padded = text.padStart(4,"0");
console.log(padded) // 0005

let text = "5";
let padded = text.padEnd(4,"0");
console.log(padded) // 5000

let text = "5";
let padded = text.padEnd(4,"x");
console.log(padded) // 5xxx

let numb = 5;
let text = numb.toString();
let padded = text.padEnd(4,"0");
console.log(padded) // 5000

let text = "Hello world!";
let result = text.repeat(2);
console.log(result) // Hello world!Hello world!

let text = "Hello world!";
let result = text.repeat(4);
console.log(result) // Hello world!Hello world!Hello world!Hello world!

let text = "Please visit Microsoft!";
let newText = text.replace("Microsoft", "W3Schools");
console.log(newText) // Please visit W3Schools!

let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace("Microsoft", "W3Schools");
console.log(newText) // Please visit W3Schools and Microsoft!

let text = "Please visit Microsoft!";
let newText = text.replace("MICROSOFT", "W3Schools");
console.log(newText) // Please visit Microsoft!

let text = "Please visit Microsoft!";
let newText = text.replace(/MICROSOFT/i, "W3Schools");
console.log(newText) // Please visit W3Schools!

let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace(/Microsoft/g, "W3Schools");
console.log(newText) // Please visit W3Schools and W3Schools!

let text = "I love cats. Cats are very easy to love. Cats are very popular."
text = text.replaceAll("Cats","Dogs");
text = text.replaceAll("cats","dogs");
console.log(text) // I love dogs. Dogs are very easy to love. Dogs are very popular.

let text = "I love cats. Cats are very easy to love. Cats are very popular";
text = text.replaceAll(/Cats/g,"Dogs");
text = text.replaceAll(/cats/g,"dogs");
console.log(text) // I love dogs. Dogs are very easy to love. Dogs are very popular

let text = "a,b,c,d,e,f";
const myArray = text.split(",");
console.log(myArray) // [ 'a', 'b', 'c', 'd', 'e', 'f' ]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>String Search Methods</h2>


| String Search Methods | Description                                                                                                               |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| indexOf()             | returns the index (position) of the first occurrence of a string in a string, or it returns -1 if the string is not found |
| lastIndexOf()         | returns the index of the last occurrence of a specified text in a string                                                  |
| search()              | searches a string for a string (or a regular expression) and returns the position of the match                            |
| match()               | returns an array containing the results of matching a string against a string (or a regular expression)                   |
| matchAll()            | returns an iterator containing the results of matching a string against a string (or a regular expression)                |
| includes()            | returns true if a string contains a specified value. Otherwise it returns false                                           |
| startsWith()          | returns true if a string begins with a specified value                                                                    |
| endsWith()            | method returns true if a string ends with a specified value, Otherwise it returns false                                   |
| search()              | searches a string for a string (or a regular expression) and returns the position of the match                            |
| search()              | searches a string for a string (or a regular expression) and returns the position of the match                            |

**Examples:**

```javascript
let text = "Please locate where 'locate' occurs!";
let index = text.indexOf("locate");
console.log(index) // 7

let text = "Please locate where 'locate' occurs!";
let index = text.lastIndexOf("locate");
console.log(index) // 21

let text = "Please locate where 'locate' occurs!";
let index = text.lastIndexOf("John");
console.log(index) // -1

let text = "Please locate where 'locate' occurs!";
let index = text.indexOf("locate", 15);
console.log(index) // 21

let text = "Please locate where 'locate' occurs!";
let res = text.lastIndexOf("locate", 15); // methods searches backwards (from the end to the beginning), meaning: if the second parameter is 15, the search starts at position 15, and searches to the beginning of the string.
console.log(res) // 7

let text = "Please locate where 'locate' occurs!";
let res = text.search("locate");
console.log(res) // 7

let text = "Please locate where 'locate' occurs!";
let res = text.search(/locate/);
console.log(res) // 7

let text = "The rain in SPAIN stays mainly in the plain";
let res = text.match("ain");
console.log(res) // ['ain', index: 5, input: 'The rain in SPAIN stays mainly in the plain', groups: undefined]

let text = "The rain in SPAIN stays mainly in the plain";
let res = text.match(/ain/);
console.log(res) // ['ain', index: 5, input: 'The rain in SPAIN stays mainly in the plain', groups: undefined]

let text = "The rain in SPAIN stays mainly in the plain";
let res = text.match(/ain/g);
console.log(res) // [ 'ain', 'ain', 'ain' ]

let text = "The rain in SPAIN stays mainly in the plain";
let res = text.match(/ain/gi);
console.log(res) // [ 'ain', 'AIN', 'ain', 'ain' ]

let text = "I love cats. Cats are very easy to love. Cats are very popular."
const iterator = text.matchAll("Cats");
console.log(iterator) // Cats,Cats

let text = "I love cats. Cats are very easy to love. Cats are very popular."
const iterator = text.matchAll(/Cats/g);
console.log(iterator) // Cats,Cats

let text = "I love cats. Cats are very easy to love. Cats are very popular."
const iterator = text.matchAll(/Cats/gi);
console.log(iterator) // cats,Cats,Cats

let text = "Hello world, welcome to the universe.";
let res = text.includes("world");
console.log(res) // true

let text = "Hello world, welcome to the universe.";
let res = text.includes("world", 12);
console.log(res) // false

let text = "Hello world, welcome to the universe.";
let res = text.startsWith("Hello");
console.log(res) // true

let text = "Hello world, welcome to the universe.";
let res = text.startsWith("world")
console.log(res) // false

let text = "Hello world, welcome to the universe.";
let res = text.startsWith("world", 5)
console.log(res) // false

let text = "Hello world, welcome to the universe.";
let res = text.startsWith("world", 6)
console.log(res) // true

let text = "John Doe";
let res = text.endsWith("Doe");
console.log(res) // true

let text = "Hello world, welcome to the universe.";
let res = text.endsWith("world", 11); // Check if the 11 first characters of a string ends with "world":
console.log(res) // res
```

**[⬆ Back to Top](#table-of-contents)**


### <h2>Template Strings</h2>

**Template Strings** use back-ticks (``) rather than the quotes ("") to define a string:

**Examples**

```javascript
let text = `Hello World!`;
console.log(text) // Hello World!

let text = `He's often called "Johnny"`;
console.log(text) // He's often called "Johnny"

let text =
`The quick
brown fox
jumps over
the lazy dog`;
console.log(text)

// OutPut

The quick
brown fox
jumps over
the lazy dog

let firstName = "John";
let lastName = "Doe";
let text = `Welcome ${firstName}, ${lastName}!`;
console.log(text) // Welcome John, Doe!

let price = 10;
let VAT = 0.25;
let total = `Total: ${(price * (1 + VAT)).toFixed(2)}`;
console.log(total) // Total: 12.50
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Interview Questions and Answers</h2>

| Questions                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------- |
| [How to remove all line breaks from a string?](#How-to-remove-all-line-breaks-from-a-string?)                                     |
| [2. How do you trim a string at the beginning or ending?](#2.-How-do-you-trim-a-string-at-the-beginning-or-ending?)                     |
| [3. How do you create specific number of copies of a string?](#3.-How-do-you-create-specific-number-of-copies-of-a-string?)             |
| [4. What is the output of below string expression?](#4.-What-is-the-output-of-below-string-expression?)                                 |
| [5. How do you write multi-line strings in template literals?](#5.-How-do-you-write-multi-line-strings-in-template-literals?)           |
| [6. How to convert string to title case with javascript?](#6.-How-to-convert-string-to-title-case-with-javascript?)                     |
| [7. How do you define multiline strings?](#7.-How-do-you-define-multiline-strings?)                                                     |
| [8. How do you trim a string in javascript?](#8.-How-do-you-trim-a-string-in-javascript?)                                               |
| [9. How do you check if a string starts with another string?](#9.-How-do-you-check-if-a-string-starts-with-another-string?)             |
| [10. How do you convert the first letter of a string to uppercase?](#10.-How-do-you-convert-the-first-letter-of-a-string-to-uppercase?) |
| [11. How do you check whether a string contains a substring?](#11.-How-do-you-check-whether-a-string-contains-a-substring?)             |
| [12. What are raw strings?](#12.-What-are-raw-strings?)                                                                                 |
| [13. What are template literals?](#13.-What-are-template-literals?)                                                                     |
| [14. What are enhanced object literals?](#14.-What-are-enhanced-object-literals?)                                                       |

### <h3>How to remove all line breaks from a string?</h3>

**Ans:** The easiest approach is using regular expressions to detect and replace newlines in the string. In this case, we use replace function along with string to replace with, which in our case is an empty string.

```javascript
function remove_linebreaks( var message ) {
    return message.replace( /[\r\n]+/gm, "" );
}
```

In the above expression, g and m are for global and multiline flags.

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>2. How do you trim a string at the beginning or ending?</h3>

**Ans:** The `trim` method of string prototype is used to trim on both sides of a string. But if you want to trim especially at the beginning or ending of the string then you can use `trimStart/trimLeft` and `trimEnd/trimRight` methods. Let's see an example of these methods on a greeting message,

```javascript
var greeting = "   Hello, Goodmorning!   ";

console.log(greeting); // "   Hello, Goodmorning!   "
console.log(greeting.trimStart()); // "Hello, Goodmorning!   "
console.log(greeting.trimLeft()); // "Hello, Goodmorning!   "

console.log(greeting.trimEnd()); // "   Hello, Goodmorning!"
console.log(greeting.trimRight()); // "   Hello, Goodmorning!"
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>3. How do you create specific number of copies of a string?</h3>

**Ans:** The `repeat()` method is used to construct and return a new string which contains the specified number of copies of the string on which it was called, concatenated together. Remember that this method has been added to the ECMAScript 2015 specification.
Let's take an example of Hello string to repeat it 4 times,

```javascript
"Hello".repeat(4); // 'HelloHelloHelloHello'
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>4. What is the output of below string expression?</h3>

```javascript
console.log("Welcome to JS world"[0]);
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

**Ans:** The output of the above expression is "W".

**Explanation:** The bracket notation with specific index on a string returns the character at a specific location. Hence, it returns the character "W" of the string. Since this is not supported in IE7 and below versions, you may need to use the .charAt() method to get the desired result.

### <h3>5. How do you write multi-line strings in template literals?</h3>

**Ans:** In ES5, you would have to use newline escape characters('\\n') and concatenation symbols(+) in order to get multi-line strings.

```javascript
console.log("This is string sentence 1\n" + "This is string sentence 2");
```

Whereas in ES6, You don't need to mention any newline sequence character,

```javascript
console.log(`This is string sentence
'This is string sentence 2`);
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>6. How to convert string to title case with javascript?</h3>

**Ans:**  Title case means that the first letter of each word is capitalized. You can convert a string to title case using the below function,

```javascript
function toTitleCase(str) {
return str.replace(/\w\S*/g, function (txt) {
    return txt.charAt(0).toUpperCase() + txt.substring(1).toLowerCase();
});
}
toTitleCase("good morning john"); // Good Morning John
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>7. How do you define multiline strings?</h3>

**Ans:** You can define multiline string literals using the '\\' character followed by line terminator.

```javascript
var str =
"This is a \
very lengthy \
sentence!";
```

But if you have a space after the '\\' character, the code will look exactly the same, but it will raise a SyntaxError.

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>8. How do you trim a string in javascript?</h3>

**Ans:** JavaScript provided a trim method on string types to trim any whitespaces present at the beginning or ending of the string.

```javascript
"  Hello World   ".trim(); //Hello World
```

If your browser(<IE9) doesn't support this method then you can use below polyfill.

```javascript
if (!String.prototype.trim) {
(function () {
    // Make sure we trim BOM and NBSP
    var rtrim = /^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g;
    String.prototype.trim = function () {
    return this.replace(rtrim, "");
    };
})();
}
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>9. How do you check if a string starts with another string?</h3>

**Ans:** You can use ECMAScript 6's `String.prototype.startsWith()` method to check if a string starts with another string or not. But it is not yet supported in all browsers. Let's see an example to see this usage,

```javascript
"Good morning".startsWith("Good"); // true
"Good morning".startsWith("morning"); // false
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>10. How do you convert the first letter of a string to uppercase?</h3>

**Ans:**

```javascript
const str = "name";
const modStr = str[0].toUpperCase() + str.slice(1);
console.log(str); // name
console.log(modStr); // Name
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>11. How do you check whether a string contains a substring?</h3>

**Ans:** There are 3 possible ways to check whether a string contains a substring or not,

1. **Using includes:** ES6 provided `String.prototype.includes` method to test a string contains a substring

```javascript
var mainString = "hello",
subString = "hell";
mainString.includes(subString);
```

2. **Using indexOf:** In an ES5 or older environment, you can use `String.prototype.indexOf` which returns the index of a substring. If the index value is not equal to -1 then it means the substring exists in the main string.

```javascript
var mainString = "hello",
subString = "hell";
mainString.indexOf(subString) !== -1;
```

3. **Using RegEx:** The advanced solution is using Regular expression's test method(`RegExp.test`), which allows for testing for against regular expressions

```javascript
var mainString = "hello",
regex = /hell/;
regex.test(mainString);
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>12. What are raw strings?</h3>

**Ans:** ES6 provides a raw strings feature using the `String.raw()` method which is used to get the raw string form of template strings. This feature allows you to access the raw strings as they were entered, without processing escape sequences. For example, the usage would be as below,

```javascript
var calculationString = String.raw`The sum of numbers is \n${
1 + 2 + 3 + 4
}!`;
console.log(calculationString); // The sum of numbers is \n10!
```

If you don't use raw strings, the newline character sequence will be processed by displaying the output in multiple lines

```javascript
var calculationString = `The sum of numbers is \n${1 + 2 + 3 + 4}!`;
console.log(calculationString);
// The sum of numbers is
// 10!
```

Also, the raw property is available on the first argument to the tag function

```javascript
function tag(strings) {
console.log(strings.raw[0]);
}
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>13. What are template literals?</h3>

**Ans:** Template literals or template strings are string literals allowing embedded expressions. These are enclosed by the back-tick (`) character instead of double or single quotes.
In ES6, this feature enables using dynamic expressions as below,

```javascript
var greeting = `Welcome to JS World, Mr. ${firstName} ${lastName}.`;
```

In ES5, you need break string like below,

```javascript
var greeting = 'Welcome to JS World, Mr. ' + firstName + ' ' + lastName.`
```

**Note:** You can use multi-line strings and string interpolation features with template literals.

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

### <h3>14. What are enhanced object literals?</h3>

Ans: Object literals make it easy to quickly create objects with properties inside the curly braces. For example, it provides shorter syntax for common object property definition as below.

```javascript
//ES6
var x = 10,
y = 20;
obj = { x, y };
console.log(obj); // {x: 10, y:20}
//ES5
var x = 10,
y = 20;
obj = { x: x, y: y };
console.log(obj); // {x: 10, y:20}
```

**[⬆ Back to Interview Questions and Answers](#Interview-Questions-and-Answers)**

**[⬆ Back to Top](#table-of-contents)**


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>