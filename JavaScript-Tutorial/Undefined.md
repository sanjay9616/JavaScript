<h1>Undefined</h1>

Undefined is a type of Data type in JavaScript. It is a primitive value undefined, when a variable is declared and not initialized or not assigned with any value. By default, the variable was stored with an Undefined value.

Undefined is a global read-only variable that represents the value Undefined. Undefined is a type of primitive type

You don’t explicitly create undefined. It’s automatically assigned to variables that lack a value:

**1. undefined Value in Variables**

```javascript
let newVar;
console.log(newVar) // undefined
```

**2. undefined Value in Functions**

```javascript
function sayhi(name) {
    console.log(`hi ${name}`);
}
x = sayhi('hike');
console.log(`value in x= ${x}`);

// Output

hi hike
value in x= undefined
```

**3. undefined value in Object Properties**

```javascript
const person = { name: "Alice" };
console.log(person.age); // undefined
```

**How to Check for undefined value**

To check for undefined value , we can use the typeof to check if the value is undefined or not:

```javascript
let myVariable;
if (typeof myVariable === "undefined") {
  console.log("myVariable is undefined");
} else {
  console.log("myVariable is defined");
}
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>
