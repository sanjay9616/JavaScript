### Table of Contents

| No. | Questions                                                           |
| --- | ------------------------------------------------------------------- |
| 1   | [Possible ways to create objects](#Possible-ways-to-create-objects) |
| 2   | [Prototype](#Prototype)                                             |

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

**Note**: The **syntax** to add the property to an object constructor function is: **objectConstructorName.prototype.key = 'value';**

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

**[⬆ Back to Top](#table-of-contents)**



