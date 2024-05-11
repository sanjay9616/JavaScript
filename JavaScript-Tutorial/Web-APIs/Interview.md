### Table of Contents

| No. | Questions                                                                                                                                                     |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the use of setTimeout](#What-is-the-use-of-setTimeout)                                                                                               |
| 2   | [What is the purpose of clearTimeout method](#What-is-the-purpose-of-clearTimeout-method)                                                                     |
| 3   | [What is the use of setInterval](#What-is-the-use-of-setInterval)                                                                                             |
| 4   | [What is the purpose of clearInterval method](#What-is-the-purpose-of-clearInterval-method)                                                                   |
| 5   | [What is the difference between setTimeout, setImmediate and process.nextTick](#What-is-the-difference-between-setTimeout,-setImmediate-and-process.nextTick) |
| 6   | [How to cancel a fetch request](#How-to-cancel-a-fetch-request)                                                                                               |
| 7   | [How do you display data in a tabular format using console object](#How-do-you-display-data-in-a-tabular-format-using-console-object)                         |
| 8   | [What are the tools or techniques used for debugging JavaScript code](#What-are-the-tools-or-techniques-used-for-debugging-JavaScript-code)                   |
| 9   | [What is a debugger statement](#What-is-a-debugger-statement)                                                                                                 |
| 10  | [What is the purpose of breakpoints in debugging](#What-is-the-purpose-of-breakpoints-in-debugging)                                                           |
| 11  | [What are the placeholders from console object](#What-are-the-placeholders-from-console-object)                                                               |
| 12  | [Is it possible to add CSS to console messages](#Is-it-possible-to-add-CSS-to-console-messages)                                                               |
| 13  | [What is the purpose of dir method of console object](#What-is-the-purpose-of-dir-method-of-console-object)                                                   |
| 14  | [Is it possible to debug HTML elements in console](#Is-it-possible-to-debug-HTML-elements-in-console)                                                         |
| 15  | [How do you group and nest console output](#How-do-you-group-and-nest-console-output)                                                                         |
| 16  | [How do style the console output using CSS](#How-do-style-the-console-output-using-CSS)                                                                       |
| 17  | [How do you encode an URL](#How-do-you-encode-an-URL)                                                                                                         |
| 18  | [How do you decode an URL](#How-do-you-decode-an-URL)                                                                                                         |
| 19  | [What are the various url properties of location object](#What-are-the-various-url-properties-of-location-object)                                             |
| 20  | [How do you get the current url with javascript](#How-do-you-get-the-current-url-with-javascript)                                                             |
| 21  | [How do I modify the url without reloading the page](#How-do-I-modify-the-url-without-reloading-the-page)                                                     |
| 22  | [How do you decode or encode a URL in JavaScript](#How-do-you-decode-or-encode-a-URL-in-JavaScript)                                                           |
| 23  | [How do get query string values in javascript](#How-do-get-query-string-values-in-javascript)                                                                 |
| 24  | [How do you print the contents of web page](#How-do-you-print-the-contents-of-web-page)                                                                       |
| 25  | [How do you access history in javascript](#How-do-you-access-history-in-javascript)                                                                           |
| 26  | [How do you detect caps lock key turned on or not](#How-do-you-detect-caps-lock-key-turned-on-or-not)                                                         |

### <h2>What is the use of setTimeout</h2>

The setTimeout() method is used to call a function or evaluate an expression after a specified number of milliseconds. For example, let's log a message after 2 seconds using setTimeout method,

```javascript
setTimeout(function () {
    console.log("Good morning");
}, 2000);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of clearTimeout method</h2>

The clearTimeout() function is used in javascript to clear the timeout which has been set by setTimeout() function before that. i.e, The return value of setTimeout() function is stored in a variable and it’s passed into the clearTimeout() function to clear the timer.

For example, the below setTimeout method is used to display the message after 3 seconds. This timeout can be cleared by the clearTimeout() method.

```javascript
<script>
var msg;
function greeting() {
    alert('Good morning');
}
function start() {
msg =setTimeout(greeting, 3000);

}

function stop() {
    clearTimeout(msg);
}
</script>
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the use of setInterval</h2>

The setInterval() method is used to call a function or evaluate an expression at specified intervals (in milliseconds). For example, let's log a message after 2 seconds using setInterval method,

```javascript
setInterval(function () {
    console.log("Good morning");
}, 2000);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of clearInterval method</h2>

The clearInterval() function is used in javascript to clear the interval which has been set by setInterval() function. i.e, The return value returned by setInterval() function is stored in a variable and it’s passed into the clearInterval() function to clear the interval.

For example, the below setInterval method is used to display the message for every 3 seconds. This interval can be cleared by the clearInterval() method.

```javascript
<script>
var msg;
function greeting() {
    alert('Good morning');
}

function start() {
    msg = setInterval(greeting, 3000);
}

function stop() {
    clearInterval(msg);
}
</script>
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between setTimeout, setImmediate and process.nextTick</h2>

1. **Set Timeout:** setTimeout() is to schedule execution of a one-time callback after delay milliseconds. </br>
2. **Set Immediate:** The setImmediate function is used to execute a function right after the current event loop finishes. </br>
3. **Process NextTick:** If process.nextTick() is called in a given phase, all the callbacks passed to process.nextTick() will be resolved before the event loop continues. This will block the event loop and create I/O Starvation if process.nextTick() is called recursively.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How to cancel a fetch request</h2>

Until a few days back, One shortcoming of native promises is no direct way to cancel a fetch request. But the new `AbortController` from js specification allows you to use a signal to abort one or multiple fetch calls.
The basic flow of cancelling a fetch request would be as below,

1. Create an `AbortController` instance
2. Get the signal property of an instance and pass the signal as a fetch option for signal
3. Call the AbortController's abort property to cancel all fetches that use that signal
For example, let's pass the same signal to multiple fetch calls will cancel all requests with that signal,

```javascript
const controller = new AbortController();
const { signal } = controller;

fetch("http://localhost:8000", { signal })
.then((response) => {
    console.log(`Request 1 is complete!`);
})
.catch((e) => {
    if (e.name === "AbortError") {
    // We know it's been canceled!
    }
});

fetch("http://localhost:8000", { signal })
.then((response) => {
    console.log(`Request 2 is complete!`);
})
.catch((e) => {
    if (e.name === "AbortError") {
    // We know it's been canceled!
    }
});

// Wait 2 seconds to abort both requests
setTimeout(() => controller.abort(), 2000);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you display data in a tabular format using console object</h2>

The `console.table()` is used to display data in the console in a tabular format to visualize complex arrays or objects.

```js
const users = [
    { name: "John", id: 1, city: "Delhi" },
    { name: "Max", id: 2, city: "London" },
    { name: "Rod", id: 3, city: "Paris" },
];
console.table(users);
```

**Not:** Remember that `console.table()` is not supported in IE.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the tools or techniques used for debugging JavaScript code</h2>

You can use below tools or techniques for debugging javascript

1. Chrome Devtools </br>
2. debugger statement </br>
3. Good old console.log statement </br>

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a debugger statement</h2>

The debugger statement invokes any available debugging functionality, such as setting a breakpoint. If no debugging functionality is available, this statement has no effect.
For example, in the below function a debugger statement has been inserted. So
execution is paused at the debugger statement just like a breakpoint in the script source.

```javascript
function getProfile() {
    // code goes here
    debugger;
    // code goes here
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of breakpoints in debugging</h2>

You can set breakpoints in the javascript code once the debugger statement is executed and the debugger window pops up. At each breakpoint, javascript will stop executing, and let you examine the JavaScript values. After examining values, you can resume the execution of code using the play button.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the placeholders from console object</h2>

Below are the list of placeholders available from console object,

1. %o — It takes an object, </br>
2. %s — It takes a string, </br>
3. %d — It is used for a decimal or integer
  These placeholders can be represented in the console.log as below

```javascript
const user = { name: "John", id: 1, city: "Delhi" };
console.log(
 "Hello %s, your details %o are available in the object form",
 "John",
 user
); // Hello John, your details {name: "John", id: 1, city: "Delhi"} are available in object
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Is it possible to add CSS to console messages</h2>

Yes, you can apply CSS styles to console messages similar to html text on the web page.

```javascript
console.log(
"%c The text has blue color, with large font and red background",
"color: blue; font-size: x-large; background: red"
);
```

**Note:** All CSS styles can be applied to console messages.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the purpose of dir method of console object</h2>

The `console.dir()` is used to display an interactive list of the properties of the specified JavaScript object as JSON.

```javascript
const user = { name: "John", id: 1, city: "Delhi" };
console.dir(user);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Is it possible to debug HTML elements in console</h2>

Yes, it is possible to get and debug HTML elements in the console just like inspecting elements.

```javascript
const element = document.getElementsByTagName("body")[0];
console.log(element);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you group and nest console output<h2>

The `console.group()` can be used to group related log messages to be able to easily read the logs and use console.groupEnd()to close the group. Along with this, you can also nest groups which allows to output message in hierarchical manner.

For example, if you’re logging a user’s details:

```js
console.group("User Details");
console.log("name: Sudheer Jonna");
console.log("job: Software Developer");

// Nested Group
console.group("Address");
console.log("Street: Commonwealth");
console.log("City: Los Angeles");
console.log("State: California");

// Close nested group
console.groupEnd();

// Close outer group
console.groupEnd();
```

You can also use `console.groupCollapsed()` instead of `console.group()` if you want the groups to be collapsed by default.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do style the console output using CSS</h2>

You can add CSS styling to the console output using the CSS format content specifier %c. The console string message can be appended after the specifier and CSS style in another argument. Let's print the red the color text using console.log and CSS specifier as below,

```js
console.log("%cThis is a red text", "color:red");
```

It is also possible to add more styles for the content. For example, the font-size can be modified for the above text

```js
console.log(
    "%cThis is a red text with bigger font",
    "color:red; font-size:20px"
);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you encode an URL</h2>

The encodeURI() function is used to encode complete URI which has special characters except (, / ? : @ & = + $ #) characters.

```javascript
var uri = "https://mozilla.org/?x=шеллы";
var encoded = encodeURI(uri);
console.log(encoded); // https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you decode an URL</h2>

The decodeURI() function is used to decode a Uniform Resource Identifier (URI) previously created by encodeURI().

```javascript
var uri = "https://mozilla.org/?x=шеллы";
var encoded = encodeURI(uri);
console.log(encoded); // https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
try {
    console.log(decodeURI(encoded)); // "https://mozilla.org/?x=шеллы"
} catch (e) {
    // catches a malformed URI
    console.error(e);
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the various url properties of location object</h2>

The below `Location` object properties can be used to access URL components of the page,

1. href - The entire URL </h2>
2. protocol - The protocol of the URL </h2>
3. host - The hostname and port of the URL </h2>
4. hostname - The hostname of the URL </h2>
5. port - The port number in the URL </h2>
6. pathname - The path name of the URL </h2>
7. search - The query portion of the URL </h2>
8. hash - The anchor portion of the URL </h2>

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you get the current url with javascript<h2>

You can use `window.location.href` expression to get the current url path and you can use the same expression for updating the URL too. You can also use `document.URL` for read-only purposes but this solution has issues in FF.

```javascript
console.log("location.href", window.location.href); // Returns full URL
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do I modify the url without reloading the page</h2>

The `window.location.href` property will be helpful to modify the url but it reloads the page. HTML5 introduced the `history.pushState()` and `history.replaceState()` methods, which allow you to add and modify history entries, respectively. For example, you can use pushState as below,

```javascript
window.history.pushState("page2", "Title", "/page2.html");
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you decode or encode a URL in JavaScript</h2>

`encodeURI()` function is used to encode an URL. This function requires a URL string as a parameter and return that encoded string. </br>
`decodeURI()` function is used to decode an URL. This function requires an encoded URL string as parameter and return that decoded string.

**Note:** If you want to encode characters such as `/ ? : @ & = + $ #` then you need to use `encodeURIComponent()`.

```javascript
let uri = "https://mozilla.org/?x=шеллы";
let encoded_uri = encodeURI(uri); // output - https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
let decoded_uri = decodeURI(encoded_uri); // output - https://mozilla.org/?x=шеллы
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do get query string values in javascript</h2>

You can use URLSearchParams to get query string values in javascript. Let's see an example to get the client code value from URL query string,

```javascript
const urlParams = new URLSearchParams(window.location.search);
const clientCode = urlParams.get("clientCode");
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you print the contents of web page</h2>

The window object provided a print() method which is used to print the contents of the current window. It opens a Print dialog box which lets you choose between various printing options. Let's see the usage of print method in an example,

```html
<input type="button" value="Print" onclick="window.print()" />
```

**Note:** In most browsers, it will block while the print dialog is open.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you access history in javascript</h2>

The window.history object contains the browser's history. You can load previous and next URLs in the history using back() and next() methods.

```javascript
function goBack() {
    window.history.back();
}

function goForward() {
    window.history.forward();
}
```

**Note:** You can also access history without window prefix.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you detect caps lock key turned on or not</h2>

The `mouseEvent getModifierState()` is used to return a boolean value that indicates whether the specified modifier key is activated or not. The modifiers such as CapsLock, ScrollLock and NumLock are activated when they are clicked, and deactivated when they are clicked again.

Let's take an input element to detect the CapsLock on/off behavior with an example,

```html
<input type="password" onmousedown="enterInput(event)" />

<p id="feedback"></p>

<script>
    function enterInput(e) {
    var flag = e.getModifierState("CapsLock");
    if (flag) {
        document.getElementById("feedback").innerHTML = "CapsLock activated";
    } else {
        document.getElementById("feedback").innerHTML =
        "CapsLock not activated";
    }
    }
</script>
```

**[⬆ Back to Top](#table-of-contents)**


