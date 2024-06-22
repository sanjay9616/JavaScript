<h1>Number</h1>

A JavaScript Boolean represents one of two values: true or false.

You can use the Boolean() function to find out if an expression (or a variable) is true:

```javascript
console.log(Boolean(10 > 9)) // true
```

Or even easier:

```javascript
console.log(10 > 9) // true
```

**Everything With a "Value" is True**

```javascript
console.log(Boolean(100)) // true
console.log(Boolean(3.14)) // true
console.log(Boolean(-15)) // true
console.log(Boolean("Hello")) // true
console.log(Boolean("false")) // true
console.log(Boolean(7 + 1 + 3.14)) // true
```

**Everything Without a "Value" is False**

```javascript
console.log(Boolean(0)) // false
console.log(Boolean(-0)) // false
console.log(Boolean("")) // false

let x; // The Boolean value of undefined is false:
console.log(Boolean(x)); // false

let x = null; // The Boolean value of null is false:
console.log(Boolean(x)); // false

let x = false; // The Boolean value of false is (you guessed it) false
console.log(Boolean(x)); // false

let x = 10 / "Hallo"; // The Boolean value of NaN is false
console.log(Boolean(x)); // false
```

**But booleans can also be defined as objects with the keyword new**

The new keyword complicates the code and slows down execution speed.

```javascript
let y = new Boolean(false);
console.log(y) // [Boolean: false]

let x = false;
let y = new Boolean(false);
console.log(typeof(x), typeof(y)) // boolean object

let x = false;
let y = new Boolean(false);
console.log(x == y) // true

let x = false;
let y = new Boolean(false);
console.log(x === y) // false

let x = new Boolean(false);
let y = new Boolean(false);
console.log(x == y) // false - Comparing two JavaScript objects always return false.

let x = new Boolean(false);
let y = new Boolean(false);
console.log(x === y) // false - Comparing two JavaScript objects always return false.
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
