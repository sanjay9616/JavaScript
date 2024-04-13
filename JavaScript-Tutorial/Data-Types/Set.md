<h1>JavaScript Sets</h1>

A JavaScript Set is a collection of unique values. </br>
Each value can only occur once in a Set. </br>
A Set can hold any value of any data type. </br>

<h2>Set Methods</h2>

| Method    | Description                                                 |
| --------- | ----------------------------------------------------------- |
| new Set() | Creates a new Set                                           |
| add()     | Adds a new element to the Set                               |
| delete()  | Removes an element from a Set                               |
| has()     | Returns true if a value exists                              |
| clear()   | Removes all elements from a Set                             |
| forEach() | Invokes a callback for each element                         |
| values()  | Returns an Iterator with all the values in a Set            |
| keys()    | Same as values()                                            |
| entries() | Returns an Iterator with the [value,value] pairs from a Set |
| size      | Returns the number elements in a Set                        |

```javascript
// Create a Set
const letters = new Set();
// Add Values to the Set
letters.add("a");
letters.add("b");
letters.add("c");
console.log(letters, typeof letters) // Set(3) { 'a', 'b', 'c' } object
console.log(letters.keys()) // [Set Iterator] { 'a', 'b', 'c' }
console.log(letters.values()) // [Set Iterator] { 'a', 'b', 'c' }
console.log(letters.entries()) // [Set Entries] { [ 'a', 'a' ], [ 'b', 'b' ], [ 'c', 'c' ] }
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/Object.md"> 🔙 Back</a></h2>