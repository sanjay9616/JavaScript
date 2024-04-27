### Table of Contents

| No. | Questions                                                                                                                     |
| --- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is a freeze method](#What-is-a-freeze-method)                                                                           |
| 2   | [What is the purpose of freeze method](#What-is-the-purpose-of-freeze-method)                                                 |
| 3   | [Why do I need to use freeze method](#Why-do-I-need-to-use-freeze-method)                                                     |
| 4   | [How do you determine whether object is frozen or not](#How-do-you-determine-whether-object-is-frozen-or-not)                 |
| 5   | [What is a proxy object](#What-is-a-proxy-object)                                                                             |
| 6   | [What is the purpose of seal method](#What-is-the-purpose-of-seal-method)                                                     |
| 7   | [What are the applications of seal method](#What-are-the-applications-of-seal-method)                                         |
| 8   | [How do you determine if an object is sealed or not](#How-do-you-determine-if-an-object-is-sealed-or-not)                     |
| 9   | [What are the differences between freeze and seal methods](#What-are-the-differences-between-freeze-and-seal-methods)         |
| 10  | [What are javascript accessors](#What-are-javascript-accessors)                                                               |
| 11  | [How do you define property on Object constructor](#How-do-you-define-property-on-Object-constructor)                         |
| 12  | [What is the difference between get and defineProperty](#What-is-the-difference-between-get-and-defineProperty)               |
| 13  | [What are the advantages of Getters and Setters](#What-are-the-advantages-of-Getters-and-Setters)                             |
| 14  | [Can I add getters and setters using defineProperty method](#Can-I-add-getters-and-setters-using-defineProperty-method)       |
| 15  | [How do you check whether an object can be extendable or not](#How-do-you-check-whether-an-object-can-be-extendable-or-not)   |
| 16  | [How do you prevent an object to extend](#How-do-you-prevent-an-object-to-extend)                                             |
| 17  | [What are the different ways to make an object non-extensible](#What-are-the-different-ways-to-make-an-object-non-extensible) |
| 18  | [What is ES6](#What-is-ES6)                                                                                                   |
| 19  | [What are classes in ES6](#What-are-classes-in-ES6)                                                                           |
| 20  | [List down some of the features of ES6](#List-down-some-of-the-features-of-ES6)                                               |

### <h2>What is a freeze method</h2>

The **freeze()** method is used to freeze an object. Freezing an object does not allow adding new properties to an object,prevents from removing and prevents changing the enumerability, configurability, or writability of existing properties. i.e, It returns the passed object and does not create a frozen copy.

```javascript
const obj = {
    prop: 100,
};

Object.freeze(obj);
obj.prop = 200; // Throws an error in strict mode

console.log(obj.prop); //100
```

Remember freezing is only applied to the top-level properties in objects but not for nested objects.
For example, let's try to freeze user object which has employment details as nested object and observe that details have been changed.

```javascript
const user = {
    name: "John",
    employment: {
        department: "IT",
    },
};

Object.freeze(user);
user.employment.department = "HR";
```

**Note:** It causes a TypeError if the argument passed is not an object.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of freeze method</h2>

Below are the main benefits of using freeze method,

1. It is used for freezing objects and arrays. </br>
2. It is used to make an object immutable.

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do I need to use freeze method</h2>

In the Object-oriented paradigm, an existing API contains certain elements that are not intended to be extended, modified, or re-used outside of their current context. Hence it works as the `final` keyword which is used in various languages.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you determine whether object is frozen or not</h2>

Object.isFrozen() method is used to determine if an object is frozen or not.An object is frozen if all of the below conditions hold true,

1. If it is not extensible.
2. If all of its properties are non-configurable.
3. If all its data properties are non-writable.
  The usage is going to be as follows,

```javascript
const object = {
 property: "Welcome JS world",
};
Object.freeze(object);
console.log(Object.isFrozen(object));
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a proxy object</h2>

The Proxy object is used to define custom behavior for fundamental operations such as property lookup, assignment, enumeration, function invocation, etc. The syntax would be as follows,

```javascript
var p = new Proxy(target, handler);
```

Let's take an example of proxy object,

```javascript
var handler = {
    get: function (obj, prop) {
        return prop in obj ? obj[prop] : 100;
    },
};

var p = new Proxy({}, handler);
p.a = 10;
p.b = null;

console.log(p.a, p.b); // 10, null
console.log("c" in p, p.c); // false, 100
```

In the above code, it uses `get` handler which define the behavior of the proxy when an operation is performed on it

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of seal method</h2>

The **Object.seal()** method is used to seal an object, by preventing new properties from being added to it and marking all existing properties as non-configurable. But values of present properties can still be changed as long as they are writable. Let's see the below example to understand more about seal() method

```javascript
const object = {
    property: "Welcome JS world",
};
Object.seal(object);
object.property = "Welcome to object world";
console.log(Object.isSealed(object)); // true
delete object.property; // You cannot delete when sealed
console.log(object.property); //Welcome to object world
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the applications of seal method<h2>

Below are the main applications of Object.seal() method,

1. It is used for sealing objects and arrays. </br>
2. It is used to make an object immutable.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you determine if an object is sealed or not</h2>

The Object.isSealed() method is used to determine if an object is sealed or not. An object is sealed if all of the below conditions hold true

1. If it is not extensible. </br>
2. If all of its properties are non-configurable. </br>
3. If it is not removable (but not necessarily non-writable).
  Let's see it in the action

```javascript
const object = {
 property: "Hello, Good morning",
};

Object.seal(object); // Using seal() method to seal the object

console.log(Object.isSealed(object)); // checking whether the object is sealed or not
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between freeze and seal methods</h2>

If an object is frozen using the Object.freeze() method then its properties become immutable and no changes can be made in them whereas if an object is sealed using the Object.seal() method then the changes can be made in the existing properties of the object.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are javascript accessors</h2>

ECMAScript 5 introduced javascript object accessors or computed properties through getters and setters. Getters uses the `get` keyword whereas Setters uses the `set` keyword.

```javascript
var user = {
    firstName: "John",
    lastName: "Abraham",
    language: "en",
    get lang() {
        return this.language;
    },
    set lang(lang) {
        this.language = lang;
    },
};
console.log(user.lang); // getter access lang as en
user.lang = "fr";
console.log(user.lang); // setter used to set lang as fr
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you define property on Object constructor</h2>

The Object.defineProperty() static method is used to define a new property directly on an object, or modify an existing property on an object, and returns the object. Let's see an example to know how to define property,

```javascript
const newObject = {};

Object.defineProperty(newObject, "newProperty", {
    value: 100,
    writable: false,
});

console.log(newObject.newProperty); // 100

newObject.newProperty = 200; // It throws an error in strict mode due to writable setting
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between get and defineProperty</h2>

Both have similar results until unless you use classes. If you use `get` the property will be defined on the prototype of the object whereas using `Object.defineProperty()` the property will be defined on the instance it is applied to.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the advantages of Getters and Setters</h2>

Below are the list of benefits of Getters and Setters,

1. They provide simpler syntax </br>
2. They are used for defining computed properties, or accessors in JS. </br>
3. Useful to provide equivalence relation between properties and methods </br>
4. They can provide better data quality </br>
5. Useful for doing things behind the scenes with the encapsulated logic. </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>Can I add getters and setters using defineProperty method</h2>

Yes, You can use the `Object.defineProperty()` method to add Getters and Setters. For example, the below counter object uses increment, decrement, add and subtract properties,

```javascript
var obj = { counter: 0 };

// Define getters
Object.defineProperty(obj, "increment", {
    get: function () {
        this.counter++;
    },
});
Object.defineProperty(obj, "decrement", {
    get: function () {
        this.counter--;
    },
});

// Define setters
Object.defineProperty(obj, "add", {
    set: function (value) {
        this.counter += value;
    },
});
Object.defineProperty(obj, "subtract", {
    set: function (value) {
        this.counter -= value;
    },
});

obj.add = 10;
obj.subtract = 5;
console.log(obj.increment); //6
console.log(obj.decrement); //5
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check whether an object can be extendable or not</h2>

The `Object.isExtensible()` method is used to determine if an object is extendable or not. i.e, Whether it can have new properties added to it or not.

```javascript
const newObject = {};
console.log(Object.isExtensible(newObject)); //true
```

**Note:** By default, all the objects are extendable. i.e, The new properties can be added or modified.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you prevent an object to extend</h2>

The `Object.preventExtensions()` method is used to prevent new properties from ever being added to an object. In other words, it prevents future extensions to the object. Let's see the usage of this property,

```javascript
const newObject = {};
Object.preventExtensions(newObject); // NOT extendable

try {
Object.defineProperty(newObject, "newProperty", {
    // Adding new property
    value: 100,
});
} catch (e) {
console.log(e); // TypeError: Cannot define property newProperty, object is not extensible
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the different ways to make an object non-extensible</h2>

You can mark an object non-extensible in 3 ways,

1. Object.preventExtensions </br>
2. Object.seal </br>
3. Object.freeze

```javascript
var newObject = {};

Object.preventExtensions(newObject); // Prevent objects are non-extensible
Object.isExtensible(newObject); // false

var sealedObject = Object.seal({}); // Sealed objects are non-extensible
Object.isExtensible(sealedObject); // false

var frozenObject = Object.freeze({}); // Frozen objects are non-extensible
Object.isExtensible(frozenObject); // false
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is ES6</h2>

ES6 is the sixth edition of the javascript language and it was released in June 2015. It was initially known as ECMAScript 6 (ES6) and later renamed to ECMAScript 2015. Almost all the modern browsers support ES6 but for the old browsers there are many transpilers, like Babel.js etc.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are classes in ES6</h2>

In ES6, Javascript classes are primarily syntactic sugar over JavaScript’s existing prototype-based inheritance.
For example, the prototype based inheritance written in function expression as below,

```javascript
function Bike(model, color) {
    this.model = model;
    this.color = color;
}

Bike.prototype.getDetails = function () {
    return this.model + " bike has" + this.color + " color";
};
```

Whereas ES6 classes can be defined as an alternative

```javascript
class Bike {
    constructor(color, model) {
        this.color = color;
        this.model = model;
    }

    getDetails() {
        return this.model + " bike has" + this.color + " color";
    }
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>List down some of the features of ES6</h2>

Below are the list of some new features of ES6,

1. Support for constants or immutable variables </br>
2. Block-scope support for variables, constants and functions </br>
3. Arrow functions </br>
4. Default parameters </br>
5. Rest and Spread Parameters </br>
6. Template Literals </br>
7. Multi-line Strings </br>
8. Destructuring Assignment </br>
9. Enhanced Object Literals </br>
10. Promises </br>
11. Classes </br>
12. Modules </br>

**[⬆ Back to Top](#table-of-contents)**
