### Table of Contents

| No. | Questions                                                                                                                                                 |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 49  | [What is a Regular Expression](#What-is-a-Regular-Expression)                                                                                             |
| 50  | [What are the string methods available in Regular expression](#What-are-the-string-methods-available-in-Regular-expression)                               |
| 51  | [What are modifiers in regular expression](#What-are-modifiers-in-regular-expression)                                                                     |
| 52  | [What are regular expression patterns](#What-are-regular-expression-patterns)                                                                             |
| 53  | [What is a RegExp object](#What-is-a-RegExp-object)                                                                                                       |
| 54  | [How do you search a string for a pattern](#How-do-you-search-a-string-for-a-pattern)                                                                     |
| 55  | [What is the purpose of exec method](#What-is-the-purpose-of-exec-method)                                                                                 |
| 56  | [How do you return all matching strings against a regular expression](#How-do-you-return-all-matching-strings-against-a-regular-expression)               |

### <h2>What is a Regular Expression</h2>

A regular expression is a sequence of characters that forms a search pattern. You can use this search pattern for searching data in a text. These can be used to perform all types of text search and text replace operations. Let's see the syntax format now,

```javascript
/pattern/modifiers;
```

For example, the regular expression or search pattern with case-insensitive username would be,

```javascript
/John/i;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the string methods available in Regular expression</h2>

Regular Expressions has two string methods: search() and replace().
The search() method uses an expression to search for a match, and returns the position of the match.

```javascript
var msg = "Hello John";
var n = msg.search(/John/i); // 6
```

The replace() method is used to return a modified string where the pattern is replaced.

```javascript
var msg = "Hello John";
var n = msg.replace(/John/i, "Buttler"); // Hello Buttler
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are modifiers in regular expression</h2>

Modifiers can be used to perform case-insensitive and global searches. Let's list down some of the modifiers,

| Modifier | Description                                             |
| -------- | ------------------------------------------------------- |
| i        | Perform case-insensitive matching                       |
| g        | Perform a global match rather than stops at first match |
| m        | Perform multiline matching                              |

Let's take an example of global modifier,

```javascript
var text = "Learn JS one by one";
var pattern = /one/g;
var result = text.match(pattern); // one,one
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are regular expression patterns</h2>

Regular Expressions provide a group of patterns in order to match characters. Basically they are categorized into 3 types,

1. **Brackets:** These are used to find a range of characters. </br>
  For example, below are some use cases, </br>
  1. [abc]: Used to find any of the characters between the brackets(a,b,c) </br>
  2. [0-9]: Used to find any of the digits between the brackets </br>
  3. (a|b): Used to find any of the alternatives separated with | </br>
1. **Metacharacters:** These are characters with a special meaning </br>
  For example, below are some use cases, </br>
  1. \\d: Used to find a digit </br>
  2. \\s: Used to find a whitespace character </br>
  3. \\b: Used to find a match at the beginning or ending of a word </br>
1. **Quantifiers:** These are useful to define quantities </br>
  For example, below are some use cases, </br>
  1. n+: Used to find matches for any string that contains at least one n </br>
  2. n\*: Used to find matches for any string that contains zero or more occurrences of n </br>
  3. n?: Used to find matches for any string that contains zero or one occurrences of n </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a RegExp object</h2>

RegExp object is a regular expression object with predefined properties and methods. Let's see the simple usage of RegExp object,

```javascript
var regexp = new RegExp("\\w+");
console.log(regexp);
// expected output: /\w+/
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you search a string for a pattern</h2>

You can use the test() method of regular expression in order to search a string for a pattern, and return true or false depending on the result.

```javascript
var pattern = /you/;
console.log(pattern.test("How are you?")); //true
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of exec method</h2>

The purpose of exec method is similar to test method but it executes a search for a match in a specified string and returns a result array, or null instead of returning true/false.

```javascript
var pattern = /you/;
console.log(pattern.exec("How are you?")); //["you", index: 8, input: "How are you?", groups: undefined]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you return all matching strings against a regular expression</h2>

The `matchAll()` method can be used to return an iterator of all results matching a string against a regular expression. For example, the below example returns an array of matching string results against a regular expression,

```javascript
let regexp = /Hello(\d?))/g;
let greeting = "Hello1Hello2Hello3";

let greetingList = [...greeting.matchAll(regexp)];

console.log(greetingList[0]); //Hello1
console.log(greetingList[1]); //Hello2
console.log(greetingList[2]); //Hello3
```

**[⬆ Back to Top](#table-of-contents)**