<h1>JavaScript Callbacks or Callbacks functions</h1>

A callback is a function that is passed as an argument to another function

This technique allows a function to call another function

A callback function can run after another function has finished (**Synchronous** and **Single-Threaded**)

**Example 1:**

```javascript
setTimeout(callBackFunction, 200)

function callBackFunction() { // Define the callback function
    console.log('I am callback function')
}
```
**Output**
```
I am callback function
```

**Example 2:**

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

**Example 3:**

```javascript
var numbers = [1, 2, 3, 4, 5]; // Define an array of numbers

function mainFunction(callback) { // Define the main function
    console.log("Performing operation...");
    numbers.forEach(callback); // Use Array.forEach to loop through the array of numbers
}

function callbackFunction(number) { // Define the callback function
console.log("Result: " + number);
}

mainFunction(callbackFunction); // Call the main function with the callback function
```
**Output**

```
Performing operation...
Result: 1
Result: 2
Result: 3
Result: 4
Result: 5
```