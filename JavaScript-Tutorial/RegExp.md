<h1>JavaScript Regular Expressions</h1>

A regular expression is a sequence of characters that forms a search pattern. </br>
When you search for data in a text, you can use this search pattern to describe what you are searching for. </br>
A regular expression can be a single character, or a more complicated pattern. </br>
Regular expressions can be used to perform all types of text search and text replace operations. </br>

**Syntax:** `/pattern/modifiers;` ex - `/w3schools/i;`

where - /w3schools/i  is a regular expression, w3schools  is a pattern (to be used in a search), and i  is a modifier (modifies the search to be case-insensitive).

```javascript
new RegExp("regexp", "i")

or simply:

/regexp/i
```

<h2>What is RegExp Object</h2>

RegExp object is a regular expression object with predefined properties and methods

**test():** It searches a string for a pattern, and returns true or false, depending on the result.

**exec():** It searches a string for a specified pattern, and returns the found text as an object, If no match is found, it returns an empty (null) object.

**Examples:**

```javascript
let text = "Visit W3Schools";
let pattern = /w3schools/i;
console.log(pattern.test(text)) // true

let text = "Visit W3Schools";
let pattern = new RegExp(/w3schools/, "i")
console.log(pattern.test(text)) // true
```

<h2>search() with a String() and Regular Expression</h2>

```javascript
let text = "Visit W3Schools!";
text.search("W3Schools"); // 6

let text = "Visit W3Schools"; // Use a regular expression to do a case-insensitive search for "w3schools" in a string
text.search(/w3schools/i); // 6
```

<h2>replace() with a String() and Regular Expression</h2>

```javascript
let text = "Visit Microsoft!, Microsoft";
let result = text.replace("Microsoft", "W3Schools");
console.log(result) // Visit W3Schools!, Microsoft

let text = "Visit Microsoft!, Microsoft";
let result = text.replace(/microsoft/i, "W3Schools"); // Use a case insensitive regular expression to replace Microsoft with W3Schools in a string
console.log(result) // Visit W3Schools!, Microsoft
```

<h2>Regular Expression Patterns</h2>

**Modifiers can be used to perform case-insensitive more global searches:**

| Modifier | Description                                    |
| -------- | ---------------------------------------------- |
| i        | Perform case-insensitive matching              |
| g        | Perform a global match (find all)              |
| m        | Perform multiline matching                     |
| d        | Perform start and end matching (New in ES2022) |

**Brackets are used to find a Range (Group) of characters:**

