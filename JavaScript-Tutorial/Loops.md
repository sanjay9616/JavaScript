<h1>Different Kinds of Loops</h1>

JavaScript Loops are powerful tools for performing repetitive tasks efficiently. Loops in JavaScript execute a block of code again and again while the condition is true.

For example, suppose we want to print “Hello World” 5 times. This can be done using JS Loop easily. In Loop, the statement needs to be written only once and the loop will be executed 5 times as shown below:

```javascript
for (let i = 0; i < 5; i++) {
	console.log("Hello World!");
}
```

### Table of Contents

| No. | Topic                                                     |
| --- | --------------------------------------------------------- |
| 1   | [for Loop](#for-Loop)                                     |
| 2   | [while Loop](#while-Loop)                                 |
| 3   | [do-while Loop](#do-while-Loop)                           |
| 4   | [for-in Loop](#for-in-Loop)                               |
| 5   | [for-of Loop](#for-of-Loop)                               |
| 6   | [Labeled Statement](#Labeled-Statement)                   |
| 7   | [Break Statement](#Break-Statement)                       |
| 8   | [Continue Statement](#Continue-Statement)                 |
| 9   | [Infinite Loop (Loop Error)](#Infinite-Loop-(Loop-Error)) |

### <h2>for Loop</h2>

**Syntax**

```javascript
for (initialization; testing condition; increment/decrement) {
    statement(s)
}
```

**Example:**

```javascript
for (i = 2; i <= 4; i++) {
    console.log("Value of x: " + i);
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>while Loop</h2>

**Syntax**

```javascript
while (boolean condition) {
    loop statements...
}
```

**Example:**

```javascript
let val = 1;
while (val < 6) {
	console.log(val);
	val += 1;
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>do-while Loop</h2>

**Syntax**

```javascript
do {
    Statements...
}
while (condition);
```

**Example:**

```javascript
let test = 1;
do {
	console.log(test);
	test++;
} while(test <= 5)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>for-in Loop</h2>

**Syntax**

```javascript
for(let variable_name in object_name) {
    // Statement
}
```

**Example:**

```javascript
let myObj = { x: 1, y: 2, z: 3 };
for (let key in myObj) {
	console.log(key, myObj[key]);
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>for-of Loop</h2>

**Syntax**

```javascript
for(let variable_name of  object_name) {
    // Statement
}
```

**Example:**

```javascript
let arr = [1, 2, 3, 4, 5];
for (let value of arr) {
	console.log(value);
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Labeled Statement</h2>

**Syntax**

```javascript
Label:
    statement (loop or block of code)
```

**Example:**

```javascript
let sum = 0, a = 1;
// Label for outer loop
outerloop: while (true) {
	a = 1;
	// Label for inner loop
	innerloop: while (a < 3) {
		sum += a;
		if (sum > 12) {
			// Break outer loop from inner loop
			break outerloop;
		}
		console.log("sum = " + sum);
		a++;
	}
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Break Statement</h2>

**Syntax**

```javascript
break;
```

**Example:**

```javascript
for (let i = 1; i < 6; i++) {
	if (i == 4)
		break;
	console.log(i);
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Continue Statement</h2>

**Syntax**

```javascript
continue;
```

**Example:**

```javascript
for (let i = 0; i < 11; i++) {
	if (i % 2 == 0)
		continue;
	console.log(i);
}
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Infinite Loop (Loop Error)</h2>

```javascript
for (let i = 5; i != 0; i -= 2) {
	console.log(i);
}

let x = 5;
while (x == 5) {
	console.log("In the loop");
}
```
**[⬆ Back to Top](#table-of-contents)**

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
