<h1>String</h1>

Strings are written with quotes. You can use single or double quotes:

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

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>