<h1>JavaScript Regular Expressions</h1>

A regular expression is a sequence of characters that forms a search pattern. </br>
When you search for data in a text, you can use this search pattern to describe what you are searching for. </br>
A regular expression can be a single character, or a more complicated pattern. </br>
Regular expressions can be used to perform all types of text search and text replace operations. </br>

**Syntax:** `/pattern/modifiers;` ex - `/w3schools/i;`

where - /w3schools/i  is a regular expression, w3schools  is a pattern (to be used in a search), and i  is a modifier (modifies the search to be case-insensitive).

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

<h2>Regular Expression Modifiers</h2>

**Modifiers can be used to perform case-insensitive more global searches:**

| Modifier | Description                                    |
| -------- | ---------------------------------------------- |
| i        | Perform case-insensitive matching              |
| g        | Perform a global match (find all)              |
| m        | Perform multiline matching                     |
| d        | Perform start and end matching (New in ES2022) |

<h2>Regular Expression Patterns</h2>

**Brackets are used to find a range of characters:**

| Expression | Description                                        |
| ---------- | -------------------------------------------------- |
| [abc]      | Find any of the characters between the brackets    |
| [0-9]      | Find any of the digits between the brackets        |
| (x&#124;y) | Find any of the alternatives separated with &#124; |

**Metacharacters are characters with a special meaning:**

| Metacharacter | Description                                                                                          |
| ------------- | ---------------------------------------------------------------------------------------------------- |
| \d            | Find a digit                                                                                         |
| \s            | Find a whitespace character                                                                          |
| \b            | Find a match at the beginning of a word like this: \bWORD, or at the end of a word like this: WORD\b |
| \uxxxx        | Find the Unicode character specified by the hexadecimal number xxxx                                  |

**Quantifiers define quantities:**

| Metacharacter | Description                                                    |
| ------------- | -------------------------------------------------------------- |
| n+            | Matches any string that contains at least one n                |
| n*            | Matches any string that contains zero or more occurrences of n |
| n?            | Matches any string that contains zero or one occurrences of n  |

<h2>What is RegExp Object</h2>

RegExp object is a regular expression object with predefined properties and methods

**test():** It searches a string for a pattern, and returns true or false, depending on the result.

**exec():** It searches a string for a specified pattern, and returns the found text as an object, If no match is found, it returns an empty (null) object.



<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>