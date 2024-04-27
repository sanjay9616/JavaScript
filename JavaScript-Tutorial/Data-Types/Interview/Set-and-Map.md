### Table of Contents

| No. | Questions                                                                                                             |
| --- | --------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is a WeakSet](#What-is-a-WeakSet)                                                                               |
| 2   | [What are the differences between a WeakSet and a Set](#What-are-the-differences-between-a-WeakSet-and-a-Set)         |
| 3   | [List down the collection of methods available on WeakSet](#List-down-the-collection-of-methods-available-on-WeakSet) |

### <h2>What is a WeakSet</h2>

WeakSet is used to store a collection of weakly(weak references) held objects. The syntax would be as follows,

```javascript
new WeakSet([iterable]);
```

Let's see the below example to explain it's behavior,

```javascript
var ws = new WeakSet();
var user = {};
ws.add(user);
ws.has(user); // true
ws.delete(user); // removes user from the set
ws.has(user); // false, user has been removed
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between a WeakSet and a Set</h2>

The main difference is that references to objects in Set are strong while references to objects in WeakSet are weak. i.e, An object in WeakSet can be garbage collected if there is no other reference to it.
Other differences are,

1. Sets can store any value Whereas WeakSets can store only collections of objects </br>
2. WeakSet does not have size property unlike Set </br>
3. WeakSet does not have methods such as clear, keys, values, entries, forEach. </br>
4. WeakSet is not iterable. </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>List down the collection of methods available on WeakSet</h2>

Below are the list of methods available on WeakSet,

1. add(value): A new object is appended with the given value to the weakset </br>
2. delete(value): Deletes the value from the WeakSet collection. </br>
3. has(value): It returns true if the value is present in the WeakSet Collection, otherwise it returns false. </br>

Let's see the functionality of all the above methods in an example,

```javascript
var weakSetObject = new WeakSet();
var firstObject = {};
var secondObject = {};
// add(value)
weakSetObject.add(firstObject);
weakSetObject.add(secondObject);
console.log(weakSetObject.has(firstObject)); //true
weakSetObject.delete(secondObject);
```

**[⬆ Back to Top](#table-of-contents)**