<h1>JavaScript Maps</h1>

A Map holds key-value pairs where the keys can be any datatype. </br>
A Map remembers the original insertion order of the keys. </br>
A Map has a property that represents the size of the map. </br>

<h2>Map Methods</h2>

| Method    | Description                                                     |
| --------- | --------------------------------------------------------------- |
| new Map() | Creates a new Map object                                        |
| set()     | Sets the value for a key in a Map                               |
| get()     | Gets the value for a key in a Map                               |
| clear()   | Removes all the elements from a Map                             |
| delete()  | Removes a Map element specified by a key                        |
| has()     | Returns true if a key exists in a Map                           |
| forEach() | Invokes a callback for each key/value pair in a Map             |
| entries() | Returns an iterator object with the [key, value] pairs in a Map |
| keys()    | Returns an iterator object with the keys in a Map               |
| values()  | Returns an iterator object of the values in a Map               |
| size      | Returns the number of Map elements                              |

```javascript
// Create a Map
const fruits = new Map([
  ["apples", 500],
  ["bananas", 300],
  ["oranges", 200]
]);
console.log(fruits) // Map(3) { 'apples' => 500, 'bananas' => 300, 'oranges' => 200 }

// Create a Map
const fruits = new Map();
// Set Map Values
fruits.set("apples", 500);
fruits.set("bananas", 300);
fruits.set("oranges", 200);
console.log(fruits) // Map(3) { 'apples' => 500, 'bananas' => 300, 'oranges' => 200 }

fruits.set("apples", 555); // The set() method can also be used to change existing Map values:
console.log(fruits) // Map(3) { 'apples' => 555, 'bananas' => 300, 'oranges' => 200 }

// The get() method gets the value of a key in a Map
console.log(fruits.get("oranges")) // 200

// The size property returns the number of elements in a Map
console.log(fruits.size) // 3

fruits.delete("apples"); // The delete() method removes a Map element:
console.log(fruits) // Map(2) { 'bananas' => 300, 'oranges' => 200 }

fruits.clear(); // The clear() method removes all the elements from a Map
console.log(fruits) // Map(0) {}

console.log(fruits.has("apples")) // false
console.log(typeof fruits) // object

// instanceof Map returns true
console.log(fruits instanceof Map) // true

console.log(fruits.keys()) // [Map Iterator] { 'apples', 'bananas', 'oranges' }
console.log(fruits.values()) // [Map Iterator] { 500, 300, 200 }
console.log(fruits.entries()) // { [ 'apples', 500 ], [ 'bananas', 300 ], [ 'oranges', 200 ] }
```

<h2>JavaScript Objects vs Maps</h2>

| Object                            | Map                           |
| --------------------------------- | ----------------------------- |
| Not directly iterable             | Directly iterable             |
| Do not have a size property       | Have a size property          |
| Keys must be Strings (or Symbols) | Keys can be any datatype      |
| Keys are not well ordered         | Keys are ordered by insertion |
| Have default keys                 | Do not have default keys      |


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>