<h1>JavaScript Math Objects</h1>

### <h2>JS Math Methods</h2>

| Method               | Description                                                                   |
| -------------------- | ----------------------------------------------------------------------------- |
| abs(x)               | Returns the absolute value of x                                               |
| acos(x)              | Returns the arccosine of x, in radians                                        |
| acosh(x)             | Returns the hyperbolic arccosine of x                                         |
| asin(x)              | Returns the arcsine of x, in radians                                          |
| asinh(x)             | Returns the hyperbolic arcsine of x                                           |
| atan(x)              | Returns the arctangent of x as a numeric value between -PI/2 and PI/2 radians |
| atan2(y, x)          | Returns the arctangent of the quotient of its arguments                       |
| atanh(x)             | Returns the hyperbolic arctangent of x                                        |
| cbrt(x)              | Returns the cubic root of x                                                   |
| ceil(x)              | Returns x, rounded upwards to the nearest integer                             |
| cos(x)               | Returns the cosine of x (x is in radians)                                     |
| cosh(x)              | Returns the hyperbolic cosine of x                                            |
| exp(x)               | Returns the value of Ex                                                       |
| floor(x)             | Returns x, rounded downwards to the nearest integer                           |
| log(x)               | Returns the natural logarithm (base E) of x                                   |
| max(x, y, z, ..., n) | Returns the number with the highest value                                     |
| min(x, y, z, ..., n) | Returns the number with the lowest value                                      |
| pow(x, y)            | Returns the value of x to the power of y                                      |
| random()             | Returns a random number between 0 and 1                                       |
| round(x)             | Rounds x to the nearest integer                                               |
| sign(x)              | Returns if x is negative, null or positive (-1, 0, 1)                         |
| sin(x)               | Returns the sine of x (x is in radians)                                       |
| sinh(x)              | Returns the hyperbolic sine of x                                              |
| sqrt(x)              | Returns the square root of x                                                  |
| tan(x)               | Returns the tangent of an angle                                               |
| tanh(x)              | Returns the hyperbolic tangent of a number                                    |
| trunc(x)             | Returns the integer part of a number (x)                                      |

<h3>Math Properties (Constants)</h3>

JavaScript provides 8 mathematical constants that can be accessed as Math properties:

```javascript
Math.E        // returns Euler's number
Math.PI       // returns PI
Math.SQRT2    // returns the square root of 2
Math.SQRT1_2  // returns the square root of 1/2
Math.LN2      // returns the natural logarithm of 2
Math.LN10     // returns the natural logarithm of 10
Math.LOG2E    // returns base 2 logarithm of E
Math.LOG10E   // returns base 10 logarithm of E
```

<h3>Number to Integer</h3>

```javascript
// Math.round() - returns the nearest integer
Math.round(4.6); // 5
Math.round(4.5); // 5
Math.round(4.4); // 4

// Math.ceil() - returns the value of x rounded up to its nearest integer
Math.ceil(4.9); // 5
Math.ceil(4.7); // 5
Math.ceil(4.4); // 5
Math.ceil(4.2); // 5
Math.ceil(-4.2); // -4

// Math.floor() - returns the value of x rounded down to its nearest integer
Math.floor(4.9); // 4
Math.floor(4.7); // 4
Math.floor(4.4); // 4
Math.floor(4.2); // 4
Math.floor(-4.2); // -5

// Math.trunc() - returns the integer part of x
Math.trunc(4.9); // 4
Math.trunc(4.7); // 4
Math.trunc(4.4); // 4
Math.trunc(4.2); // 2
Math.trunc(-4.2); // -4
```

```javascript
// Math.sign() - returns if x is negative, null or positive
Math.sign(-4); // -1
Math.sign(0); // 0
Math.sign(4); // 4

// Math.pow() - returns the value of x to the power of y
Math.pow(8, 2) // 64

// Math.sqrt() - returns the square root of x
Math.sqrt(64) // 8

// Math.abs() - returns the absolute (positive) value of x
Math.abs(-4.7); // 4.7

Math.sin(90 * Math.PI / 180);     // returns 1 (the sine of 90 degrees)
Math.cos(0 * Math.PI / 180);     // returns 1 (the cos of 0 degrees)

Math.min(0, 150, 30, 20, -8, -200); // -8
Math.max(0, 150, 30, 20, -8, -200); // 150

// Math.random() - returns a random number between 0 (inclusive), and 1 (exclusive):
Math.random(); // 0.07168919000548124

// Math.log(x) returns the natural logarithm of x.
Math.log(1); // 0
Math.log(2); // 0.6931471805599453
Math.log(3); // 1.0986122886681096

// Math.log2(x) returns the base 2 logarithm of x.
Math.log2(8); // 3
Math.log10(1000); // 3
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
