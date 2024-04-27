### Table of Contents

| No. | Questions                                                                                                                       |
| --- | ------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you display the current date in javascript](#How-do-you-display-the-current-date-in-javascript)                         |
| 2   | [How do you compare two date objects](#How-do-you-compare-two-date-objects)                                                     |
| 3   | [How do you convert date to another timezone in javascript](#How-do-you-convert-date-to-another-timezone-in-javascript)         |
| 4   | [How do you perform language specific date and time formatting](#How-do-you-perform-language-specific-date-and-time-formatting) |
| 5   | [How do get the timezone offset from date](#How-do-get-the-timezone-offset-from-date)                                           |
| 6   | [What is the shortcut to get timestamp](#What-is-the-shortcut-to-get-timestamp)                                                 |

### <h2>How do you display the current date in javascript</h2>

You can use `new Date()` to generate a new Date object containing the current date and time. For example, let's display the current date in mm/dd/yyyy

```javascript
var today = new Date();
var dd = String(today.getDate()).padStart(2, "0");
var mm = String(today.getMonth() + 1).padStart(2, "0"); //January is 0!
var yyyy = today.getFullYear();

today = mm + "/" + dd + "/" + yyyy;
document.write(today); // 04/26/2024
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you compare two date objects</h2>

You need to use date.getTime() method to compare date values instead of comparison operators (==, !=, ===, and !== operators)

```javascript
var d1 = new Date();
var d2 = new Date(d1);
console.log(d1.getTime() === d2.getTime()); //True
console.log(d1 === d2); // False
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you convert date to another timezone in javascript</h2>

You can use the toLocaleString() method to convert dates in one timezone to another. For example, let's convert current date to British English timezone as below,

```javascript
console.log(event.toLocaleString("en-GB", { timeZone: "UTC" })); //29/06/2019, 09:56:00
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you perform language specific date and time formatting</h2>

You can use the `Intl.DateTimeFormat` object which is a constructor for objects that enable language-sensitive date and time formatting. Let's see this behavior with an example,

```javascript
var date = new Date(Date.UTC(2019, 07, 07, 3, 0, 0));
console.log(new Intl.DateTimeFormat("en-GB").format(date)); // 07/08/2019
console.log(new Intl.DateTimeFormat("en-AU").format(date)); // 07/08/2019
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do get the timezone offset from date</h2>

You can use the `getTimezoneOffset` method of the date object. This method returns the time zone difference, in minutes, from current locale (host system settings) to UTC

```javascript
var offset = new Date().getTimezoneOffset();
console.log(offset); // -480
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is the shortcut to get timestamp</h2>

You can use `new Date().getTime()` to get the current timestamp. There is an alternative shortcut to get the value.

```javascript
console.log(+new Date()); // 1714138552088
console.log(Date.now()); // 1714138552094
```

**[⬆ Back to Top](#table-of-contents)**