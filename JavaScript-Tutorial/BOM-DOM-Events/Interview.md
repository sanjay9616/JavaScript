### Table of Contents

| No. | Questions                                                                                                                                             |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is an event flow](#What-is-an-event-flow)                                                                                                       |
| 2   | [What is event bubbling](#What-is-event-bubbling)                                                                                                     |
| 3   | [What is event capturing](#What-is-event-capturing)                                                                                                   |
| 4   | [What is the use of stopPropagation method](#What-is-the-use-of-stopPropagation-method)                                                               |
| 5   | [What is an event delegation](#What-is-an-event-delegation)                                                                                           |
| 6   | [What is an event queue](#What-is-an-event-queue)                                                                                                     |
| 7   | [What is an event table](#What-is-an-event-table)                                                                                                     |
| 8   | [What is the use of preventDefault method](#What-is-the-use-of-preventDefault-method)                                                                 |
| 9   | [What are events](#What-are-events)                                                                                                                   |
| 10  | [What are server-sent events](#What-are-server-sent-events)                                                                                           |
| 11  | [How do you receive server-sent event notifications](#How-do-you-receive-server-sent-event-notifications)                                             |
| 12  | [How do you check browser support for server-sent events](#How-do-you-check-browser-support-for-server-sent-events)                                   |
| 13  | [What are the events available for server sent events](#What-are-the-events-available-for-server-sent-events)                                         |
| 14  | [What is the difference between document load and DOMContentLoaded events](#What-is-the-difference-between-document-load-and-DOMContentLoaded-events) |
| 15  | [What is BOM](#What-is-BOM)                                                                                                                           |

### <h2>What is an event flow</h2>

Event flow is the order in which event is received on the web page. When you click an element that is nested in various other elements, before your click actually reaches its destination, or target element, it must trigger the click event for each of its parent elements first, starting at the top with the global window object.

There are two ways of event flow

1. Top to Bottom(Event Capturing) </h2>
2. Bottom to Top (Event Bubbling)

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is event bubbling</h2>

Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is event capturing</h2>

Event capturing is a type of event propagation where the event is first captured by the outermost element, and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the innermost DOM element.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the use of stopPropagation method</h2>

The stopPropagation method is used to stop the event from bubbling up and capturing up the event chain. For example, the below nested divs with stopPropagation method prevents default event propagation when clicking on nested div(Div1)

```javascript
<p>Click DIV1 Element</p>
<div onclick="secondFunc()">DIV 2
<div onclick="firstFunc(event)">DIV 1</div>
</div>

<script>
function firstFunc(event) {
    alert("DIV 1");
    event.stopPropagation();
}

function secondFunc() {
    alert("DIV 2");
}
</script>
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an event delegation</h2>

Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

For example, if you wanted to detect field changes in inside a specific form, you can use event delegation technique,

```javascript
var form = document.querySelector("#registration-form");

// Listen for changes to fields inside the form
form.addEventListener(
    "input",
    function (event) {
        // Log the field that was changed
        console.log(event.target);
    },
    false
);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an event queue</h2>

The event queue follows the queue data structure. It stores async callbacks to be added to the call stack. It is also known as the Callback Queue or Macrotask Queue.

Whenever the call stack receives an async function, it is moved into the Web API. Based on the function, Web API executes it and awaits the result. Once it is finished, it moves the callback into the event queue (the callback of the promise is moved into the microtask queue).

The event loop constantly checks whether or not the call stack is empty. Once the call stack is empty and there is a callback in the event queue, the event loop moves the callback into the call stack. But if there is a callback in the microtask queue as well, it is moved first. The microtask queue has a higher priority than the event queue.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is an event table</h2>

Event Table is a data structure that stores and keeps track of all the events which will be executed asynchronously like after some time interval or after the resolution of some API requests. i.e Whenever you call a setTimeout function or invoke async operation, it is added to the Event Table.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the use of preventDefault method</h2>

The preventDefault() method cancels the event if it is cancelable, meaning that the default action or behaviour that belongs to the event will not occur. For example, prevent form submission when clicking on submit button and prevent opening the page URL when clicking on hyperlink are some common use cases.

```javascript
document
.getElementById("link")
.addEventListener("click", function (event) {
    event.preventDefault();
});
```

**Note:** Remember that not all events are cancelable.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are events</h2>

Events are "things" that happen to HTML elements. When JavaScript is used in HTML pages, JavaScript can `react` on these events. Some of the examples of HTML events are,

1. Web page has finished loading </br>
2. Input field was changed </br>
3. Button was clicked

Let's describe the behavior of click event for button element,

```javascript
<!doctype html>
<html>
<head>
  <script>
    function greeting() {
      alert('Hello! Good morning');
    }
  </script>
</head>
<body>
  <button type="button" onclick="greeting()">Click me</button>
</body>
</html>
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are server-sent events</h2>

Server-sent events (SSE) is a server push technology enabling a browser to receive automatic updates from a server via HTTP connection without resorting to polling. These are a one way communications channel - events flow from server to client only. This has been used in Facebook/Twitter updates, stock price updates, news feeds etc.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you receive server-sent event notifications</h2>

The EventSource object is used to receive server-sent event notifications. For example, you can receive messages from server as below,

```javascript
if (typeof EventSource !== "undefined") {
    var source = new EventSource("sse_generator.js");
    source.onmessage = function (event) {
    document.getElementById("output").innerHTML += event.data + "<br>";
    };
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check browser support for server-sent events</h2>

You can perform browser support for server-sent events before using it as below,

```javascript
if (typeof EventSource !== "undefined") {
    // Server-sent events supported. Let's have some code here!
} else {
    // No server-sent events supported
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the events available for server sent events</h2>

Below are the list of events available for server sent events

| Event     | Description                                          |
| --------- | ---------------------------------------------------- |
| onopen    | It is used when a connection to the server is opened |
| onmessage | This event is used when a message is received        |
| onerror   | It happens when an error occurs                      |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the difference between document load and DOMContentLoaded events</h2>

The `DOMContentLoaded` event is fired when the initial HTML document has been completely loaded and parsed, without waiting for assets(stylesheets, images, and subframes) to finish loading. Whereas The load event is fired when the whole page has loaded, including all dependent resources(stylesheets, images).

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is BOM</h2>

The Browser Object Model (BOM) allows JavaScript to "talk to" the browser. It consists of the objects navigator, history, screen, location and document which are children of the window. The Browser Object Model is not standardized and can change based on different browsers.


**[⬆ Back to Top](#table-of-contents)**
