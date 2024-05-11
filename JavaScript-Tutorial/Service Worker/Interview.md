### Table of Contents

| No. | Questions                                                                                                                   |
| --- | --------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is a service worker](#What-is-a-service-worker)                                                                       |
| 2   | [How do you manipulate DOM using a service worker](#How-do-you-manipulate-DOM-using-a-service-worker)                       |
| 3   | [How do you reuse information across service worker restarts](#How-do-you-reuse-information-across-service-worker-restarts) |
| 4   | [How do you check web workers browser support](#How-do-you-check-web-workers-browser-support)                               |
| 5   | [Give an example of a web worker](#Give-an-example-of-a-web-worker)                                                         |
| 6   | [What are the restrictions of web workers on DOM](#What-are-the-restrictions-of-web-workers-on-DOM)                         |

### <h2>What is a service worker</h2>

A Service worker is basically a script (JavaScript file) that runs in the background, separate from a web page and provides features that don't need a web page or user interaction. Some of the major features of service workers are Rich offline experiences(offline first web application development), periodic background syncs, push notifications, intercept and handle network requests and programmatically managing a cache of responses.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you manipulate DOM using a service worker</h2>

Service worker can't access the DOM directly. But it can communicate with the pages it controls by responding to messages sent via the `postMessage` interface, and those pages can manipulate the DOM.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you reuse information across service worker restarts</h2>

The problem with service worker is that it gets terminated when not in use, and restarted when it's next needed, so you cannot rely on global state within a service worker's `onfetch` and `onmessage` handlers. In this case, service workers will have access to IndexedDB API in order to persist and reuse across restarts.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check web workers browser support</h2>

You need to check browser support for web workers before using it

```javascript
if (typeof Worker !== "undefined") {
    // code for Web worker support.
} else {
    // Sorry! No Web Worker support..
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Give an example of a web worker</h2>

You need to follow below steps to start using web workers for counting example

1. Create a Web Worker File: You need to write a script to increment the count value. Let's name it as counter.js

```javascript
let i = 0;

function timedCount() {
    i = i + 1;
    postMessage(i);
    setTimeout("timedCount()", 500);
}

timedCount();
```

Here postMessage() method is used to post a message back to the HTML page

1. Create a Web Worker Object: You can create a web worker object by checking for browser support. Let's name this file as web_worker_example.js

```javascript
if (typeof w == "undefined") {
    w = new Worker("counter.js");
}
```

and we can receive messages from web worker

```javascript
w.onmessage = function (event) {
    document.getElementById("message").innerHTML = event.data;
};
```

1. Terminate a Web Worker:
    Web workers will continue to listen for messages (even after the external script is finished) until it is terminated. You can use the terminate() method to terminate listening to the messages.

```javascript
w.terminate();
```

1. Reuse the Web Worker: If you set the worker variable to undefined you can reuse the code

```javascript
w = undefined;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the restrictions of web workers on DOM</h2>

WebWorkers don't have access to below javascript objects since they are defined in an external files

 1. Window object </br>
 2. Document object </br>
 3. Parent object

 **[⬆ Back to Top](#table-of-contents)**