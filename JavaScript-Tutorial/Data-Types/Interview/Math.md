### Table of Contents

| No. | Questions                                                                                                                                                 |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [Can you write a random integers function to print integers with in a range](#Can-you-write-a-random-integers-function-to-print-integers-with-in-a-range) |
| 2   | [How do you generate random integers](#How-do-you-generate-random-integers)                                                                               |

### <h2>Can you write a random integers function to print integers with in a range</h2>

Yes, you can create a proper random function to return a random number between min and max (both included)

```javascript
function randomInteger(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
randomInteger(1, 100); // returns a random integer from 1 to 100
randomInteger(1, 1000); // returns a random integer from 1 to 1000
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>How do you generate random integers</h2>

You can use Math.random() with Math.floor() to return random integers. For example, if you want generate random integers between 1 to 10, the multiplication factor should be 10,

```javascript
Math.floor(Math.random() * 10) + 1; // returns a random integer from 1 to 10
Math.floor(Math.random() * 100) + 1; // returns a random integer from 1 to 100
```

**Note:** Math.random() returns a random number between 0 (inclusive), and 1 (exclusive)

**[⬆ Back to Top](#table-of-contents)**