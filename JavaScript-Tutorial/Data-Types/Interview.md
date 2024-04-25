### Table of Contents

| No. | Questions                                                                                                                                     |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are the differences between primitives and non-primitives](#What-are-the-differences-between-primitives-and-non-primitives)             |
| 2   | [What are primitive data types](#What-are-primitive-data-types)                                                                               |
| 3   | [How do you detect primitive or non primitive value type](#How-do-you-detect-primitive-or-non-primitive-value-type)                           |
| 4   | [What is JSON](#What-is-JSON)                                                                                                                 |
| 5   | [What is JSON and its common operations](#What-is-JSON-and-its-common-operations)                                                             |
| 6   | [What are the syntax rules of JSON](#What-are-the-syntax-rules-of-JSON)                                                                       |
| 7   | [What is the purpose JSON stringify](#What-is-the-purpose-JSON-stringify)                                                                     |
| 8   | [How do you parse JSON string](#How-do-you-parse-JSON-string)                                                                                 |
| 9   | [Why do you need JSON](#Why-do-you-need-JSON)                                                                                                 |
| 10  | [How do you define JSON arrays](#How-do-you-define-JSON-arrays)                                                                               |
| 11  | [What is the purpose of the array slice method](#What-is-the-purpose-of-the-array-slice-method)                                               |
| 12  | [What is the purpose of the array splice method](#What-is-the-purpose-of-the-array-splice-method)                                             |
| 13  | [What is the difference between slice and splice](#What-is-the-difference-between-slice-and-splice)                                           |
| 14  | [What is the purpose of some method in arrays](#What-is-the-purpose-of-some-method-in-arrays)                                                 |
| 15  | [How do you map the array values without using map method](#How-do-you-map-the-array-values-without-using-map-method)                         |
| 16  | [What is the difference between dense and sparse arrays](#What-is-the-difference-between-dense-and-sparse-arrays)                             |
| 17  | [What are the different ways to create sparse arrays](#What-are-the-different-ways-to-create-sparse-arrays)                                   |
| 18  | [How do you reversing an array](#How-do-you-reversing-an-array)                                                                               |
| 19  | [How do you reverse an array without modifying original array](#How-do-you-reverse-an-array-without-modifying-original-array)                 |
| 20  | [How do you sort elements in an array](#How-do-you-sort-elements-in-an-array)                                                                 |
| 21  | [How do you find min and max value in an array](#How-do-you-find-min-and-max-value-in-an-array)                                               |
| 22  | [How do you find min and max values without Math functions](#How-do-you-find-min-and-max-values-without-Math-functions)                       |
| 23  | [How do you check whether an array includes a particular value or not](#How-do-you-check-whether-an-array-includes-a-particular-value-or-not) |
| 24  | [How do you compare scalar arrays](#How-do-you-compare-scalar-arrays)                                                                         |
| 25  | [What are typed arrays](#What-are-typed-arrays)                                                                                               |
| 26  | [What is ArrayBuffer](#What-is-ArrayBuffer)                                                                                                   |
| 27  | [What happens with negating an array](#What-happens-with-negating-an-array)                                                                   |
| 28  | [What happens if we add two arrays](#What-happens-if-we-add-two-arrays)                                                                       |
| 29  | [How do you remove falsy values from an array](#How-do-you-remove-falsy-values-from-an-array)                                                 |
| 30  | [How do you get unique values of an array](#How-do-you-get-unique-values-of-an-array)                                                         |
| 31  | [How do you combine two or more arrays](#How-do-you-combine-two-or-more-arrays)                                                               |
| 32  | [What is the easiest way to convert an array to an object](#What-is-the-easiest-way-to-convert-an-array-to-an-object)                         |
| 33  | [How do you create an array with some data](#How-do-you-create-an-array-with-some-data)                                                       |
| 34  | [How do you flattening multi dimensional arrays](#How-do-you-flattening-multi-dimensional-arrays)                                             |
| 35  | [How do you empty an array](#How-do-you-empty-an-array)                                                                                       |
| 36  | [What is the easiest way to resize an array](#What-is-the-easiest-way-to-resize-an-array)                                                     |
| 37  | [How to verify if a variable is an array](#How-to-verify-if-a-variable-is-an-array)                                                           |


<h1>InterView Questions and Answers on Basics data</h1>

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

<h1>InterView Questions and Answers based on Array</h1>

### <h2>What is the purpose of the array slice method</h2>

The **slice()** method returns the selected elements in an array as a new array object. It selects the elements starting at the given start argument, and ends at the given optional end argument without including the last element. If you omit the second argument then it selects till the end of the array.

Some of the examples of this method are,

```javascript
let arrayIntegers = [1, 2, 3, 4, 5];
let arrayIntegers1 = arrayIntegers.slice(0, 2); // returns [1,2]
let arrayIntegers2 = arrayIntegers.slice(2, 3); // returns [3]
let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
```

**Note:** Slice method doesn't mutate the original array but it returns the subset as a new array.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of the array splice method</h2>

The **splice()** method adds/removes items to/from an array, and then returns the removed item. The first argument specifies the array position/index for insertion or deletion whereas the optional second argument indicates the number of elements to be deleted. Each additional argument is added to the array.

**Syntax:**
```javascript
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, item2)
splice(start, deleteCount, item1, item2, /* …, */ itemN)
```

Some of the examples of this method are:

```javascript
let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

let arrayIntegers1 = arrayIntegersOriginal1.splice(0, 2); // returns [1, 2]; original array: [3, 4, 5]
let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
```

**Note:** Splice method modifies the original array and returns the deleted array.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between slice and splice</h2>

Some of the major differences in a tabular form:

| Slice                                        | Splice                                       |
| -------------------------------------------- | -------------------------------------------- |
| Doesn't modify the original array(immutable) | Modifies the original array(mutable)         |
| Returns the subset of original array         | Returns the deleted elements as array        |
| Used to pick the elements from array         | Used to insert/delete elements to/from array |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of some method in arrays</h2>

The some() method is used to test whether at least one element in the array passes the test implemented by the provided function. The method returns a boolean value. Let's take an example to test for any odd elements,

```javascript
var array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

var odd = (element) => element % 2 !== 0;

console.log(array.some(odd)); // true (the odd element exists)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you map the array values without using map method</h2>

You can map the array values without using the `map` method by just using the `from` method of Array. Let's map city names from Countries array,

```javascript
const countries = [
    { name: "India", capital: "Delhi" },
    { name: "US", capital: "Washington" },
    { name: "Russia", capital: "Moscow" },
    { name: "Singapore", capital: "Singapore" },
    { name: "China", capital: "Beijing" },
    { name: "France", capital: "Paris" },
];

const cityNames = Array.from(countries, ({ capital }) => capital);
console.log(cityNames); // ['Delhi, 'Washington', 'Moscow', 'Singapore', 'Beijing', 'Paris']
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between dense and sparse arrays</h2>

An array contains items at each index starting from first(0) to last(array.length - 1) is called as Dense array. Whereas if at least one item is missing (hole) at any index, the array is called as sparse.

Let's see the below two kind of arrays,

```js
const avengers = ["Ironman", "Hulk", "CaptainAmerica"];
console.log(avengers[0]); // 'Ironman'
console.log(avengers[1]); // 'Hulk'
console.log(avengers[2]); // 'CaptainAmerica'
console.log(avengers.length); // 3

const justiceLeague = ["Superman", "Aquaman", , "Batman"];
console.log(justiceLeague[0]); // 'Superman'
console.log(justiceLeague[1]); // 'Aquaman'
console.log(justiceLeague[2]); // undefined
console.log(justiceLeague[3]); // 'Batman'
console.log(justiceLeague.length); // 4
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the different ways to create sparse arrays</h2>

There are 4 different ways to create sparse arrays in JavaScript

1. **Array literal:** Omit a value when using the array literal
  ```javascript
  const justiceLeague = ["Superman", "Aquaman", , "Batman"];
  console.log(justiceLeague); // ['Superman', 'Aquaman', empty ,'Batman']
  ```
1. **Array() constructor:** Invoking Array(length) or new Array(length)
  ```javascript
  const array = Array(3);
  console.log(array); // [empty, empty ,empty]
  ```
1. **Delete operator:** Using delete array[index] operator on the array
  ```javascript
  const justiceLeague = ["Superman", "Aquaman", "Batman"];
  delete justiceLeague[1];
  console.log(justiceLeague); // ['Superman', empty, ,'Batman']
  ```
1. **Increase length property:** Increasing length property of an array
  ```javascript
  const justiceLeague = ["Superman", "Aquaman", "Batman"];
  justiceLeague.length = 5;
  console.log(justiceLeague); // ['Superman', 'Aquaman', 'Batman', empty, empty]
  ```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you reversing an array</h2>

You can use the reverse() method to reverse the elements in an array. This method is useful to sort an array in descending order. Let's see the usage of reverse() method in an example,

```javascript
let numbers = [1, 2, 5, 3, 4];
numbers.sort((a, b) => b - a);
numbers.reverse();
console.log(numbers); // [1, 2, 3, 4 ,5]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you reverse an array without modifying original array</h2>

The `reverse()` method reverses the order of the elements in an array but it mutates the original array. Let's take a simple example to demonistrate this case,

```javascript
const originalArray = [1, 2, 3, 4, 5];
const newArray = originalArray.reverse();

console.log(newArray); // [ 5, 4, 3, 2, 1]
console.log(originalArray); // [ 5, 4, 3, 2, 1]
```

There are few solutions that won't mutate the original array. Let's take a look.

1. **Using slice and reverse methods:**
In this case, just invoke the `slice()` method on the array to create a shallow copy followed by `reverse()` method call on the copy.

```javascript
const originalArray = [1, 2, 3, 4, 5];
const newArray = originalArray.slice().reverse(); //Slice an array gives a new copy

console.log(originalArray); // [1, 2, 3, 4, 5]
console.log(newArray); // [ 5, 4, 3, 2, 1]
```

2. **Using spread and reverse methods:**
In this case, let's use the spread syntax (...) to create a copy of the array followed by `reverse()` method call on the copy.

```javascript
const originalArray = [1, 2, 3, 4, 5];
const newArray = [...originalArray].reverse();

console.log(originalArray); // [1, 2, 3, 4, 5]
console.log(newArray); // [ 5, 4, 3, 2, 1]
```

3. **Using reduce and spread methods:**
Here execute a reducer function on an array elements and append the accumulated array on right side using spread syntax

```javascript
const originalArray = [1, 2, 3, 4, 5];
const newArray = originalArray.reduce((accumulator, value) => {
    return [value, ...accumulator];
}, []);

console.log(originalArray); // [1, 2, 3, 4, 5]
console.log(newArray); // [ 5, 4, 3, 2, 1]
```

4. **Using reduceRight and spread methods:**
Here execute a right reducer function(i.e. opposite direction of reduce method) on an array elements and append the accumulated array on left side using spread syntax

```javascript
const originalArray = [1, 2, 3, 4, 5];
const newArray = originalArray.reduceRight((accumulator, value) => {
    return [...accumulator, value];
}, []);

console.log(originalArray); // [1, 2, 3, 4, 5]
console.log(newArray); // [ 5, 4, 3, 2, 1]
```

5. **Using reduceRight and push methods:**
Here execute a right reducer function(i.e. opposite direction of reduce method) on an array elements and push the iterated value to the accumulator

```javascript
const originalArray = [1, 2, 3, 4, 5];
const newArray = originalArray.reduceRight((accumulator, value) => {
    accumulator.push(value);
    return accumulator;
}, []);

console.log(originalArray); // [1, 2, 3, 4, 5]
console.log(newArray); // [ 5, 4, 3, 2, 1]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you sort elements in an array</h2>

The sort() method is used to sort the elements of an array in place and returns the sorted array. The example usage would be as below,

```javascript
var months = ["Aug", "Sep", "Jan", "June"];
months.sort();
console.log(months); //  ["Aug", "Jan", "June", "Sep"]
```
```javascript
const points = [40, 100, 1, 5, 25, 10];
points.sort((a, b) => a - b)
console.log(points) // [ 1, 5, 10, 25, 40, 100 ]

const points = [40, 100, 1, 5, 25, 10];
points.sort((a, b) => a > b ? 1 : -1)
console.log(points) // [ 1, 5, 10, 25, 40, 100 ]

const points = [40, 100, 1, 5, 25, 10];
points.sort((a, b) => a > b ? -1 : 1)
console.log(points) // [ 100, 40, 25, 10, 5, 1 ]

const cars = [ { type: "Volvo", year: 2016 }, { type: "Saab", year: 2001 }, { type: "BMW", year: 2010 } ];
cars.sort((a, b) => a.year > b.year ? 1 : -1)
console.log(cars) // [ { type: 'Saab', year: 2001 }, { type: 'BMW', year: 2010 }, { type: 'Volvo', year: 2016 } ]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you find min and max value in an array</h2>

You can use `Math.min` and `Math.max` methods on array variables to find the minimum and maximum elements within an array. Let's create two functions to find the min and max value with in an array,

```javascript
var marks = [50, 20, 70, 60, 45, 30];
function findMin(arr) {
    return Math.min.apply(null, arr);
}
function findMax(arr) {
    return Math.max.apply(null, arr);
}

console.log(findMin(marks));
console.log(findMax(marks));
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you find min and max values without Math functions</h2>

You can write functions which loop through an array comparing each value with the lowest value or highest value to find the min and max values. Let's create those functions to find min and max values,

```javascript
var marks = [50, 20, 70, 60, 45, 30];
function findMin(arr) {
    var length = arr.length;
    var min = Infinity;
    while (length--) {
        if (arr[length] < min) {
        min = arr[length];
        }
    }
    return min;
}

function findMax(arr) {
    var length = arr.length;
    var max = -Infinity;
    while (length--) {
        if (arr[length] > max) {
        max = arr[length];
        }
    }
    return max;
}

console.log(findMin(marks));
console.log(findMax(marks));
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check whether an array includes a particular value or not</h2>

The `Array#includes()` method is used to determine whether an array includes a particular value among its entries by returning either true or false. Let's see an example to find an element(numeric and string) within an array.

```javascript
var numericArray = [1, 2, 3, 4];
console.log(numericArray.includes(3)); // true

var stringArray = ["green", "yellow", "blue"];
console.log(stringArray.includes("blue")); //true
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you compare scalar arrays</h2>

You can use length and every method of arrays to compare two scalar(compared directly using ===) arrays. The combination of these expressions can give the expected result,

```javascript
const arrayFirst = [1, 2, 3, 4, 5];
const arraySecond = [1, 2, 3, 4, 5];
console.log(
arrayFirst.length === arraySecond.length &&
    arrayFirst.every((value, index) => value === arraySecond[index])
); // true
```

If you would like to compare arrays irrespective of order then you should sort them before,

```javascript
const arrayFirst = [2, 3, 1, 4, 5];
const arraySecond = [1, 2, 3, 4, 5];
console.log(
arrayFirst.length === arraySecond.length &&
    arrayFirst.sort().every((value, index) => value === arraySecond[index])
); //true
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are typed arrays</h2>

Typed arrays are array-like objects from ECMAScript 6 API for handling binary data. JavaScript provides 8 Typed array types,

1. Int8Array: An array of 8-bit signed integers </br>
2. Int16Array: An array of 16-bit signed integers </br>
3. Int32Array: An array of 32-bit signed integers </br>
4. Uint8Array: An array of 8-bit unsigned integers </br>
5. Uint16Array: An array of 16-bit unsigned integers </br>
6. Uint32Array: An array of 32-bit unsigned integers </br>
7. Float32Array: An array of 32-bit floating point numbers </br>
8. Float64Array: An array of 64-bit floating point numbers </br>

For example, you can create an array of 8-bit signed integers as below

```javascript
const a = new Int8Array(); // You can pre-allocate n bytes

const bytes = 1024;
const a = new Int8Array(bytes);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is ArrayBuffer</h2>

An ArrayBuffer object is used to represent a generic, fixed-length raw binary data buffer. You can create it as below,

```javascript
let buffer = new ArrayBuffer(16); // create a buffer of length 16
alert(buffer.byteLength); // 16
```

To manipulate an ArrayBuffer, we need to use a “view” object.

```javascript
//Create a DataView referring to the buffer
let view = new DataView(buffer);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What happens with negating an array</h2>

Negating an array with `!` character will coerce the array into a boolean. Since Arrays are considered to be truthy So negating it will return `false`.

```javascript
console.log(![]); // false
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What happens if we add two arrays</h2>

If you add two arrays together, it will convert them both to strings and concatenate them. For example, the result of adding arrays would be as below,

```javascript
console.log(["a"] + ["b"]); // "ab"
console.log([] + []); // ""
console.log(![] + []); // "false", because ![] returns false.
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you remove falsy values from an array</h2>

You can apply the filter method on the array by passing Boolean as a parameter. This way it removes all falsy values(0, undefined, null, false and "") from the array.

```javascript
const myArray = [false, null, 1, 5, undefined];
myArray.filter(Boolean); // [1, 5] // is same as myArray.filter(x => x);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you get unique values of an array</h2>

You can get unique values of an array with the combination of `Set` and rest expression/spread(...) syntax.

```javascript
console.log([...new Set([1, 2, 4, 4, 3])]); // [1, 2, 4, 3]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you combine two or more arrays</h2>

The concat() method is used to join two or more arrays by returning a new array containing all the elements. The syntax would be as below,

```javascript
array1.concat(array2, array3, ..., arrayX)
```

Let's take an example of array's concatenation with veggies and fruits arrays,

```javascript
var veggies = ["Tomato", "Carrot", "Cabbage"];
var fruits = ["Apple", "Orange", "Pears"];
var veggiesAndFruits = veggies.concat(fruits);
console.log(veggiesAndFruits); // Tomato, Carrot, Cabbage, Apple, Orange, Pears
```

**Note**: Also you can use spred operator

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the easiest way to convert an array to an object</h2>

You can convert an array to an object with the same data using spread(...) operator.

```javascript
var fruits = ["banana", "apple", "orange", "watermelon"];
var fruitsObject = { ...fruits };
console.log(fruitsObject); // {0: "banana", 1: "apple", 2: "orange", 3: "watermelon"}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you create an array with some data</h2>

You can create an array with some data or an array with the same values using `fill` method.

```javascript
var newArray = new Array(5).fill("0");
console.log(newArray); // ["0", "0", "0", "0", "0"]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you flattening multi dimensional arrays</h2>

Flattening bi-dimensional arrays is trivial with Spread operator.

```javascript
const biDimensionalArr = [11, [22, 33], [44, 55], [66, 77], 88, 99];
const flattenArr = [].concat(...biDimensionalArr); // [11, 22, 33, 44, 55, 66, 77, 88, 99]
```

But you can make it work with multi-dimensional arrays by recursive calls,

```javascript
function flattenMultiArray(arr) {
const flattened = [].concat(...arr);
return flattened.some((item) => Array.isArray(item))
    ? flattenMultiArray(flattened)
    : flattened;
}
const multiDimensionalArr = [11, [22, 33], [44, [55, 66, [77, [88]], 99]]];
const flatArr = flattenMultiArray(multiDimensionalArr); // [11, 22, 33, 44, 55, 66, 77, 88, 99]
```

Also you can use the `flat` method of Array.

```javascript
const arr = [1, [2, 3], 4, 5, [6, 7]];
const fllattenArr = arr.flat(); // [1, 2, 3, 4, 5, 6, 7]

// And for multiDemensional arrays
const multiDimensionalArr = [11, [22, 33], [44, [55, 66, [77, [88]], 99]]];
const oneStepFlat = multiDimensionalArr.flat(1); // [11, 22, 33, 44, [55, 66, [77, [88]], 99]]
const towStep = multiDimensionalArr.flat(2); // [11, 22, 33, 44, 55, 66, [77, [88]], 99]
const fullyFlatArray = multiDimensionalArr.flat(Infinity); // [11, 22, 33, 44, 55, 66, 77, 88, 99]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you empty an array</h2>

You can empty an array quickly by setting the array length to zero.

```javascript
let cities = ["Singapore", "Delhi", "London"];
cities.length = 0; // cities becomes []
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the easiest way to resize an array</h2>

The length property of an array is useful to resize or empty an array quickly. Let's apply length property on number array to resize the number of elements from 5 to 2,

```javascript
var array = [1, 2, 3, 4, 5];
console.log(array.length); // 5

array.length = 2;
console.log(array.length); // 2
console.log(array); // [1,2]
```

and the array can be emptied too

```javascript
var array = [1, 2, 3, 4, 5];
array.length = 0;
console.log(array.length); // 0
console.log(array); // []
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How to verify if a variable is an array</h2>

It is possible to check if a variable is an array instance using 3 different ways,

1. Array.isArray() method:

  The `Array.isArray(value)` utility function is used to determine whether value is an array or not. This function returns a true boolean value if the variable is an array and a false value if it is not.

  ```javascript
  const numbers = [1, 2, 3];
  const user = { name: "John" };
  Array.isArray(numbers); // true
  Array.isArray(user); //false
  ```

2. instanceof operator:

  The instanceof operator is used to check the type of an array at run time. It returns true if the type of a variable is an Array other false for other type.

  ```javascript
  const numbers = [1, 2, 3];
  const user = { name: "John" };
  console.log(numbers instanceof Array); // true
  console.log(user instanceof Array); // false
  ```

3. Checking constructor type:

  The constructor property of the variable is used to determine whether the variable Array type or not.

  ```javascript
  const numbers = [1, 2, 3];
  const user = { name: "John" };
  console.log(numbers.constructor === Array); // true
  console.log(user.constructor === Array); // false
  ```

**[⬆ Back to Top](#table-of-contents)**