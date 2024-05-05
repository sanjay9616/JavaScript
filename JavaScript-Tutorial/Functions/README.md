<h1>Lambda or Arrow Function</h1>

**this keyword** represents the current context, or it can access variable, properties, and methods within it's scope

```javascript
let user = {
    name: "Sanjay",
    salary: 21,
    welcomeMsg: function() {
        console.log(`Welcome ${this.name}`);
    }
}
user.welcomeMsg() // Welcome Sanjay
user.name = "Anurag"
user.welcomeMsg() // Welcome Anurag
```

```javascript
let user = {
    name: "Sanjay",
    printThis: function() {
        console.log(this);
    }
}
user.printThis() // { name: 'Sanjay', printThis: [Function: printThis] }
user.name = "Anurag"
user.printThis() // { name: 'Anurag', printThis: [Function: printThis] }
```

**Definiion:** `An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.`

```js
const addTwo = (a, b) => {
    return a + b;
}
console.log(addTwo(4, 5)) // 9

// ########### OR ########### //

const addTwo = (a, b) => (a + b) // if you use () then don't need return statement
console.log(addTwo(4, 5)) // 9
```

<h1>First Class Function</h1>



<h1>First Order Function</h1>
<h1>Higher Order Function</h1>
<h1>Unary Function</h1>
<h1>Pure Function</h1>
<h1>IIFE(Immediately Invoked Function Expression)</h1>
<h1>isFinite Function</h1>
<h1>Anonymous Function</h1>
<h1>compareFunction Function</h1>
<h1>Thunk Function</h1>
<h1>async Function</h1>
<h1>Pure and Impure Function</h1>
<h1>Compose and Pipe Function</h1>
<h1>uneval and eval Function</h1>