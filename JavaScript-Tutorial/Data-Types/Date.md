<h1>JavaScript Date Objects</h1>

By default, JavaScript will use the browser's time zone and display a date as a full text string

**Sun Apr 14 2024 12:49:34 GMT+0530 (India Standard Time)**

### Table of Contents

| No. | Topic                               |
| --- | ----------------------------------- |
| 1   | [JS Dates](#JS-Dates)               |
| 2   | [JS Date Formats](#JS-Date-Formats) |

### <h2>JS Dates</h2>

<h3>Creating Date Objects</h3>

Date objects are created with the new Date() constructor. </br>
There are 9 ways to create a new date object

```javascript
new Date()
new Date(date string)
new Date(year,month)
new Date(year,month,day)
new Date(year,month,day,hours)
new Date(year,month,day,hours,minutes)
new Date(year,month,day,hours,minutes,seconds)
new Date(year,month,day,hours,minutes,seconds,ms)
new Date(milliseconds)
```
<h3>JavaScript new Date()</h3>

new Date() creates a date object with the current date and time

**Note:** JavaScript counts months from 0 (January) to 11 (December)

```javascript
const d = new Date();
console.log(d) // 2024-04-14T07:30:11.386Z

const d = new Date("October 13, 2014 11:13:00");
console.log(d) // 2014-10-13T11:13:00.000Z

const d = new Date("2022-03-25");
console.log(d) // 2022-03-25T00:00:00.000Z

const d = new Date(2018, 11, 24, 10, 33, 30, 0);
console.log(d) // 2018-12-24T10:33:30.000Z

const d1 = new Date(2018, 15, 24, 10, 33, 30);
const d2 = new Date(2019, 3, 24, 10, 33, 30);
console.log(d1, d2) // 2019-04-24T10:33:30.000Z 2019-04-24T10:33:30.000Z (d1 is same as d2)

const d1 = new Date(2018, 5, 35, 10, 33, 30);
const d2 = new Date(2018, 6, 5, 10, 33, 30);
console.log(d1, d2) // 2018-07-05T10:33:30.000Z 2018-07-05T10:33:30.000Z (d1 is same as d2)
```

**Previous Century** One and two digit years will be interpreted as 19xx

```javascript
const d = new Date(99, 11, 24);
console.log(d) // 1999-12-24T00:00:00.000Z
```

<h3>JavaScript Stores Dates as Milliseconds</h3>

JavaScript stores dates as number of milliseconds since January 01, 1970.

<h3>toDateString() Method</h3>

The toDateString() method converts a date to a more readable format:

```javascript
const d = new Date();
d.toDateString();
console.log(d) // 2024-04-14T09:15:12.560Z
```

<h3>toUTCString() Method</h3>

The toUTCString() method converts a date to a string using the UTC standard

```javascript
const d = new Date();
d.toUTCString();
console.log(d) // 2024-04-14T09:16:29.783Z
```

<h3>toISOString() Method</h3>

The toISOString() method converts a date to a string using the ISO standard

```javascript
const d = new Date();
d.toISOString();
console.log(d) // 2024-04-14T09:34:07.521Z
````

**[⬆ Back to Top](#table-of-contents)**

### <h2>JS Date Formats</h2>

**[⬆ Back to Top](#table-of-contents)**


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>

