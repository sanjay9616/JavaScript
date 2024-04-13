<h1>JavaScript Arrays</h1>

An array is a special variable, which can hold more than one value </br>
Arrays are a special type of objects. The typeof operator in JavaScript returns "object" for arrays.

```javascript
// Creating an Array
const array_name = [item1, item2, ...];
const array_name = new Array(item1, item2, ...) // The new keyword complicates the code and slows down execution speed.
```

**Example:**

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort()
console.log(fruits) // [ 'Apple', 'Banana', 'Mango', 'Orange' ]
console.log(fruits.length) // 4
console.log(fruits instanceof Array) // true
console.log(Array.isArray(fruits)) // true

// WARNING !!
const fruits = ["Banana", "Orange", "Apple"];
fruits[6] = "Lemon";  // Creates undefined "holes" in fruits
console.log(fruits) // [ 'Banana', 'Orange', 'Apple', <3 empty items>, 'Lemon' ]

// WARNING !!
// If you use named indexes, JavaScript will redefine the array to an object.
// After that, some array methods and properties will produce incorrect results.
const person = [];
person["firstName"] = "John";
person["lastName"] = "Doe";
person["age"] = 46;
console.log(person) // [ firstName: 'John', lastName: 'Doe', age: 46 ]
```

### Table of Contents

| No. | Topic                                                   |
| --- | ------------------------------------------------------- |
| 1   | [Basic Array Methods](#Basic-Array-Methods)             |
| 2   | [JavaScript Search Methods](#JavaScript-Search-Methods) |
| 3   | [Sorting Arrays Methods](#Sorting-Arrays-Methods)       |
| 4   | [Array Iteration Methods](#Array-Iteration-Methods)     |

### <h2>Basic Array Methods</h2>

| Method       | Description                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| length       | returns the length (size) of an array                                                                                         |
| toString()   | converts an array to a string of (comma separated) array values                                                               |
| at()         | Get the element at index of Array                                                                                             |
| join()       | Joins all array elements into a string using specified separator                                                              |
| pop()        | Removes last element from the array and returns the value that was "popped out"                                               |
| push()       | adds a new element to an array at the end                                                                                     |
| shift()      | removes the first array element and "shifts" all other elements to a lower index and returns the value that was "shifted out" |
| unshift()    | adds a new element to an array (at the beginning), and "unshifts" older elements                                              |
| delete()     | Remove element at index and leaves undefined holes in the array                                                               |
| concat()     | creates a new array by merging (concatenating) existing arrays                                                                |
| copyWithin() | copies array elements to another position in an array. The copyWithin() method overwrites the existing values                 |
| flat()       | creates a new array with sub-array elements concatenated to a specified depth                                                 |
| splice()     | Remove some element at index and insert items at index without leaving "holes" in the array                                   |
| toSpliced()  | Same as Splice() but toSplced() creates new array                                                                             |
| slice()      | Returns selected elements in an array, as a new array                                                                         |

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.toString()) // Banana,Orange,Apple,Mango

const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.at(2)) // Apple
console.log(fruits[2]) // Apple

const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.join(' * ')) // Banana * Orange * Apple * Mango

const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.pop()) // Mango
console.log(fruits) // [ 'Banana', 'Orange', 'Apple' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.push("kiwi")) // 5 (returns the new array length)
console.log(fruits) // [ 'Banana', 'Orange', 'Apple', 'Mango', 'kiwi' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.shift()) // Banana (returns the value that was "shifted out")
console.log(fruits) // [ 'Orange', 'Apple', 'Mango' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.unshift("Lemon")); // 5 (returns the new array length)
console.log(fruits) // [ 'Lemon', 'Banana', 'Orange', 'Apple', 'Mango' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
delete fruits[0];
console.log(fruits) // [ <1 empty item>, 'Orange', 'Apple', 'Mango' ]

const myGirls = ["Cecilie", "Lone"];
const myBoys = ["Emil", "Tobias", "Linus"];
const myChildren = myGirls.concat(myBoys);
console.log(myChildren) // [ 'Cecilie', 'Lone', 'Emil', 'Tobias', 'Linus' ]

const arr1 = ["Emil", "Tobias", "Linus"];
const myChildren = arr1.concat("Peter", "Sanjay"); // can also take strings as arguments
console.log(myChildren) // [ 'Emil', 'Tobias', 'Linus', 'Peter', 'Sanjay' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.copyWithin(2, 0); // Copy to index 2, all elements from index 0
console.log(fruits) // [ 'Banana', 'Orange', 'Banana', 'Orange' ]

const fruits = ["Banana", "Orange", "Apple", "Mango", "Kiwi"];
fruits.copyWithin(2, 0, 2); // Copy to index 2, the elements from index 0 to 2
console.log(fruits) // [ 'Banana', 'Orange', 'Banana', 'Orange', 'Apple' ]

const myArr = [[1,2],[3,4],[5,6],7,8];
const newArr = myArr.flat();
console.log(newArr) // [1, 2, 3, 4, 5, 6, 7, 8]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 0, "Lemon", "Kiwi"); // delete 0 element from 2nd index and add "Lemon", "Kiwi"
console.log(fruits) // [ 'Banana', 'Orange', 'Lemon', 'Kiwi', 'Apple', 'Mango' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 2, "Lemon", "Kiwi"); // delete 2 element from 2nd index and add "Lemon", "Kiwi"
console.log(fruits) // [ 'Banana', 'Orange', 'Lemon', 'Kiwi' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(0, 1); // delete 1 element from 0th index
console.log(fruits) // [ 'Orange', 'Apple', 'Mango' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(1);
console.log(fruits) // [ 'Banana' ]

const months = ["Jan", "Feb", "Mar", "Apr"];
const spliced = months.toSpliced(0, 1);
console.log(spliced) // [ 'Orange', 'Apple', 'Mango' ]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JavaScript Search Methods</h2>

| Method          | Description                                                                                             |
| --------------- | ------------------------------------------------------------------------------------------------------- |
| indexOf()       | returns the position of the fist occurrence of the specified element, return -1 if element is not found |
| lastIndexOf()   | returns the position of the last occurrence of the specified element, return -1 if element is not found |
| includes()      | This allows us to check if an element is present in an array                                            |
| find()          | returns the value of the first array element that passes a test function                                |
| findIndex()     | returns the index of the first array element that passes a test function                                |
| findLast()      | start from the end of an array and return the value of the first element that satisfies a condition     |
| findLastIndex() | finds the index of the last element that satisfies a condition                                          |

```javascript
// Syntax - array.indexOf(item, start) 2nd argument is Optional. Where to start the search default start is 0
const fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.indexOf("Orange")) // 1

