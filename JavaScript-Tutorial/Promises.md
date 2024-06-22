<h1>JavaScript Promises</h1>

`Promise is an object representing the eventual completion or failure of an aync operation. It returns a single value based on the operation being rejected or resolved.` </br>
Promises are used to handle aync operation </br>
There are mainly three stages of the Promise, which are shown below:

**1. pending:** It is the initial state of each Promise. It represents that the result has not been computed yet. </br>
**2. fulfilled:** It means operation was completed successfully. </br>
**3. rejected:** It means operation failed </br>

The eventual state of a pending promise can either be fulfilled with a value or rejected with a reason (error).</br>
A promise is said to be settled if it is either fulfilled or rejected, but not pending.

**Example:**

```javascript
const cart = ["shoes", "pants", "kurta"]

function createOrder(cart) { // return a promise
    const pr = new Promise((resolve, reject) => {
        if (!validateCart(cart)) {
            const err = new Error("Cart is not Valid");
            reject(err)
        }
        const orderId = '12345';
        if (orderId) {
            setTimeout(() => {
                resolve(orderId)
            }, 500)
        }
    })
    return pr;
}

function validateCart(cart) {
    return true;
}

createOrder(cart) // / return orderId as promise
    .then((orderId) => { // attached callback function when success occurs
        console.log('orderId', orderId);
    })
    .catch((err) => { // attached callback function when failure occurs
        console.log('error', err);
    })
```

<h2>Promise Chaining</h2>

```javascript
const cart = ["shoes", "pants", "kurta"]

function validateCart(cart) {
    return true;
}

function ValidateOrderId(orderId) {
    return true
}

function createOrder(cart) { // return a promise
    const pr = new Promise((resolve, reject) => {
        if (!validateCart(cart)) {
            const err = new Error("Cart is not Valid");
            reject(err)
        }
        const orderId = '12345';
        if (orderId) {
            setTimeout(() => {
                resolve(orderId)
            }, 500)
        }
    })
    return pr;
}

function proceedToPayment(orderId) {
    return new Promise((reject, resolve) => {
        if(!ValidateOrderId(orderId)) {
            const err = new Error("Order Id is not Valid");
            reject(err)
        }
        const paymentId = 'payment - 1'
        if(paymentId) {
            setTimeout(() => {
                resolve(paymentId)
            }, 500);
        }
    })
}

createOrder(cart) // / return orderId as promise
    .then((orderId) => { // attached callback function when success occurs
        console.log('orderId', orderId);
        return orderId
    })
    .then((orderId) => {
        return proceedToPayment(orderId)
    })
    .then((paymentId) => {
        console.log('paymentId', paymentId)
    })
    .catch((err) => { // attached callback function when failure occurs - handles any error
        console.log('error', err);
    })
```

<h2>JavaScript Promise Methods</h2>

| Method                         | Description                                                                                                             |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| `Promise.all(iterable)`        | Waits for all promises to be resolved or any one to be rejected                                                         |
| `Promise.allSettled(iterable)` | Waits until all promises are settled (either resolved or rejected)                                                      |
| `Promise.race(iterable)`       | Wait until any of the promises is resolved or rejected (which takes min time)                                           |
| `Promise.any(iterable)`        | Returns the promise value as soon as any one of the promises is fulfilled(resolved) if all fails return aggregate error |
| `Promise.reject(reason)`       | Returns a new Promise object that is rejected for the given reason                                                      |
| `Promise.resolve(value)`       | Returns a new Promise object that is resolved with the given value                                                      |
| `then()`                       | Appends the resolved handler callback                                                                                   |
| `catch()`                      | Appends the rejection handler callback                                                                                  |
| `finally()`                    | Appends a handler to the promise                                                                                        |

<h2>Promise.all(iterable)</h2>

**Example 1:**

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P1 Success")
    }, 1000)
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P2 Success")
    }, 2000)
})

const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P3 Success")
    }, 5000)
})

Promise.all([p1, p2, p3]).then((res) => {
    console.log(res)
})
```
**Output:** (after 5 sec) `[ 'P1 Success', 'P2 Success', 'P3 Success' ]`

**Example 2:**

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P1 Success")
    }, 1000)
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P2 Fails")
    }, 2000)
})

const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P3 Success")
    }, 5000)
})

Promise.all([p1, p2, p3])
    .then((res) => {
        console.log(res)
    })
    .catch((err) => {
        console.log(err)
    })
```
**Output:** (after 2 sec) `P2 Fails`

<h2>Promise.allSettled(iterable)</h2>

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P1 Success")
    }, 1000)
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P2 Fails")
    }, 2000)
})

const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P3 Success")
    }, 5000)
})

Promise.allSettled([p1, p2, p3])
    .then((res) => {
        console.log(res)
    })
    .catch((err) => {
        console.log(err)
    })
```
**Output** (after 5 sec)

```
[
  { status: 'fulfilled', value: 'P1 Success' },
  { status: 'rejected', reason: 'P2 Fails' },
  { status: 'fulfilled', value: 'P3 Success' }
]
```

<h2>Promise.race(iterable)</h2>

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P1 Success")
    }, 1000)
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P2 Fails")
    }, 2000)
})

const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P3 Success")
    }, 5000)
})

Promise.race([p1, p2, p3])
    .then((res) => {
        console.log(res)
    })
    .catch((err) => {
        console.log(err)
    })
```
**Output** (after 1 sec) `P1 Success`

<h2>Promise.any(iterable)</h2>

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P1 Success")
    }, 1000)
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P2 Fails")
    }, 2000)
})

const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("P3 Success")
    }, 5000)
})

Promise.any([p1, p2, p3])
    .then((res) => {
        console.log(res)
    })
    .catch((err) => {
        console.log(err)
    })
```
**Output** (after 5 sec) `P3 Success`

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P1 Success")
    }, 1000)
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P2 Fails")
    }, 2000)
})

const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("P3 Success")
    }, 5000)
})

Promise.any([p1, p2, p3])
    .then((res) => {
        console.log(res)
    })
    .catch((err) => {
        console.log(err)
    })
```
**Output** (aggregate error after 5 sec)

```
[AggregateError: All promises were rejected] {
  [errors]: [ 'P1 Success', 'P2 Fails', 'P3 Success' ]
}

if replace console.log(err) with console.log(err.errors) then output [ 'P1 Success', 'P2 Fails', 'P3 Success' ]
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>


