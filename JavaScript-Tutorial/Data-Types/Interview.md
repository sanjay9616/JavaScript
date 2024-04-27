### Table of Contents

| No. | Questions                                                                                                                                                 |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 40  | [What is a WeakSet](#What-is-a-WeakSet)                                                                                                                   |
| 41  | [What are the differences between a WeakSet and a Set](#What-are-the-differences-between-a-WeakSet-and-a-Set)                                             |
| 42  | [List down the collection of methods available on WeakSet](#List-down-the-collection-of-methods-available-on-WeakSet)                                     |
| 43  | [How do you display the current date in javascript](#How-do-you-display-the-current-date-in-javascript)                                                   |
| 44  | [How do you compare two date objects](#How-do-you-compare-two-date-objects)                                                                               |
| 45  | [How do you convert date to another timezone in javascript](#How-do-you-convert-date-to-another-timezone-in-javascript)                                   |
| 46  | [How do you perform language specific date and time formatting](#How-do-you-perform-language-specific-date-and-time-formatting)                           |
| 47  | [How do get the timezone offset from date](#How-do-get-the-timezone-offset-from-date)                                                                     |
| 48  | [What is the shortcut to get timestamp](#What-is-the-shortcut-to-get-timestamp)                                                                           |
| 49  | [What is a Regular Expression](#What-is-a-Regular-Expression)                                                                                             |
| 50  | [What are the string methods available in Regular expression](#What-are-the-string-methods-available-in-Regular-expression)                               |
| 51  | [What are modifiers in regular expression](#What-are-modifiers-in-regular-expression)                                                                     |
| 52  | [What are regular expression patterns](#What-are-regular-expression-patterns)                                                                             |
| 53  | [What is a RegExp object](#What-is-a-RegExp-object)                                                                                                       |
| 54  | [How do you search a string for a pattern](#How-do-you-search-a-string-for-a-pattern)                                                                     |
| 55  | [What is the purpose of exec method](#What-is-the-purpose-of-exec-method)                                                                                 |
| 56  | [How do you return all matching strings against a regular expression](#How-do-you-return-all-matching-strings-against-a-regular-expression)               |


<h1>InterView Questions and Answers based on Set and Map</h1>

### <h2>What is a WeakSet</h2>

WeakSet is used to store a collection of weakly(weak references) held objects. The syntax would be as follows,

```javascript
new WeakSet([iterable]);
```

Let's see the below example to explain it's behavior,

```javascript
var ws = new WeakSet();
var user = {};
ws.add(user);
ws.has(user); // true
ws.delete(user); // removes user from the set
ws.has(user); // false, user has been removed
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between a WeakSet and a Set</h2>

The main difference is that references to objects in Set are strong while references to objects in WeakSet are weak. i.e, An object in WeakSet can be garbage collected if there is no other reference to it.
Other differences are,

1. Sets can store any value Whereas WeakSets can store only collections of objects </br>
2. WeakSet does not have size property unlike Set </br>
3. WeakSet does not have methods such as clear, keys, values, entries, forEach. </br>
4. WeakSet is not iterable. </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>List down the collection of methods available on WeakSet</h2>

Below are the list of methods available on WeakSet,

1. add(value): A new object is appended with the given value to the weakset </br>
2. delete(value): Deletes the value from the WeakSet collection. </br>
3. has(value): It returns true if the value is present in the WeakSet Collection, otherwise it returns false. </br>

Let's see the functionality of all the above methods in an example,

```javascript
var weakSetObject = new WeakSet();
var firstObject = {};
var secondObject = {};
// add(value)
weakSetObject.add(firstObject);
weakSetObject.add(secondObject);
console.log(weakSetObject.has(firstObject)); //true
weakSetObject.delete(secondObject);
```

**[⬆ Back to Top](#table-of-contents)**

<h1>InterView Questions and Answers based on Date</h1>

### <h2>How do you display the current date in javascript</h2>

You can use `new Date()` to generate a new Date object containing the current date and time. For example, let's display the current date in mm/dd/yyyy

```javascript
var today = new Date();
var dd = String(today.getDate()).padStart(2, "0");
var mm = String(today.getMonth() + 1).padStart(2, "0"); //January is 0!
var yyyy = today.getFullYear();

today = mm + "/" + dd + "/" + yyyy;
document.write(today); // 04/26/2024
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you compare two date objects</h2>

You need to use date.getTime() method to compare date values instead of comparison operators (==, !=, ===, and !== operators)

```javascript
var d1 = new Date();
var d2 = new Date(d1);
console.log(d1.getTime() === d2.getTime()); //True
console.log(d1 === d2); // False
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you convert date to another timezone in javascript</h2>

You can use the toLocaleString() method to convert dates in one timezone to another. For example, let's convert current date to British English timezone as below,

```javascript
console.log(event.toLocaleString("en-GB", { timeZone: "UTC" })); //29/06/2019, 09:56:00
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you perform language specific date and time formatting</h2>

You can use the `Intl.DateTimeFormat` object which is a constructor for objects that enable language-sensitive date and time formatting. Let's see this behavior with an example,

```javascript
var date = new Date(Date.UTC(2019, 07, 07, 3, 0, 0));
console.log(new Intl.DateTimeFormat("en-GB").format(date)); // 07/08/2019
console.log(new Intl.DateTimeFormat("en-AU").format(date)); // 07/08/2019
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do get the timezone offset from date</h2>

You can use the `getTimezoneOffset` method of the date object. This method returns the time zone difference, in minutes, from current locale (host system settings) to UTC

```javascript
var offset = new Date().getTimezoneOffset();
console.log(offset); // -480
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the shortcut to get timestamp</h2>

You can use `new Date().getTime()` to get the current timestamp. There is an alternative shortcut to get the value.

```javascript
console.log(+new Date()); // 1714138552088
console.log(Date.now()); // 1714138552094
```

**[⬆ Back to Top](#table-of-contents)**

<h1>InterView Questions and Answers based on RegExp</h1>

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



