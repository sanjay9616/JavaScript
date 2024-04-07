### Table of Contents

| No. | Questions                                                           |
| --- | ------------------------------------------------------------------- |
| 1   | [Possible ways to create objects](#Possible-ways-to-create-objects) |
| 2   | [Prototype](#Prototype)                                             |
| 3   | [Call, Apply and Bind](#Call-Apply-and-Bind)                        |
| 4   | [JSON](#JSON)                                                       |
| 5   | [Object and Map](#Object-and-Map)                                   |
| 6   | [== and === operators](#==-and-===-operators)                       |
| 7   | [var, let, and const](#var-let-and-const)                           |

### <h2>Possible ways to create objects</h2>

   1. **Object literal syntax:**

      ```javascript
      var object = {
           name: "Sudheer",
           age: 34
      };

      Object literal property values can be of any data type, including array, function, and nested object.
      ```

      **Note:** This is one of the easiest ways to create an object.

   2. **Object constructor:**

      The simplest way to create an empty object is using the `Object` constructor. Currently this approach is not recommended.

      ```javascript
      var object = new Object();
      ```

      The `Object()` is a built-in constructor function so "new" keyword is not required. The above code snippet can be re-written as:

      ```javascript
      var object = Object();
      ```

   3. **Object's create method:**

      The create method of Object is used to create a new object by passing the specificied prototype object and properties as arguments, i.e., this pattern is helpful to create new objects based on existing objects.
      The second argument is optional and it is used to create properties on a newly created object.

      The following code creates a new empty object whose prototype is null.

      ```javascript
      var object = Object.create(null);
      ```

   4. **Function constructor:**

      In this approach, create any function and apply the new operator to create object instances.

      ```javascript
      function Person(name) {
        this.name = name;
        this.age = 21;
      }
      var object = new Person("Sudheer");
      ```

   5. **Function constructor with prototype:**

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

   6. **ES6 Class syntax:**

      ES6 introduces class feature to create objects.

      ```javascript
      class Person {
        constructor(name) {
          this.name = name;
        }
      }

      var object = new Person("Sudheer");
      ```

   7. **Singleton pattern:**

      A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance. This way one can ensure that they don't accidentally create multiple instances.

      ```javascript
      var object = new (function () {
        this.name = "Sudheer";
      })();
      ```

      **[⬆ Back to Top](#table-of-contents)**

### <h2>Prototype</h2>

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

**Add Methods to a Constructor Function Using Prototype**

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

**Changing Prototype**

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

<h3>Questions and Answers:</h3>

**1. How do you create an object with prototype?**

**Ans:** The Object.create() method is used to create a new object with the specified prototype object and properties. i.e, It uses an existing object as the prototype of the newly created object. It returns a new object with the specified prototype object and properties.

```javascript
let animal = {
  eats: true
};

// create a new object with animal as a prototype
let rabbit = Object.create(animal); // same as {__proto__: animal}

console.log(rabbit.eats); // true

console.log(rabbit.__proto__); // { eats: true }
```

**2. How do you get the prototype of an object?**

**Ans:** You can use the `Object.getPrototypeOf(obj)` method to return the `prototype` of the specified object. i.e. The value of the internal prototype property. If there are no inherited properties then `null` value is returned.

```javascript
const newPrototype = {};
const newObject = Object.create(newPrototype);

console.log(Object.getPrototypeOf(newObject) === newPrototype); // true
```

**3. How do you set prototype of one object to another?**

**Ans:** You can use the `Object.setPrototypeOf()` method that sets the prototype (i.e., the internal `Prototype` property) of a specified object to another object or null. For example, if you want to set prototype of a square object to rectangle object would be as follows,

```javascript
Object.setPrototypeOf(Square.prototype, Rectangle.prototype);
Object.setPrototypeOf({}, null);
```

**4. What happens If I pass string type for getPrototype method?**

**Ans:** In ES5, it will throw a TypeError exception if the obj parameter isn't an object. Whereas in ES2015, the parameter will be coerced to an `Object`.

```javascript
// ES5
Object.getPrototypeOf("James"); // TypeError: "James" is not an object
// ES2015
Object.getPrototypeOf("James"); // String.prototype
```

**5. Do all objects have prototypes?**

**Ans:** No. All objects have prototypes except for the base object which is created by the user, or an object that is created using the new keyword.

**6. What is a prototype chain?**

**Ans:** Prototype chaining is used to build new types of objects based on existing ones. It is similar to inheritance in a class based language. </br>
The prototype on object instance is available through Object.getPrototypeOf(object) or __proto__ property whereas prototype on constructors function is available through Object.prototype.

![prototype_chain](https://github.com/sanjay9616/JavaScript/assets/87460579/b1465657-f9ed-46bd-a591-3f8f330c4523)

**6. What is the difference between proto and prototype**

**Ans:** The `__proto__` object is the actual object that is used in the lookup chain to resolve methods, etc. Whereas `prototype` is the object that is used to build `__proto__` when you create an object with new.

```javascript
new Employee().__proto__ === Employee.prototype;
new Employee().prototype === undefined;
```

There are few more differences,

| feature    | Prototype                                                    | proto                                                      |
| ---------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| Access     | All the function constructors have prototype properties.     | All the objects have \_\_proto\_\_ property                |
| Purpose    | Used to reduce memory wastage with a single copy of function | Used in lookup chain to resolve methods, constructors etc. |
| ECMAScript | Introduced in ES6                                            | Introduced in ES5                                          |
| Usage      | Frequently used                                              | Rarely used                                                |

**[⬆ Back to Top](#table-of-contents)**

### <h2>Call, Apply and Bind</h2>

The difference between Call, Apply and Bind can be explained with below examples,

**Call:** The call() method invokes a function with a given `this` value and arguments provided one by one

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(
      greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
   );
}

invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How are you?
invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

**Apply:** Invokes the function with a given `this` value and allows you to pass in arguments as an array

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(
      greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
   );
}

invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
```

**Bind:** returns a new function, allowing you to pass any number of arguments

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(
      greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
   );
}

var inviteEmployee1 = invite.bind(employee1);
var inviteEmployee2 = invite.bind(employee2);
inviteEmployee1("Hello", "How are you?"); // Hello John Rodson, How are you?
inviteEmployee2("Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

Call and Apply are pretty much interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.

Bind creates a new function that will have `this` set to the first parameter passed to bind().

**Questions and Answers**

**1. How do you create your own bind method using either call or apply method?**

**Ans:** The custom bind function needs to be created on Function prototype inorder to use it as other builtin functions. This custom function should return a function similar to original bind method and the implementation of inner function needs to use apply method call.

The function which is going to bind using custom `myOwnBind` method act as the attached function(`boundTargetFunction`) and argument as the object for `apply` method call.

```js
Function.prototype.myOwnBind = function (whoIsCallingMe) {
   if (typeof this !== "function") {
   throw new Error(this + "cannot be bound as it's not callable");
   }
   const boundTargetFunction = this;
   return function () {
   boundTargetFunction.apply(whoIsCallingMe, arguments);
   };
};
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JSON</h2>

**JSON** is a text-based data format following JavaScript object syntax, which was popularized by `Douglas Crockford`. It is useful when you want to transmit data across a network. It is basically just a text file with an extension of .json, and a MIME type of application/json

**OR**

JSON (JavaScript Object Notation) is a lightweight format that is used for data interchanging. It is based on a subset of JavaScript language in the way objects are built in JavaScript.

**Parsing:** Converting a string to a native object

```javascript
JSON.parse(text);
```

**Stringification:** Converting a native object to a string so that it can be transmitted across the network

```javascript
JSON.stringify(object);
```
**Purpose:** When sending data to a web server, the data has to be in a string format. You can achieve this by converting JSON object into a string using stringify() method.

Below are the list of syntax rules of JSON </br>
1. The data is in name/value pairs </br>
2. The data is separated by commas </br>
3. Curly braces hold objects </br>
4. Square brackets hold arrays </br>

**Questions and Answers**

**1. How do you define JSON arrays?**

**Ans:** JSON arrays are written inside square brackets and arrays contain javascript objects. For example, the JSON array of users would be as below,

```javascript
"users":[
  {"firstName":"John", "lastName":"Abrahm"},
  {"firstName":"Anna", "lastName":"Smith"},
  {"firstName":"Shane", "lastName":"Warn"}
]
```

**2. What are the syntax rules of JSON?**

**Ans:** 1. The data is in name/value pairs <br>
         2. The data is separated by commas <br>
         3. Curly braces hold objects <br>
         4. Square brackets hold arrays <br>

**3. What is the purpose JSON stringify?**

**Ans:** When sending data to a web server, the data has to be in a string format. You can achieve this by converting JSON object into a string using stringify() method.

```javascript
var userJSON = { name: "John", age: 31 };
var userString = JSON.stringify(userJSON);
console.log(userString); //"{"name":"John","age":31}"
```

**4. Why do you need JSON?**

**Ans:** When exchanging data between a browser and a server, the data can only be text. Since JSON is text only, it can easily be sent to and from a server, and used as a data format by any programming language.

**[⬆ Back to Top](#table-of-contents)**

### <h2>Object and Map</h2>

**Objects** are similar to **Maps** in that both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. Due to this reason, Objects have been used as Maps historically. But there are important differences that make using a Map preferable in certain cases:

1. The keys of an Object can be Strings and Symbols, whereas they can be any value for a Map, including functions, objects, and any primitive. <br>
2. The keys in a Map are ordered while keys added to Object are not. Thus, when iterating over it, a Map object returns keys in the order of insertion. <br>
3. You can get the size of a Map easily with the size property, while the number of properties in an Object must be determined manually. <br>
4. A Map is an iterable and can thus be directly iterated, whereas iterating over an Object requires obtaining its keys in some fashion and iterating over them.
5. An Object has a prototype, so there are default keys in an object that could collide with your keys if you're not careful. As of ES5 this can be bypassed by creating an object(which can be called a map) using `Object.create(null)`, but this practice is seldom done. <br>
6. A Map may perform better in scenarios involving frequent addition and removal of key pairs. <br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>== and === operators</h2>

JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,

1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions. <br>
2. Two numbers are strictly equal when they are numerically equal, i.e., having the same number value. There are two special cases in this, <br>
   1. NaN is not equal to anything, including NaN. <br>
   2. Positive and negative zeros are equal to one another. <br>
3. Two Boolean operands are strictly equal if both are true or both are false. <br>
4. Two objects are strictly equal if they refer to the same Object. <br>
5. Null and Undefined types are not equal with ===, but equal with ==, i.e, <br>
   null===undefined --> false, but null==undefined --> true <br>

Some of the example which covers the above cases:

```javascript
0 == false   // true
0 === false  // false
1 == "1"     // true
1 === "1"    // false
null == undefined // true
null === undefined // false
'0' == false // true
'0' === false // false
[]==[] or []===[] //false, refer different objects in memory
{}=={} or {}==={} //false, refer different objects in memory
```
**[⬆ Back to Top](#table-of-contents)**

### <h2>var, let, and const</h2>

You can list out the differences in a tabular format

| var                                                    | let                                             | const                                  |
| ------------------------------------------------------ | ----------------------------------------------- | -------------------------------------- |
| Redeclare and reassign is possible                     | Redeclare not possible but reassign is possible | Redeclare and reassign is not possible |
| Global scope                                           | Block scope                                     | Block scope                            |
| It has been available from the beginning of JavaScript | Introduced as part of ES6                       | Introduced as part of ES6              |
| Global scope                                           | Block scope                                     | Block scope                            |
| Global scope                                           | Block scope                                     | Block scope                            |

**Examples:**

```javascript
var a = 10

var a = 11 // It is allowed

a = 12 // It is allowed
```
```javascript
let a = 10

let a = 11 // It is not allowed

a = 12 // It is allowed
```

```javascript
const a = 10

const a = 10 // It is not allowed

a = 10 // It is not allowed
```

**Questions and Answers**

**1. What is the purpose of the let keyword?**

**Ans:**

**2. What is the reason to choose the name let as a keyword?**

**Ans:** The `let` statement declares a **block scope local variable**. Hence the variables defined with let keyword are limited in scope to the block, statement, or expression on which it is used. Whereas variables declared with the `var` keyword used to define a variable globally, or locally to an entire function regardless of block scope.

Let's take an example to demonstrate the usage,

```javascript
let counter = 30;
if (counter === 30) {
let counter = 31;
console.log(counter); // 31
}
console.log(counter); // 30 (because the variable in if block won't exist here)
```

**3. Can I redeclare let and const variables?**

**Ans:** No, you cannot redeclare let and const variables. If you do, it throws below error

```bash
Uncaught SyntaxError: Identifier 'someVariable' has already been declared
```

**Explanation:** The variable declaration with `var` keyword refers to a function scope and the variable is treated as if it were declared at the top of the enclosing scope due to hoisting feature. So all the multiple declarations contributing to the same hoisted variable without any error. Let's take an example of re-declaring variables in the same scope for both var and let/const variables.

```javascript
var name = "John";
function myFunc() {
   var name = "Nick";
   var name = "Abraham"; // Re-assigned in the same function block
   alert(name); // Abraham
}
myFunc();
alert(name); // John
```

The block-scoped multi-declaration throws syntax error,

```javascript
let name = "John";
function myFunc() {
   let name = "Nick";
   let name = "Abraham"; // Uncaught SyntaxError: Identifier 'name' has already been declared
   alert(name);
}

myFunc();
alert(name);
```

**[⬆ Back to Top](#table-of-contents)**