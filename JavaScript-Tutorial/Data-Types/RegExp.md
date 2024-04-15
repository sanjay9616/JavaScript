<h1>JavaScript Regular Expressions</h1>

<h2>What Is a Regular Expression?</h2>

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

| Modifier | Description                                    |
| -------- | ---------------------------------------------- |
| i        | Perform case-insensitive matching              |
| g        | Perform a global match (find all)              |
| m        | Perform multiline matching                     |
| d        | Perform start and end matching (New in ES2022) |

<h2>Regular Expression Patterns</h2>

| Expression | Description                                        |
| ---------- | -------------------------------------------------- |
| [abc]      | Find any of the characters between the brackets    |
| [0-9]      | Find any of the digits between the brackets        |
| (x&#124;y) | Find any of the alternatives separated with &#124; |

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>