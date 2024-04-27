### Table of Contents

| No. | Questions                                                                                           |
| --- | --------------------------------------------------------------------------------------------------- |
| 1   | [Questions based on Objects and Map](#Questions-based-on-Objects-and-Map)                           |
| 3   | [Call, Apply and Bind](#Call-Apply-and-Bind)                                                        |
| 7   | [== and === operators](#==-and-===-operators)                                                       |
| 9   | [How do you decode or encode a URL in JavaScript](#How-do-you-decode-or-encode-a-URL-in-JavaScript) |
| 10  | [localStorage, sessionStorage, and Cookie](#localStorage-sessionStorage-and-Cookie)                 |

### <h1>Questions based on Objects and Map</h1>

**Object:** The keys of an Object must be either a String or a Symbol. (add theorey)

**Map:** A Map 's keys can be any value (including functions, objects, or any primitive). (add theorey)

**WeakMap:** The WeakMap object is a collection of key/value pairs in which the keys are weakly referenced. In this case, keys must be objects and the values can be arbitrary values. The syntax is looking like as below,

```javascript
new WeakMap([iterable]);
```

Let's see the below example to explain it's behavior,

```javascript
var ws = new WeakMap();
var user = {};
ws.set(user);
ws.has(user); // true
ws.delete(user); // removes user from the map
ws.has(user); // false, user has been removed
```

<h2>Questions and Answers:</h2>

**1. What are the possible ways to create objects in JavaScript?**

**Ans:** There are many ways to create objects in javascript as mentioned below:

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

**2. What are the recommendations to create new object?**

**Ans:** It is recommended to avoid creating new objects using `new Object()`. Instead you can initialize values based on it's type to create the objects.

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

**3. What is the difference between native, host and user objects?**

**Ans:** `Native objects` are objects that are part of the JavaScript language defined by the ECMAScript specification. For example, String, Math, RegExp, Object, Function etc core objects defined in the ECMAScript spec.
`Host objects` are objects provided by the browser or runtime environment (Node). For example, window, XmlHttpRequest, DOM nodes etc are considered as host objects.
`User objects` are objects defined in the javascript code. For example, User objects created for profile information.

**4. How do you compare two date objects?**

**Ans:** You need to use date.getTime() method to compare date values instead of comparison operators (==, !=, ===, and !== operators)

```javascript
var d1 = new Date();
var d2 = new Date(d1);
console.log(d1.getTime() === d2.getTime()); //True
console.log(d1 === d2); // False
```

**5. What are wrapper objects?**

**Ans:** Primitive Values like string,number and boolean don't have properties and methods but they are temporarily converted or coerced to an object(Wrapper object) when you try to perform actions on them. For example, if you apply toUpperCase() method on a primitive string value, it does not throw an error but returns uppercase of the string.

```javascript
let name = "john";

console.log(name.toUpperCase()); // Behind the scenes treated as console.log(new String(name).toUpperCase());
```

i.e, Every primitive except null and undefined have Wrapper Objects and the list of wrapper objects are String,Number,Boolean,Symbol and BigInt.

**5. How do you compare Object and Map?**

**Ans:** **Objects** are similar to **Maps** in that both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. Due to this reason, Objects have been used as Maps historically. But there are important differences that make using a Map preferable in certain cases:

1. The keys of an Object can be Strings and Symbols, whereas they can be any value for a Map, including functions, objects, and any primitive. <br>
2. The keys in a Map are ordered while keys added to Object are not. Thus, when iterating over it, a Map object returns keys in the order of insertion. <br>
3. You can get the size of a Map easily with the size property, while the number of properties in an Object must be determined manually. <br>
4. A Map is an iterable and can thus be directly iterated, whereas iterating over an Object requires obtaining its keys in some fashion and iterating over them.
5. An Object has a prototype, so there are default keys in an object that could collide with your keys if you're not careful. As of ES5 this can be bypassed by creating an object(which can be called a map) using `Object.create(null)`, but this practice is seldom done. <br>
6. A Map may perform better in scenarios involving frequent addition and removal of key pairs. <br>

**6. What are the differences between WeakMap and Map?**

**Ans:** The main difference is that references to key objects in Map are strong while references to key objects in WeakMap are weak. i.e, A key object in WeakMap can be garbage collected if there is no other reference to it.
Other differences are,

1. Maps can store any key type Whereas WeakMaps can store only collections of key objects <br>
2. WeakMap does not have size property unlike Map <br>
3. WeakMap does not have methods such as clear, keys, values, entries, forEach. <br>
4. WeakMap is not iterable. <br>

**7. List down the collection of methods available on WeakMap?**

**Ans:** Below are the list of methods available on WeakMap,

1. set(key, value): Sets the value for the key in the WeakMap object. Returns the WeakMap object. <br>
2. delete(key): Removes any value associated to the key. <br>
3. has(key): Returns a Boolean asserting whether a value has been associated to the key in the WeakMap object or not. <br>
4. get(key): Returns the value associated to the key, or undefined if there is none. <br>
  Let's see the functionality of all the above methods in an example, <br>

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

**8. How do you map the array values without using map method?**

**Ans:** You can map the array values without using the `map` method by just using the `from` method of Array. Let's map city names from Countries array,

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

### <h1>Call, Apply and Bind</h1>

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

<h2>Questions and Answers:</h2>

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

### <h1>null, undefined, and Nan</h1>

**null** - The value null represents the intentional absence of any object value. It is one of JavaScript's primitive values. The type of null value is object. You can empty the variable by setting the value to null.

```javascript
var user = null;
console.log(typeof user); //object
```

**NaN** - The NaN property is a global property that represents "Not-a-Number" value. i.e, It indicates that a value is not a legal number. It is very rare to use NaN in a program but it can be used as return value for few cases

```javascript
Math.sqrt(-1);
parseInt("Hello");
```

**isNaN** - The isNaN() function is used to determine whether a value is an illegal number (Not-a-Number) or not. i.e, This function returns true if the value equates to NaN. Otherwise it returns false.

```javascript
isNaN("Hello"); //true
isNaN("100"); //false
```

**undefined** - The undefined property indicates that a variable has not been assigned a value, or declared but not initialized at all. The type of undefined value is undefined too.

```javascript
var user; // Value is undefined, type is undefined
console.log(typeof user); //undefined
```

Any variable can be emptied by setting the value to undefined.

```javascript
user = undefined;
```

### <h1>== and === operators</h1>

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

### <h1>How do you decode or encode a URL in JavaScript</h1>

`encodeURI()` function is used to encode an URL. This function requires a URL string as a parameter and return that encoded string.
`decodeURI()` function is used to decode an URL. This function requires an encoded URL string as parameter and return that decoded string.

**Note:** If you want to encode characters such as `/ ? : @ & = + $ #` then you need to use `encodeURIComponent()`.

```javascript
let uri = "https://mozilla.org/?x=шеллы";
let encoded_uri = encodeURI(uri); // output - https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
let decoded_uri = decodeURI(encoded_uri); // output - https://mozilla.org/?x=шеллы
```
**[⬆ Back to Top](#table-of-contents)**

### <h1>localStorage, sessionStorage, and Cookie</h1>

**localStorage:** The localStorage object allows you to save key/value pairs in the browser, the data is not deleted even when the browser is closed and reopened(i.e it has no expiration time).

**sessionStorage:** The localStorage object allows you to save key/value pairs in the browser, the data is deleted when tab is closed.

**Cookie:** The localStorage object allows you to save key/value pairs in the browser, the data is deleted as configured using Expires option.

<h2>Questions and Answers:</h2>

**1. What is web storage?**

**Ans:** Web storage is an API that provides a mechanism by which browsers can store key/value pairs locally within the user's browser, in a much more intuitive fashion than using cookies. The web storage provides two mechanisms for storing data on the client.

1. **Local storage:** It stores data for current origin with no expiration date. </br>
2. **Session storage:** It stores data for one session and the data is lost when the browser tab is closed. </br>

**2. What are the differences between cookie, local storage and session storage?**

**Ans:** Below are some of the differences between cookie, local storage and session storage,

| Feature                           | Cookie                             | Local storage    | Session storage     |
| --------------------------------- | ---------------------------------- | ---------------- | ------------------- |
| Accessed on client or server side | Both server-side & client-side     | client-side only | client-side only    |
| Lifetime                          | As configured using Expires option | until deleted    | until tab is closed |
| SSL support                       | Supported                          | Not supported    | Not supported       |
| Maximum data size                 | 4KB                                | 5 MB             | 5MB                 |

**3. What is the main difference between localStorage and sessionStorage?**

**Ans:** LocalStorage is the same as SessionStorage but it persists the data even when the browser is closed and reopened(i.e it has no expiration time) whereas in sessionStorage data gets cleared when the page session ends.

**4. How do you access web storage?**

**Ans:** The Window object implements the `WindowLocalStorage` and `WindowSessionStorage` objects which has `localStorage`(window.localStorage) and `sessionStorage`(window.sessionStorage) properties respectively. These properties create an instance of the Storage object, through which data items can be set, retrieved and removed for a specific domain and storage type (session or local).
For example, you can read and write on local storage objects as below

```javascript
localStorage.setItem("logo", document.getElementById("logo").value);
localStorage.getItem("logo");
```

**5. What are the methods available on session storage?**

The session storage provided methods for reading, writing and clearing the session data

```javascript
sessionStorage.setItem("key", "value"); // Save data to sessionStorage
let data = sessionStorage.getItem("key"); // Get saved data from sessionStorage
sessionStorage.removeItem("key"); // Remove saved data from sessionStorage
sessionStorage.clear(); // Remove all saved data from sessionStorage
```

**6. What is a storage event and its event handler?**

**Ans:** The StorageEvent is an event that fires when a storage area has been changed in the context of another document. Whereas onstorage property is an EventHandler for processing storage events.
The syntax would be as below

```javascript
window.onstorage = functionRef;
```
Let's take the example usage of onstorage event handler which logs the storage key and it's values

```javascript
window.onstorage = function (e) {
console.log(
   "The " +
      e.key +
      " key has been changed from " +
      e.oldValue +
      " to " +
      e.newValue +
      "."
);
};
```

**7. Why do you need web storage?**

**Ans:** Web storage is more secure, and large amounts of data can be stored locally, without affecting website performance. Also, the information is never transferred to the server. Hence this is a more recommended approach than Cookies.

**8. How do you check web storage browser support?**

**Ans:** You need to check browser support for localStorage and sessionStorage before using web storage,

```javascript
if (typeof Storage !== "undefined") {
// Code for localStorage/sessionStorage.
} else {
// Sorry! No Web Storage support..
}
```

**9. What is a Cookie?**

**Ans:** A cookie is a piece of data that is stored on your computer to be accessed by your browser. Cookies are saved as key/value pairs.
For example, you can create a cookie named username as below,

```javascript
document.cookie = "username=John";
```

**10. Why do you need a Cookie?**

**Ans:** Cookies are used to remember information about the user profile(such as username). It basically involves two steps,

1. When a user visits a web page, the user profile can be stored in a cookie. </br>
2. Next time the user visits the page, the cookie remembers the user profile. </br>

**11. What are the options in a cookie?**

**Ans:** There are few below options available for a cookie,

1. By default, the cookie is deleted when the browser is closed but you can change this behavior by setting expiry date (in UTC time).
```javascript
document.cookie = "username=John; expires=Sat, 8 Jun 2019 12:00:00 UTC";
```

1. By default, the cookie belongs to a current page. But you can tell the browser what path the cookie belongs to using a path parameter.
```javascript
document.cookie = "username=John; path=/services";
```

**12. How do you delete a cookie?**

You can delete a cookie by setting the expiry date as a passed date. You don't need to specify a cookie value in this case.
For example, you can delete a username cookie in the current page as below.

```javascript
document.cookie =
"username=; expires=Fri, 07 Jun 2019 00:00:00 UTC; path=/;";
```

**Note:** You should define the cookie path option to ensure that you delete the right cookie. Some browsers doesn't allow to delete a cookie unless you specify a path parameter.

**[⬆ Back to Top](#table-of-contents)**

### <h1>Object and Map</h1>


**[⬆ Back to Top](#table-of-contents)**