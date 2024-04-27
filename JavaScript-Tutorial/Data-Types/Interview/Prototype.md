### Table of Contents

| No. | Questions                                                                                                                 |
| --- | ------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you set prototype of one object to another](#How-do-you-set-prototype-of-one-object-to-another)                   |
| 2   | [How do you create an object with prototype](#How-do-you-create-an-object-with-prototype)                                 |
| 3   | [How do you get the prototype of an object](#How-do-you-get-the-prototype-of-an-object)                                   |
| 4   | [What happens If I pass string type for getPrototype method](#What-happens-If-I-pass-string-type-for-getPrototype-method) |
| 5   | [Do all objects have prototypes](#Do-all-objects-have-prototypes)                                                         |
| 6   | [What is the difference between proto and prototype](#What-is-the-difference-between-proto-and-prototype)                 |

### <h2>How do you set prototype of one object to another</h2>

You can use the `Object.setPrototypeOf()` method that sets the prototype (i.e., the internal `Prototype` property) of a specified object to another object or null. For example, if you want to set prototype of a square object to rectangle object would be as follows,

```javascript
Object.setPrototypeOf(Square.prototype, Rectangle.prototype);
Object.setPrototypeOf({}, null);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you create an object with prototype</h2>

The Object.create() method is used to create a new object with the specified prototype object and properties. i.e, It uses an existing object as the prototype of the newly created object. It returns a new object with the specified prototype object and properties.

```javascript
const user = {
    name: "John",
    printInfo: function () {
        console.log(`My name is ${this.name}.`);
    },
};

const admin = Object.create(user);

admin.name = "Nick"; // Remember that "name" is a property set on "admin" but not on "user" object

admin.printInfo(); // My name is Nick
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you get the prototype of an object</h2>

You can use the `Object.getPrototypeOf(obj)` method to return the prototype of the specified object. i.e. The value of the internal `prototype` property. If there are no inherited properties then `null` value is returned.

```javascript
const newPrototype = {};
const newObject = Object.create(newPrototype);

console.log(Object.getPrototypeOf(newObject) === newPrototype); // true
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What happens If I pass string type for getPrototype method</h2>

In ES5, it will throw a TypeError exception if the obj parameter isn't an object. Whereas in ES2015, the parameter will be coerced to an `Object`.

```javascript
// ES5
Object.getPrototypeOf("James"); // TypeError: "James" is not an object
// ES2015
Object.getPrototypeOf("James"); // String.prototype
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Do all objects have prototypes</h2>

No. All objects have prototypes except for the base object which is created by the user, or an object that is created using the new keyword.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between proto and prototype</h2>

The `__proto__` object is the actual object that is used in the lookup chain to resolve methods, etc. Whereas `prototype` is the object that is used to build `__proto__` when you create an object with new.

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