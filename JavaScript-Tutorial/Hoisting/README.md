<h1>Hoisting in Javascript</h1>

In JavaScript, hoisting refers to the built-in behavior of the language through which declarations of functions, variables, and classes are moved to the top of their scope – all before code execution. In turn, **this allows us to use functions, variables, and classes before they are declared**.

```javascript
console.log(x) // undefined (declared but not assigned - memory created)
console.log(demo()) // Hoisting Chapter
var x = 9 // global scope
function demo() { // global scope
    return "Hoisting Chapter"
}
```

```javascript
console.log(x) // ReferenceError (not declared - memory not created)
let x = 9 // local scope
```

```javascript
console.log(x) // ReferenceError (not declared - memory not created)
let const = 9 // local scope
```

```javascript
console.log(demo) // undefined (declared but not assigned - memory created)
var demo = () => { // arrow function it behaves like a variable - global scope
    return "Hoisting Chapter"
}
```

```javascript
console.log(demo) // ReferenceError (not declared - memory not created)
let demo = () => { // arrow function it behaves like a variable - local scope
    return "Hoisting Chapter"
}
```

```javascript
console.log(demo) // ReferenceError (not declared - memory not created)
const demo = () => { // arrow function it behaves like a variable - local scope
    return "Hoisting Chapter"
}
```