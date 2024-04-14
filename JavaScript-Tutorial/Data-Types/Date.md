<h1>JavaScript Date Objects</h1>

By default, JavaScript will use the browser's time zone and display a date as a full text string

**Sun Apr 14 2024 12:49:34 GMT+0530 (India Standard Time)**

### Table of Contents

| No. | Topic                                       |
| --- | ------------------------------------------- |
| 1   | [JS Dates](#JS-Dates)                       |
| 2   | [JS Date Formats](#JS-Date-Formats)         |
| 3   | [JS Get Date Methods](#JS-Get-Date-Methods) |
| 4   | [JS Set Date Methods](#JS-Set-Date-Methods) |

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
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JS Date Formats</h2>

<h3>JavaScript Date Input</h3>

There are generally 3 types of JavaScript date input formats:

**ISO Date:** "2015-03-25" (The International Standard) </br>
**Short Date:** "03/25/2015" </br>
**Long Date:** "Mar 25 2015" or "25 Mar 2015" </br>

<h3>JavaScript ISO Dates</h3>

SO 8601 is the international standard for the representation of dates and times. </br>
The ISO 8601 syntax (YYYY-MM-DD) is also the preferred JavaScript date format:

```javascript
const d = new Date("2015-03-25");
console.log(d) // 2015-03-25T00:00:00.000Z

const d = new Date("2015-03"); // ISO dates can be written without specifying the day (YYYY-MM)
console.log(d) // 2015-03-01T00:00:00.000Z

const d = new Date("2015"); // ISO dates can be written without month and day (YYYY)
console.log(d) // 2015-01-01T00:00:00.000Z

const d = new Date("2015-03-25T12:00:00Z"); // ISO dates can be written with added hours, minutes, and seconds (YYYY-MM-DDTHH:MM:SSZ)
console.log(d) // 2015-03-25T12:00:00.000Z

const d = new Date("2015-03-25T12:00:00-06:30") // If you want to modify the time relative to UTC, remove the Z and add +HH:MM or -HH:MM instead
console.log(d) // 2015-03-25T18:30:00.000Z
```

**Time Zones**

When setting a date, without specifying the time zone, JavaScript will use the browser's time zone. </br>
When getting a date, without specifying the time zone, the result is converted to the browser's time zone. </br>
In other words: If a date/time is created in GMT (Greenwich Mean Time), the date/time will be converted to CDT (Central US Daylight Time) if a user browses from central US

<h3>JavaScript Short Dates</h3>

```javascript
const d = new Date("03/25/2015");
const d = new Date("2015/3/25"); // In some browsers, months or days with no leading zeroes may produce an error
```

<h3>JavaScript Long Dates</h3>

Long dates are most often written with a "MMM DD YYYY" syntax like this

```javascript
// Month and day can be in any order:
const d = new Date("Mar 25 2015");
const d = new Date("25 Mar 2015");

// month can be written in full (January), or abbreviated (Jan):
const d = new Date("January 25 2015");
const d = new Date("Jan 25 2015");

// Commas are ignored. Names are case insensitive:
const d = new Date("JANUARY, 25, 2015");
```

<h3>Date Input - Parsing Dates</h3>

If you have a valid date string, you can use the Date.parse() method to convert it to milliseconds. </br>
Date.parse() returns the number of milliseconds between the date and January 1, 1970:

```javascript
let msec = Date.parse("March 21, 2012");
console.log(msec) // 1332288000000

let msec = Date.parse("Jan 01, 1970");
console.log(msec) // 0

let msec = Date.parse("March 21, 2012"); // You can then use the number of milliseconds to convert it to a date object:
const d = new Date(msec);
console.log(d) // 2012-03-21T00:00:00.000Z
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JS Get Date Methods</h2>

| Method            | Description                                   |
| ----------------- | --------------------------------------------- |
| getFullYear()     | Get year as a four digit number (yyyy)        |
| getMonth()        | Get month as a number (0-11)                  |
| getDate()         | Get day as a number (1-31)                    |
| getDay()          | Get weekday as a number (0-6)                 |
| getHours()        | Get hour (0-23)                               |
| getMinutes()      | Get minute (0-59)                             |
| getSeconds()      | Get second (0-59)                             |
| getMilliseconds() | Get millisecond (0-999)                       |
| getTime()         | Get time (milliseconds since January 1, 1970) |

**0 menans first day (sunday), first month (january)**

```javascript
const d = new Date("2021-03-25");
console.log(d.getFullYear()) // 2021
console.log(d.getMonth()) // 2
console.log(d.getDate()) // 25

const d = new Date();
console.log(d.getHours()) // 11
console.log(d.getMinutes()) // 22
console.log(d.getSeconds()) // 43
console.log(d.getMilliseconds()) // 628
console.log(d.getDay()) // 0

console.log(d.getTime()) // 1713094028929
```

<h3>The Date.now() Method</h3>

Date.now() returns the number of milliseconds since January 1, 1970.

```javascript
let ms = Date.now();
console.log(ms) // 1713094170703

// Calculate the number of years since 1970/01/01:
const minute = 1000 * 60;
const hour = minute * 60;
const day = hour * 24;
const year = day * 365;
let years = Math.round(Date.now() / year);
console.log(years) // 54
```

<h3>UTC Date Get Methods</h3>

**Add UTC before above methods** ex - getUTCDate(), getUTCFullYear(), getUTCMonth(), getUTCDay(), getUTCHours(), getUTCMinutes(), getUTCSeconds(), getUTCMilliseconds()

<h3>The getTimezoneOffset() Method</h3>

The getTimezoneOffset() method returns the difference (in minutes) between local time an UTC time

```javascript
let d = new Date()
let diff = d.getTimezoneOffset();
console.log(diff)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>JS Date Methods</h2>

| Method            | Description                                       |
| ----------------- | ------------------------------------------------- |
| setFullYear()     | Set the year (optionally month and day)           |
| setMonth()        | Set the month (0-11)                              |
| setDate()         | Set the day as a number (1-31)                    |
| setHours()        | Set the hour (0-23)                               |
| setMinutes()      | Set the minutes (0-59)                            |
| setSeconds()      | Set the seconds (0-59)                            |
| setMilliseconds() | Set the milliseconds (0-999)                      |
| setTime()         | Set the time (milliseconds since January 1, 1970) |


```javascript
const d = new Date();
d.setFullYear(2020);
console.log(d) // 2020-04-14T11:41:25.690Z

const d = new Date();
d.setFullYear(2020, 11, 3); // The setFullYear() method can optionally set month and day
console.log(d) // 2020-12-03T11:41:55.308Z

const d = new Date();
d.setMonth(11); // 2024-12-14T11:42:41.830Z

const d = new Date();
d.setDate(15); // 2024-04-15T11:43:03.298Z

const d = new Date();
d.setDate(d.getDate() + 50); // The setDate() method can also be used to add days to a date
console.log(d) // 2024-06-03T11:43:43.789Z

const d = new Date();
d.setHours(22);
console.log(d) // 2024-04-14T22:44:49.967Z

const d = new Date();
d.setMinutes(30);
console.log(d) // 2024-04-14T11:30:13.874Z

const d = new Date();
d.setSeconds(30);
console.log(d) // 2024-04-14T11:45:30.560Z
```

**Compare Dates**

```javascript
let text = "";
const today = new Date();
const someday = new Date();
someday.setFullYear(2100, 0, 14);
if (someday > today) {
  text = "Today is before January 14, 2100.";
} else {
  text = "Today is after January 14, 2100.";
}
```

**[⬆ Back to Top](#table-of-contents)**


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/Data-Types/README.md"> 🔙 Back</a></h2>

