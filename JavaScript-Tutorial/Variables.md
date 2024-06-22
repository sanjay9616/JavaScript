<h1>JavaScript Variables</h1>

JavaScript Variables can be declared in 4 ways: </br>
1. Automatically </br>
2. Using var </br>
3. Using let </br>
4. Using const </br>

```javascript
a = 9; // Automatically
var b = 1; // Using var
let c = 3 // Using let
const d = 8; // Using const
```

You can declare many variables in one statement.

```javascript
let person = "John Doe", carName = "Volvo", price = 200;
```

You can list out the differences in a tabular format

| var                                | let                                             | const                                  |
| ---------------------------------- | ----------------------------------------------- | -------------------------------------- |
| Redeclare and reassign is possible | Redeclare not possible but reassign is possible | Redeclare and reassign is not possible |
| Global scope                       | Block scope                                     | Block scope                            |

<h2>JavaScript Let:</h2>

The let keyword was introduced in ES6 (2015) </br>
Variables declared with let have Block Scope </br>
Variables declared with let must be Declared before use </br>
Variables declared with let cannot be Redeclared in the same scope </br>

<h3>JavaScript Variable (var & let) Scope</h3>

```javascript
{
  let x = 2;
}
// x can NOT be used here
```

```javascript
{
  var x = 2;
}
// x CAN be used here
```

```javascript
let x = "John Doe";
let x = 0; // you can NOT do this - redeclare
```

```javascript
var x = "John Doe";
var x = 0; // you can do this - redeclare
```


```javascript
var x = 10; // Here x is 10
{
    var x = 2; // Here x is 2
}
// Here x is 2
```

```javascript
let x = 10; // Here x is 10
{
    let x = 2; // Here x is 2
}
// Here x is 10
```

**Difference Between var, let and const**

|       | Block Scope | Redeclare | Reassign | Hoisted | Binds this |
| ----- | ----------- | --------- | -------- | ------- | ---------- |
| var   | No          | Yes       | Yes      | Yes     | Yes        |
| let   | Yes         | No        | Yes      | No      | No         |
| const | Yes         | No        | No       | No      | No         |

<h3>JavaScript Variable (var & let) Redeclaring</h3>

```javascript
var x = 2; // Now x is 2
var x = 3; // Now x is 3
```

```javascript
var x = 2;   // Allowed
let x = 3;   // Not allowed
{
    let x = 2;   // Allowed
    let x = 3;   // Not allowed
}
{
    let x = 2;   // Allowed
    var x = 3;   // Not allowed
}
```

```javascript
let x = 2;   // Allowed
{
    let x = 3;   // Allowed
}
{
    let x = 4;    // Allowed
}
```

<h3>JavaScript Variable (var & let) Hoisting</h3>

Variables defined with var are hoisted to the top and can be initialized at any time

```javascript
carName = "Volvo";
var carName;
```

WARNING: Meaning: Using a let variable before it is declared will result in a ReferenceError:

```javascript
carName = "Saab";
let carName = "Volvo";
```

<h2>JavaScript Const:</h2>

Variables defined with const cannot be Redeclared </br>
Variables defined with const cannot be Reassigned </br>
Variables defined with const have Block Scope </br>

```javascript
const PI = 3.141592653589793;
PI = 3.14;      // This will give an error
PI = PI + 10;   // This will also give an error
```

JavaScript const variables must be assigned a value when they are declared

```javascript
const PI = 3.14159265359; // OK

const PI; // Incorrect
PI = 3.14159265359;
```

**Constant Objects and Arrays**

```javascript
const cars = ["Saab", "Volvo", "BMW"]; // You can create a constant array:
cars[0] = "Toyota"; // You can change an element:
cars.push("Audi"); // You can add an element:

cars = ["Toyota", "Volvo", "Audi"];    // ERROR - But you can NOT reassign the array
```

```javascript
const car = {type:"Fiat", model:"500", color:"white"}; // You can create a const object:
car.color = "red"; // You can change a property:
car.owner = "Johnson"; // You can add a property:

car = {type:"Volvo", model:"EX60", color:"red"};    // ERROR - But you can NOT reassign the object:
```

<h3>JavaScript Variable (const) Scope</h3>

```javascript
const x = 10; // Here x is 10
{
    const x = 2; // Here x is 2
}
// Here x is 10
```


```javascript
var x = 2;     // Allowed
const x = 2;   // Not allowed
{
    let x = 2;     // Allowed
    const x = 2;   // Not allowed
}
{
    const x = 2;   // Allowed
    const x = 2;   // Not allowed
}
```

```javascript
const x = 2;     // Allowed
x = 2;           // Not allowed
var x = 2;       // Not allowed
let x = 2;       // Not allowed
const x = 2;     // Not allowed
{
  const x = 2;   // Allowed
  x = 2;         // Not allowed
  var x = 2;     // Not allowed
  let x = 2;     // Not allowed
  const x = 2;   // Not allowed
}
```


```javascript
const x = 2;       // Allowed
{
  const x = 3;   // Allowed
}
{
  const x = 4;   // Allowed
}
```

Variables defined with var are hoisted to the top and can be initialized at any time

```javascript
carName = "Volvo";
var carName;
```

Variables defined with const are also hoisted to the top, but not initialized. - `ReferenceError`

```javascript
alert (carName);
const carName = "Volvo";
```


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
