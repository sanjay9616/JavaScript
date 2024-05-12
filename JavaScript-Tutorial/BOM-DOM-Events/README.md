`Both the BOM and DOM are part of the JavaScript environment within a web browser`

`The BOM provides access to browser-specific features and controls the browser window.`

`The DOM represents the structure of an HTML or XML document and enables manipulation of its elements.`

<h1>Event Flow</h1>

Event flow is the order in which event is received on the web page. When you click an element that is nested in various other elements, before your click actually reaches its destination, or target element, it must trigger the click event for each of its parent elements first, starting at the top with the global window object.
There are two ways of event flow

The stopPropagation method is used to stop the event from bubbling up and capturing up the event chain. For example, the below nested divs with stopPropagation method prevents default event propagation when clicking on nested div(Div1)

1. Top to Bottom(Event Capturing) </br>
2. Bottom to Top (Event Bubbling)

<h2>1. Top to Bottom(Event Capturing)</h2>

Event capturing is a type of event propagation where the event is first captured by the outermost element, and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the innermost DOM element.

<h2>2. Bottom to Top (Event Bubbling)</h2>

Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element.

<h1>Event Delegation</h1>

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

<h1>Server Side Events</h1>

A server-sent event is when a web page automatically gets updates from a server.

This was also possible before, but the web page would have to ask if any updates were available. With server-sent events, the updates come automatically.

Examples: Facebook/Twitter updates, stock price updates, news feeds, sport results, etc.

<h1>Event Queue</h1>

The event queue follows the queue data structure. It stores async callbacks to be added to the call stack. It is also known as the Callback Queue or Macrotask Queue.

Whenever the call stack receives an async function, it is moved into the Web API. Based on the function, Web API executes it and awaits the result. Once it is finished, it moves the callback into the event queue (the callback of the promise is moved into the microtask queue).

The event loop constantly checks whether or not the call stack is empty. Once the call stack is empty and there is a callback in the event queue, the event loop moves the callback into the call stack. But if there is a callback in the microtask queue as well, it is moved first. The microtask queue has a higher priority than the event queue.

<h1>Event loop</h1>

The event loop is a process that continuously monitors both the call stack and the event queue and checks whether or not the call stack is empty. If the call stack is empty and there are pending events in the event queue, the event loop dequeues the event from the event queue and pushes it to the call stack. The call stack executes the event, and any additional events generated during the execution are added to the end of the event queue.

**Note:** The event loop allows Node.js to perform non-blocking I/O operations, even though JavaScript is single-threaded, by offloading operations to the system kernel whenever possible. Since most modern kernels are multi-threaded, they can handle multiple operations executing in the background.

<h1>Event Table</h1>

Event Table is a data structure that stores and keeps track of all the events which will be executed asynchronously like after some time interval or after the resolution of some API requests. i.e Whenever you call a setTimeout function or invoke async operation, it is added to the Event Table.

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
