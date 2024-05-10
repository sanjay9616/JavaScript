### Table of Contents

| No. | Questions                                                                                                                                                   |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are the possible ways to create objects in JavaScript](#What-are-the-possible-ways-to-create-objects-in-JavaScript)                                   |
| 2   | [What are the recommendations to create new object](#What-are-the-recommendations-to-create-new-object)                                                     |
| 3   | [What is the difference between native, host and user objects](#What-is-the-difference-between-native,-host-and-user-objects)                               |
| 4   | [What are wrapper objects](#What-are-wrapper-objects)                                                                                                       |
| 5   | [How do you compare two date objects](#How-do-you-compare-two-date-objects)                                                                                 |
| 6   | [How do you compare Object and Map](#How-do-you-compare-Object-and-Map)                                                                                     |
| 7   | [What are the differences between WeakMap and Map](#What-are-the-differences-between-WeakMap-and-Map)                                                       |
| 8   | [List down the collection of methods available on WeakMap](#List-down-the-collection-of-methods-available-on-WeakMap)                                       |
| 9   | [How do you map the array values without using map method](#How-do-you-map-the-array-values-without-using-map-method)                                       |
| 10  | [How do you check if a key exists in an object](#How-do-you-check-if-a-key-exists-in-an-object)                                                             |
| 11  | [How do you loop through or enumerate javascript object](#How-do-you-loop-through-or-enumerate-javascript-object)                                           |
| 12  | [How do you test for an empty object](#How-do-you-test-for-an-empty-object)                                                                                 |
| 13  | [What is an arguments object](#What-is-an-arguments-object)                                                                                                 |
| 14  | [How do you add a key value pair in javascript](#How-do-you-add-a-key-value-pair-in-javascript)                                                             |
| 15  | [How do you determine two values same or not using object](#How-do-you-determine-two-values-same-or-not-using-object)                                       |
| 16  | [What is the purpose of using object is method](#What-is-the-purpose-of-using-object-is-method)                                                             |
| 17  | [How do you copy properties from one object to other](#How-do-you-copy-properties-from-one-object-to-other)                                                 |
| 18  | [What are the applications of assign method](#What-are-the-applications-of-assign-method)                                                                   |
| 19  | [How do you get enumerable key and value pairs](#How-do-you-get-enumerable-key-and-value-pairs)                                                             |
| 20  | [What are the different ways to access object properties](#What-are-the-different-ways-to-access-object-properties)                                         |
| 21  | [How can you get the list of keys of any object](#How-can-you-get-the-list-of-keys-of-any-object)                                                           |
| 22  | [What is the main difference between Object.values and Object.entries method](#What-is-the-main-difference-between-Object.values-and-Object.entries-method) |
| 23  | [How do you list all properties of an object](#How-do-you-list-all-properties-of-an-object)                                                                 |
| 24  | [How do you define multiple properties on an object](#How-do-you-define-multiple-properties-on-an-object)                                                   |
| 25  | [What is an Intl object](#What-is-an-Intl-object)                                                                                                           |
| 26  | [What are the properties of Intl object](#What-are-the-properties-of-Intl-object)                                                                           |
| 27  | [What is an Iterator](#What-is-an-Iterator)                                                                                                                 |
| 28  | [How do you make an object iterable in javascript](#How-do-you-make-an-object-iterable-in-javascript)                                                       |
| 29  | [What is an object initializer](#What-is-an-object-initializer)                                                                                             |
| 30  | [What is a constructor method](#What-is-a-constructor-method)                                                                                               |
| 31  | [What happens if you write constructor more than once in a class](#What-happens-if-you-write-constructor-more-than-once-in-a-class)                         |
| 32  | [How do you call the constructor of a parent class](#How-do-you-call-the-constructor-of-a-parent-class)                                                     |
| 33  | [How do you get property descriptors of an object](#How-do-you-get-property-descriptors-of-an-object)                                                       |
| 34  | [What are the attributes provided by a property descriptor](#What-are-the-attributes-provided-by-a-property-descriptor)                                     |

### <h2>What are the possible ways to create objects in JavaScript</h2>

There are many ways to create objects in javascript as mentioned below:

**1. Object literal syntax:**

```javascript
var object = {
      name: "Sudheer",
      age: 34
};

Object literal property values can be of any data type, including array, function, and nested object.
```

**Note:** This is one of the easiest ways to create an object.

**2. Object constructor:**

The simplest way to create an empty object is using the `Object` constructor. Currently this approach is not recommended.

```javascript
var object = new Object();
```

The `Object()` is a built-in constructor function so "new" keyword is not required. The above code snippet can be re-written as:

```javascript
var object = Object();
```

**3. Object's create method:**

The create method of Object is used to create a new object by passing the specificied prototype object and properties as arguments, i.e., this pattern is helpful to create new objects based on existing objects.
The second argument is optional and it is used to create properties on a newly created object.

The following code creates a new empty object whose prototype is null.

```javascript
var object = Object.create(null);
```

**4. Function constructor:**

In this approach, create any function and apply the new operator to create object instances.

```javascript
function Person(name) {
   this.name = name;
   this.age = 21;
}
var object = new Person("Sudheer");
```

**5. Function constructor with prototype:**

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

**6. ES6 Class syntax:**

ES6 introduces class feature to create objects.

```javascript
class Person {
   constructor(name) {
      this.name = name;
   }
}

var object = new Person("Sudheer");
```

**7. Singleton pattern:**

A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance. This way one can ensure that they don't accidentally create multiple instances.

```javascript
var object = new (function () {
   this.name = "Sudheer";
})();
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the recommendations to create new object</h2>

It is recommended to avoid creating new objects using `new Object()`. Instead you can initialize values based on it's type to create the objects.

1. Assign {} instead of new Object() </br>
2. Assign "" instead of new String() </br>
3. Assign 0 instead of new Number() </br>
4. Assign false instead of new Boolean() </br>
5. Assign [] instead of new Array() </br>
6. Assign /()/ instead of new RegExp() </br>
7. Assign function (){} instead of new Function() </br>

You can define them as an example,

```javascript
var v1 = {};
var v2 = "";
var v3 = 0;
var v4 = false;
var v5 = [];
var v6 = /()/;
var v7 = function () {};
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between native, host and user objects</h2>

`Native objects` are objects that are part of the JavaScript language defined by the ECMAScript specification. For example, String, Math, RegExp, Object, Function etc core objects defined in the ECMAScript spec. </br>
`Host objects` are objects provided by the browser or runtime environment (Node). For example, window, XmlHttpRequest, DOM nodes etc are considered as host objects. </br>
`User objects` are objects defined in the javascript code. For example, User objects created for profile information.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are wrapper objects</h2>

Primitive Values like string,number and boolean don't have properties and methods but they are temporarily converted or coerced to an object(Wrapper object) when you try to perform actions on them. For example, if you apply toUpperCase() method on a primitive string value, it does not throw an error but returns uppercase of the string.

```javascript
let name = "john";
console.log(name.toUpperCase()); // Behind the scenes treated as console.log(new String(name).toUpperCase());
```

i.e, Every primitive except null and undefined have Wrapper Objects and the list of wrapper objects are String,Number,Boolean,Symbol and BigInt.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you compare two date objects</h2>

You need to use date.getTime() method to compare date values instead of comparison operators (==, !=, ===, and !== operators)

```javascript
var d1 = new Date();
var d2 = new Date(d1);
console.log(d1.getTime() === d2.getTime()); //True
console.log(d1 === d2); // False
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you compare Object and Map</h2>

**Objects** are similar to **Maps** in that both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. Due to this reason, Objects have been used as Maps historically. But there are important differences that make using a Map preferable in certain cases:

1. The keys of an Object can be Strings and Symbols, whereas they can be any value for a Map, including functions, objects, and any primitive. </br>
2. The keys in a Map are ordered while keys added to Object are not. Thus, when iterating over it, a Map object returns keys in the order of insertion.</br>
3. You can get the size of a Map easily with the size property, while the number of properties in an Object must be determined manually.</br>
4. A Map is an iterable and can thus be directly iterated, whereas iterating over an Object requires obtaining its keys in some fashion and iterating over them.</br>
5. An Object has a prototype, so there are default keys in an object that could collide with your keys if you're not careful. As of ES5 this can be bypassed by creating an object(which can be called a map) using `Object.create(null)`, but this practice is seldom done.</br>
6. A Map may perform better in scenarios involving frequent addition and removal of key pairs.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between WeakMap and Map</h2>

The main difference is that references to key objects in Map are strong while references to key objects in WeakMap are weak. i.e, A key object in WeakMap can be garbage collected if there is no other reference to it.
Other differences are,

1. Maps can store any key type Whereas WeakMaps can store only collections of key objects </br>
2. WeakMap does not have size property unlike Map</br>
3. WeakMap does not have methods such as clear, keys, values, entries, forEach.</br>
4. WeakMap is not iterable.

**[⬆ Back to Top](#table-of-contents)**

### <h2>List down the collection of methods available on WeakMap</h2>

Below are the list of methods available on WeakMap,

1. set(key, value): Sets the value for the key in the WeakMap object. Returns the WeakMap object. </br>
2. delete(key): Removes any value associated to the key. </br>
3. has(key): Returns a Boolean asserting whether a value has been associated to the key in the WeakMap object or not. </br>
4. get(key): Returns the value associated to the key, or undefined if there is none. </br>
  Let's see the functionality of all the above methods in an example,

```javascript
var weakMapObject = new WeakMap();
var firstObject = {};
var secondObject = {};
// set(key, value)
weakMapObject.set(firstObject, "John");
weakMapObject.set(secondObject, 100);
console.log(weakMapObject.has(firstObject)); //true
console.log(weakMapObject.get(firstObject)); // John
weakMapObject.delete(secondObject);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you map the array values without using map method</h2>

You can map the array values without using the `map` method by just using the `from` method of Array. Let's map city names from Countries array,

```javascript
const countries = [
    { name: "India", capital: "Delhi" },
    { name: "US", capital: "Washington" },
    { name: "Russia", capital: "Moscow" },
    { name: "Singapore", capital: "Singapore" },
    { name: "China", capital: "Beijing" },
    { name: "France", capital: "Paris" },
];

const cityNames = Array.from(countries, ({ capital }) => capital);
console.log(cityNames); // ['Delhi, 'Washington', 'Moscow', 'Singapore', 'Beijing', 'Paris']
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check if a key exists in an object</h2>

You can check whether a key exists in an object or not using three approaches,

1. **Using in operator:** You can use the in operator whether a key exists in an object or not

```javascript
"key" in obj;
```

and If you want to check if a key doesn't exist, remember to use parenthesis,

```javascript
!("key" in obj);
```

2. **Using hasOwnProperty method:** You can use `hasOwnProperty` to particularly test for properties of the object instance (and not inherited properties)

```javascript
obj.hasOwnProperty("key"); // true
```

3. **Using undefined comparison:** If you access a non-existing property from an object, the result is undefined. Let’s compare the properties against undefined to determine the existence of the property.

```javascript
const user = {
 name: "John",
};

console.log(user.name !== undefined); // true
console.log(user.nickName !== undefined); // false
```
4. **Using Object.keys(Obj):**

```javascript
console.log(Object.keys(user).includes('name')); // true
console.log(!Object.keys(user).includes('name')); // false
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you loop through or enumerate javascript object</h2>

You can use the `for-in` loop to loop through javascript object. You can also make sure that the key you get is an actual property of an object, and doesn't come from the prototype using `hasOwnProperty` method.

```javascript
var object = {
    k1: "value1",
    k2: "value2",
    k3: "value3",
};

for (var key in object) {
    if (object.hasOwnProperty(key)) {
        console.log(key + " -> " + object[key]); // k1 -> value1 ...
    }
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you test for an empty object</h2>

There are different solutions based on ECMAScript versions

1. **Using Object entries(ECMA 7+):** You can use object entries length along with constructor type.

```javascript
Object.entries(obj).length === 0 && obj.constructor === Object; // Since date object length is 0, you need to check constructor check as well
```

1. **Using Object keys(ECMA 5+):** You can use object keys length along with constructor type.

```javascript
Object.keys(obj).length === 0 && obj.constructor === Object; // Since date object length is 0, you need to check constructor check as well
```

1. **Using for-in with hasOwnProperty(Pre-ECMA 5):** You can use a for-in loop along with hasOwnProperty.

```javascript
function isEmpty(obj) {
 for (var prop in obj) {
   if (obj.hasOwnProperty(prop)) {
     return false;
   }
 }

 return JSON.stringify(obj) === JSON.stringify({});
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an arguments object</h2>

The arguments object is an Array-like object accessible inside functions that contains the values of the arguments passed to that function. For example, let's see how to use arguments object inside sum function,

```javascript
function sum() {
var total = 0;
for (var i = 0, len = arguments.length; i < len; ++i) {
    total += arguments[i];
}
return total;
}

sum(1, 2, 3); // returns 6
```

**Note:** You can't apply array methods on arguments object. But you can convert into a regular array as below.

```javascript
var argsArray = Array.prototype.slice.call(arguments);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you add a key value pair in javascript</h2>

There are two possible solutions to add new properties to an object. Let's take a simple object to explain these solutions.

```javascript
var object = {
    key1: value1,
    key2: value2,
};
```

1. **Using dot notation:** This solution is useful when you know the name of the property

```javascript
object.key3 = "value3";
```

1. **Using square bracket notation:** This solution is useful when the name of the property is dynamically determined.

```javascript
obj["key3"] = "value3";
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you determine two values same or not using object</h2>

The Object.is() method determines whether two values are the same value. For example, the usage with different types of values would be,

```javascript
Object.is("hello", "hello"); // true
Object.is(window, window); // true
Object.is([], []); // false
```

Two values are the same if one of the following holds:

1. both undefined </br>
2. both null </br>
3. both true or both false </br>
4. both strings of the same length with the same characters in the same order </br>
5. both the same object (means both object have same reference) </br>
6. both numbers and </br>
both +0 </br>
both -0 </br>
both NaN </br>
both non-zero and both not NaN and both have the same value.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of using object is method</h2>

Some of the applications of Object's `is` method are follows,

1. It is used for comparison of two strings. </br>
2. It is used for comparison of two numbers. </br>
3. It is used for comparing the polarity of two numbers. </br>
4. It is used for comparison of two objects. </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you copy properties from one object to other</h2>

You can use the Object.assign() method which is used to copy the values and properties from one or more source objects to a target object. It returns the target object which has properties and values copied from the source objects. The syntax would be as below,

```javascript
Object.assign(target, ...sources);
```

Let's take example with one source and one target object,

```javascript
const target = { a: 1, b: 2 };
const source = { b: 3, c: 4 };

const returnedTarget = Object.assign(target, source);

console.log(target); // { a: 1, b: 3, c: 4 }

console.log(returnedTarget); // { a: 1, b: 3, c: 4 }
```

As observed in the above code, there is a common property(`b`) from source to target so it's value has been overwritten.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the applications of assign method</h2>

Below are the some of main applications of Object.assign() method,

1. It is used for cloning an object. </br>
2. It is used to merge objects with the same properties.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you get enumerable key and value pairs</h2>

The Object.entries() method is used to return an array of a given object's own enumerable string-keyed property [key, value] pairs, in the same order as that provided by a for...in loop. Let's see the functionality of object.entries() method in an example,

```javascript
const object = {
    a: "Good morning",
    b: 100,
};

for (let [key, value] of Object.entries(object)) {
    console.log(`${key}: ${value}`); // a: 'Good morning'
    // b: 100
}
```

**Note:** The order is not guaranteed as object defined.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the different ways to access object properties</h2>

There are 3 possible ways for accessing the property of an object.

1. **Dot notation:** It uses dot for accessing the properties

```javascript
objectName.property;
```

1. **Square brackets notation:** It uses square brackets for property access

```javascript
objectName["property"];
```

1. **Expression notation:** It uses expression in the square brackets

```javascript
objectName[expression];
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How can you get the list of keys of any object</h2>

You can use the `Object.keys()` method which is used to return an array of a given object's own property names, in the same order as we get with a normal loop. For example, you can get the keys of a user object,

```javascript
const user = {
    name: "John",
    gender: "male",
    age: 40,
};

console.log(Object.keys(user)); //['name', 'gender', 'age']
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the main difference between Object.values and Object.entries method</h2>

The Object.values() method's behavior is similar to Object.entries() method but it returns an array of values instead [key,value] pairs.

```javascript
const object = {
    a: "Good morning",
    b: 100,
};

for (let value of Object.values(object)) {
    console.log(`${value}`); // 'Good morning'
    100;
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you list all properties of an object</h2>

You can use the `Object.getOwnPropertyNames()` method which returns an array of all properties found directly in a given object. Let's the usage of it in an example,

```javascript
const newObject = {
    a: 1,
    b: 2,
    c: 3,
};

console.log(Object.getOwnPropertyNames(newObject));
["a", "b", "c"];
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you define multiple properties on an object</h2>

The `Object.defineProperties()` method is used to define new or modify existing properties directly on an object and returning the object. Let's define multiple properties on an empty object,

```javascript
const newObject = {};

Object.defineProperties(newObject, {
newProperty1: {
    value: "John",
    writable: true,
},
newProperty2: {},
});
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an Intl object</h2>

The Intl object is the namespace for the ECMAScript Internationalization API, which provides language sensitive string comparison, number formatting, and date and time formatting. It provides access to several constructors and language sensitive functions.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the properties of Intl object</h2>

Below are the list of properties available on Intl object,

1. **Collator:** These are the objects that enable language-sensitive string comparison. </br>
2. **DateTimeFormat:** These are the objects that enable language-sensitive date and time formatting. </br>
3. **ListFormat:** These are the objects that enable language-sensitive list formatting. </br>
4. **NumberFormat:** Objects that enable language-sensitive number formatting. </br>
5. **PluralRules:** Objects that enable plural-sensitive formatting and language-specific rules for plurals. </br>
6. **RelativeTimeFormat:** Objects that enable language-sensitive relative time formatting.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an Iterator</h2>

An iterator is an object which defines a sequence and a return value upon its termination. It implements the Iterator protocol with a `next()` method which returns an object with two properties: `value` (the next value in the sequence) and `done` (which is true if the last value in the sequence has been consumed).

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you make an object iterable in javascript</h2>

By default, plain objects are not iterable. But you can make the object iterable by defining a `Symbol.iterator` property on it.

Let's demonstrate this with an example,

```javascript
const collection = {
one: 1,
two: 2,
three: 3,
[Symbol.iterator]() {
    const values = Object.keys(this);
    let i = 0;
    return {
    next: () => {
        return {
        value: this[values[i++]],
        done: i > values.length,
        };
    },
    };
},
};

const iterator = collection[Symbol.iterator]();

console.log(iterator.next()); // → {value: 1, done: false}
console.log(iterator.next()); // → {value: 2, done: false}
console.log(iterator.next()); // → {value: 3, done: false}
console.log(iterator.next()); // → {value: undefined, done: true}
```

The above process can be simplified using a generator function,

```javascript
const collection = {
one: 1,
two: 2,
three: 3,
[Symbol.iterator]: function* () {
    for (let key in this) {
    yield this[key];
    }
},
};
const iterator = collection[Symbol.iterator]();
console.log(iterator.next()); // {value: 1, done: false}
console.log(iterator.next()); // {value: 2, done: false}
console.log(iterator.next()); // {value: 3, done: false}
console.log(iterator.next()); // {value: undefined, done: true}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an object initializer</h2>

An object initializer is an expression that describes the initialization of an Object. The syntax for this expression is represented as a comma-delimited list of zero or more pairs of property names and associated values of an object, enclosed in curly braces ({}). This is also known as literal notation. It is one of the ways to create an object.

```javascript
var initObject = { a: "John", b: 50, c: {} };

console.log(initObject.a); // John
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a constructor method</h2>

The constructor method is a special method for creating and initializing an object created within a class. If you do not specify a constructor method, a default constructor is used. The example usage of constructor would be as below,

```javascript
class Employee {
    constructor() {
        this.name = "John";
    }
}

var employeeObject = new Employee();

console.log(employeeObject.name); // John
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What happens if you write constructor more than once in a class</h2>

The "constructor" in a class is a special method and it should be defined only once in a class. i.e, If you write a constructor method more than once in a class it will throw a `SyntaxError` error.

```javascript
class Employee {
    constructor() {
        this.name = "John";
    }
    constructor() {   //  Uncaught SyntaxError: A class may only have one constructor
        this.age = 30;
    }
}

var employeeObject = new Employee();

console.log(employeeObject.name);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you call the constructor of a parent class</h2>

You can use the `super` keyword to call the constructor of a parent class. Remember that `super()` must be called before using 'this' reference. Otherwise it will cause a reference error. Let's the usage of it,

```javascript
class Square extends Rectangle {
    constructor(length) {
        super(length, length);
        this.name = "Square";
    }

    get area() {
        return this.width * this.height;
    }

    set area(value) {
        this.area = value;
    }
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you get property descriptors of an object</h2>

You can use the `Object.getOwnPropertyDescriptors()` method which returns all own property descriptors of a given object. The example usage of this method is below,

```javascript
const newObject = {
a: 1,
b: 2,
c: 3,
};
const descriptorsObject = Object.getOwnPropertyDescriptors(newObject);
console.log(descriptorsObject.a.writable); //true
console.log(descriptorsObject.a.configurable); //true
console.log(descriptorsObject.a.enumerable); //true
console.log(descriptorsObject.a.value); // 1
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the attributes provided by a property descriptor</h2>

A property descriptor is a record which has the following attributes

1. value: The value associated with the property </br>
2. writable: Determines whether the value associated with the property can be changed or not </br>
3. configurable: Returns true if the type of this property descriptor can be changed and if the property can be deleted from the corresponding object. </br>
4. enumerable: Determines whether the property appears during enumeration of the properties on the corresponding object or not. </br>
5. set: A function which serves as a setter for the property </br>
6. get: A function which serves as a getter for the property

**[⬆ Back to Top](#table-of-contents)**
