### Table of Contents

| No. | Questions                                                                                                                                             |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the difference between Call Apply and Bind](#What-is-the-difference-between-Call-Apply-and-Bind)                                             |
| 1   | [How do you create your own bind method using either call or apply method](#How-do-you-create-your-own-bind-method-using-either-call-or-apply-method) |

### <h2>What is the difference between Call, Apply and Bind</h2>

The difference between Call, Apply and Bind can be explained with below examples,

<h3>Call:</h3>

The call() method invokes a function with a given `this` value and arguments provided one by one.

**Example**

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2);
}

invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How are you?
invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

<h3>Apply:</h3>

Invokes the function with a given `this` value and allows you to pass in arguments as an array.

**Example**

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2);
}

invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
```

<h3>Bind:</h3>

Returns a new function, allowing you to pass any number of arguments.

**Example**

```javascript
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
   console.log(greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2);
}

var inviteEmployee1 = invite.bind(employee1);
var inviteEmployee2 = invite.bind(employee2);
inviteEmployee1("Hello", "How are you?"); // Hello John Rodson, How are you?
inviteEmployee2("Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

Call and Apply are pretty much interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.

Bind creates a new function that will have `this` set to the first parameter passed to bind().

### <h2>How do you create your own bind method using either call or apply method</h2>

The custom bind function needs to be created on Function prototype inorder to use it as other builtin functions. This custom function should return a function similar to original bind method and the implementation of inner function needs to use apply method call.

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


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
