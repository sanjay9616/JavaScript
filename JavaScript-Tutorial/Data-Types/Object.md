<h1>Objects</h1>

JavaScript variables can also contain many values. </br>
Objects are variables too. But objects can contain many values. </br>
Object values are written as name : value pairs (name and value separated by a colon).

`A JavaScript object is a collection of named values`

```javascript
let person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
console.log(typeof person) // object
```

Objects written as name value pairs are similar to:

1. Associative arrays in PHP</br>
2. Dictionaries in Python</br>
3. Hash tables in C</br>
3. Hash maps in Java</br>
4. Hashes in Ruby and Perl</br>

### Table of Contents

| No. | Topic                                                             |
| --- | ----------------------------------------------------------------- |
| 1   | [Creating a JavaScript Object](#Creating-a-JavaScript-Object)     |
| 2   | [JavaScript Objects are Mutable](#JavaScript-Objects-are-Mutable) |

### <h2>Creating a JavaScript Object</h2>

There are different ways to create new objects:

| No. | Method                                                                      |
| --- | --------------------------------------------------------------------------- |
| 1   | [Object literal Method](#Object-literal-Method)                             |
| 2   | [Object constructor Method](#Object-constructor-Method)                     |
| 3   | [Object create Method](#Object-create-Method)                               |
| 4   | [Function constructor Method](#Function-constructor-Method)                 |
| 5   | [Function constructor with prototype](#Function-constructor-with-prototype) |
| 6   | [ES6 Class Syntax Method](#ES6-Class-Syntax-Method)                         |
| 7   | [Singleton Pattern Method](#Singleton-Pattern-Method)                       |

### <h3>Object literal Method</h3>

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

Object literal property values can be of any data type, including array, function, and nested object.
```

**Note:** This is one of the easiest ways to create an object.

**[⬆ Back to Creating a JavaScript Object](#Creating-a-JavaScript-Object)**

### <h3>Object constructor Method</h3>

The simplest way to create an empty object is using the `Object` constructor. Currently this approach is not recommended.

```javascript
var object = new Object();
```

The `Object()` is a built-in constructor function so "new" keyword is not required. The above code snippet can be re-written as:

```javascript
var object = Object();
```

**[⬆ Back to Creating a JavaScript Object](#Creating-a-JavaScript-Object)**

### <h3>Object create Method</h3>

The create method of Object is used to create a new object by passing the specificied prototype object and properties as arguments, i.e., this pattern is helpful to create new objects based on existing objects.
The second argument is optional and it is used to create properties on a newly created object.

The following code creates a new empty object whose prototype is null.

```javascript
var object = Object.create(null);
```

**[⬆ Back to Creating a JavaScript Object](#Creating-a-JavaScript-Object)**

### <h3>Function constructor Method</h3>

In this approach, create any function and apply the new operator to create object instances.

```javascript
function Person(name) {
   this.name = name;
   this.age = 21;
}
var object = new Person("Sudheer");
```

**[⬆ Back to Creating a JavaScript Object](#Creating-a-JavaScript-Object)**

### <h3>Function constructor with prototype</h3>

This is similar to function constructor but it uses prototype for their properties and methods,

```javascript
function Person() {}
Person.prototype.name = "Sudheer";
var object = new Person();
```

This is equivalent to creating an instance with Object.create method with a function prototype and then calling that function with an instance and parameters as arguments.

```javascript
function func() {}

new func(x, y, z);
```

**(OR)**

```javascript
// Create a new instance using function prototype.
var newInstance = Object.create(func.prototype)

// Call the function
var result = func.call(newInstance, x, y, z),

// If the result is a non-null object then use it otherwise just use the new instance.
console.log(result && typeof result === 'object' ? result : newInstance);
```

**[⬆ Back to Creating a JavaScript Object](#Creating-a-JavaScript-Object)**

### <h3>ES6 Class Syntax Method</h3>

ES6 introduces class feature to create objects.

```javascript
class Person {
   constructor(name) {
      this.name = name;
   }
}

var object = new Person("Sudheer");
```

**[⬆ Back to Creating a JavaScript Object](#Creating-a-JavaScript-Object)**

### <h3>Singleton Pattern Method</h3>

A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance. This way one can ensure that they don't accidentally create multiple instances.

```javascript
var object = new (function () {
   this.name = "Sudheer";
})();
```

**[⬆ Back to Creating a JavaScript Object](#Creating-a-JavaScript-Object)**

**[⬆ Back to Top](#table-of-contents)**

### <h2>JavaScript Objects are Mutable</h2>

```javascript
let person = {
  firstName:"John",
  lastName:"Doe",
  age:50,
  eyeColor:"blue"
}

let x = person;
x.age = 10;
console.log(person, x)

// Output
{ firstName: 'John', lastName: 'Doe', age: 10, eyeColor: 'blue' }
{ firstName: 'John', lastName: 'Doe', age: 10, eyeColor: 'blue' }
```

**[⬆ Back to Top](#table-of-contents)**


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>
