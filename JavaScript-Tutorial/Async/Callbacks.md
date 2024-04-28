<h1>JavaScript Callbacks or Callbacks functions</h1>

A callback is a function that is passed as an argument to another function

This technique allows a function to call another function

A callback function can run after another function has finished (**Synchronous** and **Single-Threaded**)

```javascript
function mainFunction(callback) {
    console.log("Performing operation...");
    setTimeout(() => { // Use setTimeout to simulate an asynchronous operation
        callback("Operation complete");
    }, 1000);
}

function callbackFunction(result) { // Define the callback function
    console.log("Result: " + result);
}

mainFunction(callbackFunction); // Call the main function with the callback function
```
**Output**
```
Performing operation...
Result: Operation complete
```