| Expression | Description                                        |
| ---------- | -------------------------------------------------- |
| [abc]      | Find any of the characters between the brackets    |
| [0-9]      | Find any of the digits between the brackets        |
| [A-Z]      | Any character from uppercase A to uppercase Z      |
| [a-z]      | Any character from lowercase a to lowercase z      |
| [A-z]      | Any character from uppercase A to lowercase z      |
| (x&#124;y) | Find any of the alternatives separated with &#124; |

**Metacharacters are characters with a special meaning:**

| Metacharacter | Description                                                                                          |
| ------------- | ---------------------------------------------------------------------------------------------------- |
| .             | Find a single character, except newline or line terminator                                           |
| \d            | Find a digit                                                                                         |
| \D            | Find a non-digit character                                                                           |
| \s            | Find a whitespace character                                                                          |
| \S            | Find a non-whitespace character                                                                      |
| \b            | Find a match at the beginning of a word like this: \bWORD, or at the end of a word like this: WORD\b |
| \B            | Find a match, but not at the beginning/end of a word                                                 |
| \w            | Find a word character                                                                                |
| \W            | Find a non-word character                                                                            |
| \0            | Find a NULL character                                                                                |
| \n            | Find a new line character                                                                            |
| \f            | Find a form feed character                                                                           |
| \r            | Find a carriage return character                                                                     |
| \t            | Find a tab character                                                                                 |
| \v            | Find a vertical tab character                                                                        |
| \xxx          | Find the character specified by an octal number xxx                                                  |
| \xdd          | Find the character specified by a hexadecimal number dd                                              |
| \uxxxx        | Find the Unicode character specified by the hexadecimal number xxxx                                  |

**Quantifiers define quantities:**

| Quantifier | Description                                                    |
| ---------- | -------------------------------------------------------------- |
| n+         | Matches any string that contains at least one n                |
| n*         | Matches any string that contains zero or more occurrences of n |
| n?         | Matches any string that contains zero or one occurrences of n  |
| n{X}       | Matches any string that contains a sequence of X n's           |
| n{X,Y}     | Matches any string that contains a sequence of X to Y n's      |
| n{X,}      | Matches any string that contains a sequence of at least X n's  |
| ^n         | Matches any string with n at the beginning of it               |
| ?=n        | Matches any string that is followed by a specific string n     |
| n?         | Matches any string that contains zero or one occurrences of n  |
| ?!n        | Matches any string that is not followed by a specific string n |

```javascript
// <------------------  Regular Expression Modifiers   -------------------->
let text = "Visit W3Schools";
let pattern = /w3schools/i;
console.log(pattern.test(text)) // true

let text = "Visit W3Schools";
let pattern = new RegExp(/w3schools/, "i")
console.log(pattern.test(text)) // true

let text = "Is this all there is?";
let pattern = /is/i;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) //  [ 'Is', index: 0, input: 'Is this all there is?', groups: undefined ]
console.log(text.match(pattern)) // [ 'Is', index: 0, input: 'Is this all there is?', groups: undefined ]

let text = "Is this all there is?";
let pattern = /is/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'is', index: 18, input: 'Is this all there is?', groups: undefined ]
console.log(text.match(pattern)) // [ 'is', 'is' ]

let text = "Is this all there is?";
let pattern = /is/ig;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'is', index: 5, input: 'Is this all there is?', groups: undefined ]
console.log(text.match(pattern)) // [ 'Is', 'is', 'is' ]

let text = "aaaabb";
let pattern = /(aa)(bb)/d;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'aabb', 'aa', 'bb', index: 2, input: 'aaaabb', groups: undefined, indices: [ [ 2, 6 ], [ 2, 4 ], [ 4, 6 ], groups: undefined ] ]
console.log(text.match(pattern)) // [ 'aabb', 'aa', 'bb', index: 2, input: 'aaaabb', groups: undefined, indices: [ [ 2, 6 ], [ 2, 4 ], [ 4, 6 ], groups: undefined ] ]

let text = `Is this
all there
is`;
let pattern = /^is/gm;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // null
console.log(text.match(pattern)) // [ 'is' ]

let text = `Is this
all there
is`;
let pattern = /^is/gmi;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'is', index: 18, input: 'Is this\nall there\nis', groups: undefined ]
console.log(text.match(pattern)) // [ 'Is', 'is' ]

// <------------------  Regular Expression Range (Group)   -------------------->

let text = "Is this all there is?";
let pattern = /[h]/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'h', index: 13, input: 'Is this all there is?', groups: undefined ]
console.log(text.match(pattern)) // [ 'h', 'h' ]

let text = "Do you know if this is all there is?";
let pattern = /[is]/gi;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'i', index: 17, input: 'Do you know if this is all there is?', groups: undefined ]
console.log(text.match(pattern)) // ['i', 'i', 's', 'i', 's', 'i', 's']

let text = "I SCREAM FOR ICE CREAM!";
let pattern = /[A-E]/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'E', index: 5, input: 'I SCREAM FOR ICE CREAM!', groups: undefined ]
console.log(text.match(pattern)) // [ 'C', 'E', 'A', 'C', 'E', 'C', 'E', 'A' ]

// Use the [^abc] expression to find any character NOT between the brackets.

let text = "Is this all there is?";
let pattern = /[^h]/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) //[ 's', index: 1, input: 'Is this all there is?', groups: undefined ]
console.log(text.match(pattern)) //[ 'I', 's', ' ', 't', 'i', 's', ' ', 'a', 'l', 'l', ' ', 't', 'e', 'r', 'e', ' ', 'i', 's', '?' ]

let text = "Do you know if this is all there is?";
let pattern = /[^is]/gi; // Do a global search for characters that are NOT "i" and "s" in a string
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'o', index: 1, input: 'Do you know if this is all there is?', groups: undefined ]
console.log(text.match(pattern)) // [ 'D', 'o', ' ', 'y', 'o', 'u', ' ', 'k', 'n', 'o', 'w', ' ', 'f', ' ', 't', 'h', ' ', ' ', 'a', 'l', 'l', ' ', 't', 'h', 'e', 'r', 'e', ' ', '?' ]

let text = "123456789";
let pattern = /[1-4]/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ '2', index: 1, input: '123456789', groups: undefined ]
console.log(text.match(pattern)) // [ '1', '2', '3', '4' ]

let text = "123456789";
let pattern = /[^1-4]/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ '6', index: 5, input: '123456789', groups: undefined ]
console.log(text.match(pattern)) // [ '5', '6', '7', '8', '9' ]

let text = "re, green, red, green, gren, gr, blue, yellow";
let pattern= /(red|green)/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'red', 'red', index: 11, input: 're, green, red, green, gren, gr, blue, yellow', groups: undefined ]
console.log(text.match(pattern)) // [ 'green', 'red', 'green' ]

// <------------------  Regular Expression Metacharacters   -------------------->

let text = "Give 100%!";
let pattern = /\w/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'i', index: 1, input: 'Give 100%!', groups: undefined ]
console.log(text.match(pattern)) // [ 'G', 'i', 'v', 'e', '1', '0', '0' ]

// <------------------  Regular Expression Quantifier   -------------------->

let text = "Hellooo World! Hello W3Schools!";
let pattern = /o+/g;
console.log(pattern.test(text)); // true
console.log(pattern.exec(text)) // [ 'o', index: 9, input: 'Hellooo World! Hello W3Schools!', groups: undefined ]
console.log(text.match(pattern)) // [ 'ooo', 'o', 'o', 'oo' ]

```



<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
