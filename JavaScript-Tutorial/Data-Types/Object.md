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

| No. | Topic                                                                                                                                    |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [Creating a JavaScript Object](#Creating-a-JavaScript-Object)                                                                            |
| 2   | [JavaScript Objects are Mutable](#JavaScript-Objects-are-Mutable)                                                                        |
| 3   | [Displaying the Object in a Loop](#Displaying-the-Object-in-a-Loop)                                                                      |
| 4   | [JavaScript Accessors](#JavaScript-Accessors)                                                                                            |
| 5   | [Object Prototypes](#Object-Prototypes)                                                                                                  |
| 6   | [JavaScript Iterators](#JavaScript-Iterators)                                                                                            |
| 7   | <a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/Set.md">JavaScript Sets</a>                 |
| 8   | <a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/Map.md">JavaScript Maps</a>                 |
| 9   | <a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/Object-Reference.md">ES5 Object Methods</a> |

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

### <h2>Displaying the Object in a Loop</h2>

```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

let txt = "";
for (let x in person) {
txt += person[x] + " ";
};
console.log(txt) // John 30 New York
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JavaScript Accessors</h2>

Getters and setters allow you to define Object Accessors (Computed Properties)

**JavaScript Getter**

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  get fullName() {
    return this.firstName + " " + this.lastName;
  }
};
console.log(person.fullName) // John Doe
```

**JavaScript Setter**

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  language: "",
  set lang(lang) {
    this.language = lang;
  }
};

person.lang = "en";
console.log(person.language) // en
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Object Prototypes</h2>

In JavaScript, every function and object has a property named prototype by default

```javascript
function Person () {
    this.name = 'John',
    this.age = 23
}

const person = new Person();

console.log(Person.prototype); // { ... }
```

You can not add a new property to an existing object constructor:

```javascript
Person.nationality = "English";
console.log(person.nationality) // Output - undefined
```

a prototype can be used to add properties and methods to a constructor function. And objects inherit properties and methods from a prototype

```javascript
Person.prototype.nationality = "English";
console.log(person.nationality) // Output - English
```

**Note**: The **syntax** to add the property to an object constructor: `objectConstructorName.prototype.key = 'value'`;

<h3>Add Methods to a Constructor Function Using Prototype</h3>

```javascript
function Person () {
    this.name = 'John',
    this.age = 23
}
const person1 = new Person();
Person.prototype.greet = function() {
    console.log('hello' + ' ' +  this.name);
}
person1.greet(); // hello John
```

<h3>Changing Prototype</h3>

If a prototype value is changed, then all the new objects will have the changed property value, and all the previously created objects will have the previous value. For example,

```javascript
function Person() {
    this.name = 'John'
}

Person.prototype.age = 20;

const person1 = new Person();

console.log(person1.age); // 20

Person.prototype = { age: 50 }

const person2 = new Person();

console.log(person2.age); // 50
console.log(person1.age); // 20
```

You can also access the prototype property of a constructor function from an object.

```javascript
function Person () {
    this.name = 'John'
}

Person.prototype.age = 24;

const person = new Person();

console.log(person.__proto__);   // { age: 24 }
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JavaScript Iterators<h2>

The iterator protocol defines how to produce a sequence of values from an object. </br>
An object becomes an iterator when it implements a next() method. </br>
The next() method must return an object with two properties: <br>
**1. value**: The value returned by the iterator (Can be omitted if done is true) </br>
**2. done**: true if the iterator has completed (false if the iterator has produced a new value) </br>

```javascript
const array = ['a', 'b', 'c'];
const it = array[Symbol.iterator]();
console.log(JSON.stringify(it.next())); // {"value":"a","done":false}
console.log(JSON.stringify(it.next())); // {"value":"b","done":false}
console.log(JSON.stringify(it.next())); // {"value":"c","done":false}
console.log(JSON.stringify(it.next())); // {"done":true}
```

```javascript
const array = ['a', 'b', 'c'];
const it = array[Symbol.iterator]()
for (let value of it) {
    console.log(value)
}

// Output

a
b
c
```

**[⬆ Back to Top](#table-of-contents)**

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>
