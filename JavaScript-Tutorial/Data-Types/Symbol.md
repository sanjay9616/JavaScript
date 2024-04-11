<h1>Symbol</h1>

The JavaScript ES6 introduced a new primitive data type called Symbol. Symbols are immutable (cannot be changed) and are unique. For example,

```javascript
// two symbols with the same description
const value1 = Symbol('hello');
const value2 = Symbol('hello');
console.log(value1 === value2); // false
```

You use the Symbol() function to create a Symbol. For example,

```javascript
// creating symbol
const x = Symbol()
typeof x; // symbol
```

You can pass an optional string as its description. For example,

```javascript
const x = Symbol('hey');
console.log(x); // Symbol(hey)
```

To access the description of a symbol, we use the . operator. For example,

```javascript
const x = Symbol('hey');
console.log(x.description); // hey
```

You can add symbols as a key in an object using square brackets []. For example,

```javascript
let id = Symbol("id");
let person = {
    name: "Jack",

    // adding symbol as a key
    [id]: 123 // not "id": 123
};
console.log(person); // {name: "Jack", Symbol(id): 123}
```

The for...in loop does not iterate over Symbolic properties. For example,

```javascript
let id = Symbol("id");
let person = {
    name: "Jack",
    age: 25,
    [id]: 12
};
// using for...in
for (let key in person) {
    console.log(key);
}

// Output
name
age
```

**Benefit of Using Symbols in Object**

If the same code snippet is used in various programs, then it is better to use Symbols in the object key. It's because you can use the same key name in different codes and avoid duplication issues. For example,

```javascript
let person = {
    name: "Jack"
};
// creating Symbol
let id = Symbol("id");
// adding symbol as a key
person[id] = 12;
```

**Symbol Methods**

| Method     | Description                                                  |
| ---------- | ------------------------------------------------------------ |
| for()      | Searches for existing symbols                                |
| keyFor()   | Returns a shared symbol key from the global symbol registry. |
| toSource() | Returns a string containing the source of the Symbol object  |
| toString() | Returns a string containing the description of the Symbol    |
| valueOf()  | Returns the primitive value of the Symbol object.            |

```javascript
// get symbol by name
let sym = Symbol.for('hello');
let sym1 = Symbol.for('id');
// get name by symbol
console.log( Symbol.keyFor(sym) ); // hello
console.log( Symbol.keyFor(sym1) ); // id
```

**Symbol Properties**

| Properties         | Description                                                                        |
| ------------------ | ---------------------------------------------------------------------------------- |
| asyncIterator      | Returns the default AsyncIterator for an object                                    |
| hasInstance        | Determines if a constructor object recognizes an object as its instance            |
| isConcatSpreadable | Indicates if an object should be flattened to its array elements                   |
| iterator           | Returns the default iterator for an object                                         |
| match              | Matches against a string                                                           |
| matchAll           | Returns an iterator that yields matches of the regular expression against a string |
| replace            | Replaces matched substrings of a string                                            |
| search             | Returns the index within a string that matches the regular expression              |
| split              | Splits a string at the indices that match a regular expression                     |
| species            | Creates derived objects                                                            |
| toPrimitive        | Converts an object to a primitive value                                            |
| toStringTag        | Gives the default description of an object                                         |
| description        | Returns a string containing the description of the symbol                          |

```javascript
const x = Symbol('hey');
// description property
console.log(x.description); // hey
const stringArray = ['a', 'b', 'c'];
const numberArray = [1, 2, 3];
// isConcatSpreadable property
numberArray[Symbol.isConcatSpreadable] = false;
let result = stringArray.concat(numberArray);
console.log(result); // ["a", "b", "c", [1, 2, 3]]
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>