### Table of Contents

| No. | Questions                                                                                                                                                 |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is web storage](#What-is-web-storage)                                                                                                               |
| 2   | [How do you access web storage](#How-do-you-access-web-storage)                                                                                           |
| 3   | [Why do you need web storage](#Why-do-you-need-web-storage)                                                                                               |
| 4   | [How do you check web storage browser support](#How-do-you-check-web-storage-browser-support)                                                             |
| 5   | [What are the differences between cookie, local storage and session storage](#What-are-the-differences-between-cookie,-local-storage-and-session-storage) |
| 6   | [What is the main difference between localStorage and sessionStorage](#What-is-the-main-difference-between-localStorage-and-sessionStorage)               |
| 7   | [What are the methods available on session storage](#What-are-the-methods-available-on-session-storage)                                                   |
| 8   | [What is a storage event and its event handler](#What-is-a-storage-event-and-its-event-handler)                                                           |
| 9   | [What is a Cookie](#What-is-a-Cookie)                                                                                                                     |
| 10  | [Why do you need a Cookie](#Why-do-you-need-a-Cookie)                                                                                                     |
| 11  | [What are the options in a cookie](#What-are-the-options-in-a-cookie)                                                                                     |
| 12  | [How do you delete a cookie](#How-do-you-delete-a-cookie)                                                                                                 |

### <h2>What is web storage</h2>

Web storage is an API that provides a mechanism by which browsers can store key/value pairs locally within the user's browser, in a much more intuitive fashion than using cookies. The web storage provides two mechanisms for storing data on the client.

1. **Local storage:** It stores data for current origin with no expiration date. </br>
2. **Session storage:** It stores data for one session and the data is lost when the browser tab is closed.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you access web storage</h2>

The Window object implements the `WindowLocalStorage` and `WindowSessionStorage` objects which has `localStorage`(window.localStorage) and `sessionStorage`(window.sessionStorage) properties respectively. These properties create an instance of the Storage object, through which data items can be set, retrieved and removed for a specific domain and storage type (session or local).
For example, you can read and write on local storage objects as below

```javascript
localStorage.setItem("logo", document.getElementById("logo").value);
localStorage.getItem("logo");
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do you need web storage</h2>

Web storage is more secure, and large amounts of data can be stored locally, without affecting website performance. Also, the information is never transferred to the server. Hence this is a more recommended approach than Cookies.

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you check web storage browser support</h2>

You need to check browser support for localStorage and sessionStorage before using web storage,

```javascript
if (typeof Storage !== "undefined") {
    // Code for localStorage/sessionStorage.
} else {
    // Sorry! No Web Storage support..
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the differences between cookie, local storage and session storage</h2>

Below are some of the differences between cookie, local storage and session storage,

| Feature                           | Cookie                             | Local storage    | Session storage     |
| --------------------------------- | ---------------------------------- | ---------------- | ------------------- |
| Accessed on client or server side | Both server-side & client-side     | client-side only | client-side only    |
| Lifetime                          | As configured using Expires option | until deleted    | until tab is closed |
| SSL support                       | Supported                          | Not supported    | Not supported       |
| Maximum data size                 | 4KB                                | 5 MB             | 5MB                 |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the main difference between localStorage and sessionStorage</h2>

LocalStorage is the same as SessionStorage but it persists the data even when the browser is closed and reopened(i.e it has no expiration time) whereas in sessionStorage data gets cleared when the page session ends.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the methods available on session storage</h2>

The session storage provided methods for reading, writing and clearing the session data

```javascript
// Save data to sessionStorage
sessionStorage.setItem("key", "value");

// Get saved data from sessionStorage
let data = sessionStorage.getItem("key");

// Remove saved data from sessionStorage
sessionStorage.removeItem("key");

// Remove all saved data from sessionStorage
sessionStorage.clear();
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a storage event and its event handler</h2>

The StorageEvent is an event that fires when a storage area has been changed in the context of another document. Whereas onstorage property is an EventHandler for processing storage events.
The syntax would be as below

```javascript
window.onstorage = functionRef;
```

Let's take the example usage of onstorage event handler which logs the storage key and it's values

```javascript
window.onstorage = function (e) {
    console.log(
    "The " +
        e.key +
        " key has been changed from " +
        e.oldValue +
        " to " +
        e.newValue +
        "."
    );
};
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is a Cookie</h2>

A cookie is a piece of data that is stored on your computer to be accessed by your browser. Cookies are saved as key/value pairs.
For example, you can create a cookie named username as below,

```javascript
document.cookie = "username=John";
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Why do you need a Cookie</h2>

Cookies are used to remember information about the user profile(such as username). It basically involves two steps,

1. When a user visits a web page, the user profile can be stored in a cookie. </br>
2. Next time the user visits the page, the cookie remembers the user profile.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the options in a cookie</h2>

There are few below options available for a cookie,

1. By default, the cookie is deleted when the browser is closed but you can change this behavior by setting expiry date (in UTC time).

```javascript
document.cookie = "username=John; expires=Sat, 8 Jun 2019 12:00:00 UTC";
```

1. By default, the cookie belongs to a current page. But you can tell the browser what path the cookie belongs to using a path parameter.

```javascript
document.cookie = "username=John; path=/services";
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you delete a cookie</h2>

You can delete a cookie by setting the expiry date as a passed date. You don't need to specify a cookie value in this case.
For example, you can delete a username cookie in the current page as below.

```javascript
document.cookie =
"username=; expires=Fri, 07 Jun 2019 00:00:00 UTC; path=/;";
```

**Note:** You should define the cookie path option to ensure that you delete the right cookie. Some browsers doesn't allow to delete a cookie unless you specify a path parameter.

**[⬆ Back to Top](#table-of-contents)**