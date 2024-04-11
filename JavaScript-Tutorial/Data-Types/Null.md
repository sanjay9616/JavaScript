
<h1>Null</h1>

In JavaScript, `null` represents the intentional absence of any object value. It is a primitive value that signifies the absence of a value or a placeholder for an object that doesn’t exist. It is distinct from `undefined`, which indicates a variable that has been declared but hasn’t been assigned a value.

```javascript
let number = null;
console.log("Type of number is:" ,typeof number); // Type of number is: object
```

```javascript
class Square {
	constructor(length) {
		this.length = length;
	}
	get area_of_square() {
		return Math.pow(this.length, 2);
	}

	// Static function that returns the length
	static create_function(length) {
		return length > 0 ? new Square(length) : null;
	}
}

let variableOne = Square.create_function(10);
console.log(variableOne.area_of_square); // 100

let variableTwo = Square.create_function();
console.log(variableTwo); // null
```

**Checking for null**

```javascript
const myValue = null;
if (myValue) {
console.log("Not null"); // This won't execute
} else {
console.log("Null"); // Output: "Null"
}
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>
