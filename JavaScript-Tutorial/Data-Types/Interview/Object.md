### Table of Contents

| No. | Questions                                                                                                                     |
| --- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are the possible ways to create objects in JavaScript](#What-are-the-possible-ways-to-create-objects-in-JavaScript)     |
| 2   | [What are the recommendations to create new object](#What-are-the-recommendations-to-create-new-object)                       |
| 3   | [What is the difference between native, host and user objects](#What-is-the-difference-between-native,-host-and-user-objects) |
| 4   | [What are wrapper objects](#What-are-wrapper-objects)                                                                         |
| 5   | [How do you compare two date objects](#How-do-you-compare-two-date-objects)                                                   |
| 6   | [How do you compare Object and Map](#How-do-you-compare-Object-and-Map)                                                       |
| 7   | [What are the differences between WeakMap and Map](#What-are-the-differences-between-WeakMap-and-Map)                         |
| 8   | [List down the collection of methods available on WeakMap](#List-down-the-collection-of-methods-available-on-WeakMap)         |
| 9   | [How do you map the array values without using map method](#How-do-you-map-the-array-values-without-using-map-method)         |

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
