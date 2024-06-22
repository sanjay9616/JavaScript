<h1>JavaScript ES5 Object Methods</h1>

<h2>JavaScript Object Management</h2>

```javascript
Object.create() // Create object with an existing object as prototype
Object.defineProperty(object, property, descriptor) // Adding or changing value of a property
Object.defineProperties(object, descriptors) // Adding or changing object properties
Object.getOwnPropertyDescriptor(object, property) // Accessing Properties
Object.getOwnPropertyNames(object) // Returns all properties as an array
Object.getPrototypeOf(object) // Accessing the prototype
Object.keys(object) // Returns enumerable properties as an array
```
<h3>Examples</h3>

```javascript
const person = { firstName: "John", lastName : "Doe", language : "EN" };
Object.defineProperty(person, "language", {value : "NO"}); // Change value of a property
console.log(person) // { firstName: 'John', lastName: 'Doe', language: 'NO' }

const person = { firstName: "John", lastName : "Doe", language : "EN" };
Object.defineProperty(person, "year", {value:"2008"}); // Add a property
console.log(person) // { firstName: 'John', lastName: 'Doe', language: 'EN' }
console.log(person.year) // 2008

const person = {firstName:"John", lastName:"Doe"};
Object.defineProperty(person, "fullName", { // // Define a getter
  get: function () {return this.firstName + " " + this.lastName;}
});
console.log(person.fullName) // John Doe
```

<h2>JavaScript Object Protection</h2>

```javascript
Object.preventExtensions(object) // Prevents adding properties to an object
Object.isExtensible(object) // Returns true if properties can be added to an object

Object.seal(object) // Prevents changes of object properties (not values)
Object.isSealed(object) // Returns true if object is sealed

Object.freeze(object) // Prevents any changes to an object
Object.isFrozen(object) // Returns true if object is frozen
```

<h2>Changing Meta Data</h2>

```javascript
writable : true      // Property value can be changed
enumerable : true    // Property can be enumerated
configurable : true  // Property can be reconfigured

writable : false     // Property value can not be changed
enumerable : false   // Property can be not enumerated
configurable : false // Property can be not reconfigured

Object.defineProperty(person, "language", {writable:false}); // This example makes language read-only
Object.defineProperty(person, "language", {enumerable:false}); // This example makes language not enumerable
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>