// Syntax - array.lastIndexOf(item, start) 2nd argument is Optional. Where to start the search default start is 0
const fruits = ["Apple", "Orange", "Apple", "Mango"];
console.log(fruits.lastIndexOf("Apple")) // 2

const fruits = ["Apple", "Orange", "Apple", "Mango"];
console.log(fruits.includes("Apple")) // true

const temp = [27, 28, 30, 40, 42, 35, 30];
let element = temp.find(x => x > 40); // 4
console.log(element) // 42

const temp = [27, 28, 30, 40, 42, 52, 30];
let lastElement = temp.findLast(x => x > 40);
console.log(lastElement) // 52

const temp = [27, 28, 30, 40, 42, 35, 30];
let index = temp.findIndex(x => x > 40);
console.log(index) // 4

const temp = [27, 28, 30, 40, 42, 35, 30];
let lastIndex = temp.findLastIndex(x => x > 40);
console.log(lastIndex) // 4
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Sorting Arrays Methods</h2>

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
console.log(fruits) // [ 'Apple', 'Banana', 'Mango', 'Orange' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.reverse();
console.log(fruits) // [ 'Mango', 'Apple', 'Orange', 'Banana' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
const sorted = fruits.toSorted();
console.log(sorted) // [ 'Apple', 'Banana', 'Mango', 'Orange' ]

const fruits = ["Banana", "Orange", "Apple", "Mango"];
const reversed = months.toReversed();
console.log(reversed) // [ 'Mango', 'Apple', 'Orange', 'Banana' ]

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

### <h2>Array Iteration Methods</h2>

**[⬆ Back to Top](#table-of-contents)**

<h3>Array forEach</h3>

The forEach() method calls a function (a callback function) once for each array element.

```javascript
const numbers = [45, 4, 9, 16, 25]
let sum = 0
numbers.forEach((number) => sum = sum + number)
console.log(sum) // 99
```

<h3>Array map()</h3>

Creates a new array by calling a function for iterating every element of the original array.

```javascript
let arr1 = [1, 2, 3, 4, 5]
const arr2 = Arr1.map((val) => val * 5)
console.log(arr2) // [ 5, 10, 15, 20, 25 ]
```

<h3>Array fill()</h3>

Fills specified elements in an array with a value

```javascript
let arr1 = [1, 2, 3, 4, 5]
const arr2 = arr1.fill(9)
console.log(arr2) // [ 9, 9, 9, 9, 9 ]

arr = new Array(3).fill(false)
console.log(arr) // [ false, false, false ]
```

<h3>Array some()</h3>

Return true if at least one element in the array passes the test, else false.

```javascript
let arr1 = [1, 2, 3, 4, 5]
const bol = arr1.some((val) => val == 3)
console.log(bol) // true

let arr1 = [1, 2, 3, 4, 5]
const bol = arr1.some((val) => val == 9)
console.log(bol) // false
```

<h3>Array every()</h3>

Return true if all elements in the array passes the test, else false.

```javascript
let arr1 = [1, 2, 3, 4, 5]
const bol = arr1.every((val) => val > 0)
console.log(bol) // true

let arr1 = [1, 2, 3, 4, 5]
const bol = arr1.every((val) => val > 2)
console.log(bol) // false
```

<h3>Reduce every()</h3>

Reduce() method in JavaScript is used to reduce the array to a single value and executes a provided function for each value of the array (from left-to-right) and the return value of the function is stored in an accumulator.

```javascript
let array = [15, 16, 17, 18, 19];
const val = array.reduce((accumulator, currentValue, index) => accumulator+currentValue)
console.log(val) // 85
![kkkkkkkk](https://github.com/sanjay9616/JavaScript/assets/87460579/08f43899-eaf8-42f8-94ed-f31b8d0939db)

const array = [{ x: 1 }, { x: 2 }, { x: 3 }];
const val = array.reduce((accumulator, currentValue) => accumulator + currentValue.x, 0)
console.log(val) // 6
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/Object.md"> 🔙 Back</a></h2>
