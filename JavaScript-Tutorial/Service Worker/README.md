<h1>Web Workers or Service Workers</h1>

`A Service worker is basically a script (JavaScript file) that runs in the background, separate from a web page and provides features that don't need a web page or user interaction. Some of the major features of service workers are Rich offline experiences(offline first web application development), periodic background syncs, push notifications, intercept and handle network requests and programmatically managing a cache of responses.`

<ul>
    <li>It means to run your code in a background script</li>
    <li>We can create a worker object using constructor Worker()</li>
    <li>Worker runs in a different global context</li>
    <li>They can do complex operations without interfering the UI</li>
    <li>They can send and accept message/data from UI using events</li>
</ul>

```js
var workerObj = new Worker('workerFileName.js')
onMessage(), postMessage()
```

<h1>Advantages</h1>

1. Helps in complext computing. </br>
2. Does not block the UI. </br>
3. Optimize performance of our program. </br>

<h1>Disadvantages</h1>

1. Does not have access to Parent object. </br>
2. Does not have access to window object. </br>
3. Does not have access to Document Object. </br>