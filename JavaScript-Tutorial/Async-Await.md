<h1>Async and Await</h1>

The word `async` before a function means one simple thing: a function **always returns a promise**</br>
The `await` keyword is used inside the async function to wait for the asynchronous operation.</br>

**Sync:** only one operation or program will run at a time.</br>
**Async:** Async means process operates independently of other processes means operations or program can run in parallel.</br>

`Async and Await combo is used to handle Promises`

```javascript
async function getData() { // always return Promise
    return "Sanjay"
}
getData()
    .then((res) => {
        console.log(res)
    }) // Sanjay
```

<h2>How to handle promise before Async and Await</h2>

```javascript
const p = new Promise((resolve, reject) => {
    resolve("Promise resolved value!")
})
getData = () => {
    p.then((res) => console.log(res))
}
getData() // Promise resolved value!
```
OR (without arrow function)

```javascript
const p = new Promise((resolve, reject) => {
    resolve("Promise resolved value!")
})
function getData() {
    p.then((res) => console.log(res))
}
getData() // Promise resolved value!
```

<h2>How to handle promise after Async and Await</h2>

```javascript
const p = new Promise((resolve, reject) => {
    resolve("Promise resolved value!")
})
getData = async () => {
    const val = await p;
    console.log(val)
}
getData() // Promise resolved value!
```
OR (without arrow function)

```javascript
const p = new Promise((resolve, reject) => {
    resolve("Promise resolved value!")
})
async function getData() {
    const val = await p; // await can be only used inside an async function
    console.log(val)
}
getData() // Promise resolved value!
```

<h2>Dividing deep into Async Await</h2>

```javascript
const p = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Promise resolved value!")
    }, 5000)
})
getData = async() => {
    console.log('111')
    const val1 = await p;
    console.log('222')
    console.log(val1)

    const val2 = await p;
    console.log('222')
    console.log(val2)
}
getData()
```
Output
```
111
// after 5 sec below value print at a time
222
Promise resolved value!
222
Promise resolved value!
```

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Promise resolved value - 1!")
    }, 10000)
})
const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Promise resolved value - 2!")
    }, 5000)
})
getData = async() => {
    console.log('111')
    const val1 = await p1;
    console.log('222')
    console.log(val1)

    const val2 = await p2;
    console.log('222')
    console.log(val2)
}
getData()
```
Output
```
111
// after 10 sec below value print at a time
222
Promise resolved value - 1!
222
Promise resolved value - 2!
```

```javascript
const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Promise resolved value - 1!")
    }, 10000)
})
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Promise resolved value - 2!")
    }, 5000)
})
getData = async() => {
    console.log('111')
    const val1 = await p1;
    console.log('222')
    console.log(val1)

    const val2 = await p2;
    console.log('222')
    console.log(val2)
}
getData()
```
Output
```
111
// after 5 sec
222
Promise resolved value - 2!
// after next 5 sec
222
Promise resolved value - 1!
```

<h2>Error Handling in Async Await</h2>

```javascript
const p = new Promise((resolve, reject) => {
    reject("Promise resolved value!")
})
async function getData() {
    try {
        const val = await p;
        console.log(val)
    } catch(err) {
        console.log('err - catch', err)
    }
}
getData() // err - catch Promise resolved value!
```

```javascript
const API_URL = "https://api.github.com/users/sanjay9616"
async function handlePromise() {
    try {
        const data = await fetch(API_URL);
        const jsonValue = await data.json();
        consoe.log('json', jsonValue)
    } catch(err) {
        console.log('err', err)
    }
}
handlePromise()
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>

