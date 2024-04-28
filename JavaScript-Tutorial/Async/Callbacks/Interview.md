### Table of Contents

| No. | Questions                                                     |
| --- | ------------------------------------------------------------- |
| 1   | [What is a callback function](#What-is-a-callback-function)   |
| 2   | [Why do we need callbacks](#Why-do-we-need-callbacks)         |
| 3   | [What is a callback hell](#What-is-a-callback-hell)           |
| 4   | [What is callback in callback](#What-is-callback-in-callback) |

### <h2>What is a callback function</h2>

A callback function is a function passed into another function as an argument. This function is invoked inside the outer function to complete an action.
Let's take a simple example of how to use callback function

```javascript
function callbackFunction(name) {
    console.log("Hello " + name);
}

function outerFunction(callback) {
    let name = prompt("Please enter your name.");
    callback(name);
}

outerFunction(callbackFunction);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do we need callbacks</h2>

The callbacks are needed because javascript is an event driven language. That means instead of waiting for a response javascript will keep executing while listening for other events.
Let's take an example with the first function invoking an API call(simulated by setTimeout) and the next function which logs the message.

```javascript
function firstFunction() {
    // Simulate a code delay
    setTimeout(function () {
    console.log("First function called");
    }, 1000);
}
function secondFunction() {
    console.log("Second function called");
}
firstFunction();
secondFunction();

Output;
// Second function called
// First function called
```

As observed from the output, javascript didn't wait for the response of the first function and the remaining code block got executed. So callbacks are used in a way to make sure that certain code doesn’t execute until the other code finishes execution.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a callback hell</h2>

Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic. The callback hell looks like below,

```javascript
async1(function(){
    async2(function(){
        async3(function(){
            async4(function(){
                ....
            });
        });
    });
});
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is callback in callback</h2>

You can nest one callback inside in another callback to execute the actions sequentially one by one. This is known as callbacks in callbacks.

```javascript
loadScript("/script1.js", function (script) {
    console.log("first script is loaded");

    loadScript("/script2.js", function (script) {
    console.log("second script is loaded");

    loadScript("/script3.js", function (script) {
        console.log("third script is loaded");
        // after all scripts are loaded
    });
    });
});
```

**[⬆ Back to Top](#table-of-contents)**