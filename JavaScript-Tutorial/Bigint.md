<h1>BigInt</h1>

BigInt is a built-in object in JavaScript that provides a way to represent whole numbers larger than 2^53 – 1. The largest number that JavaScript can reliably represent with the Number primitive is 2^53 – 1, which is represented by the MAX_SAFE_INTEGER constant. BigInts are utilized in scenarios where operations on large numbers are necessary due to their ability to represent integers with arbitrary precision.

```javascript
console.log(typeof 100n) // bigint
```

**1. Creating BigInt using BigInt() Function**

```javascript
// Parameter in decimal format
let bigNum = BigInt("123422222222222222222222222222222222222");
console.log(bigNum); // 123422222222222222222222222222222222222n

// Parameter in hexadecimal format
let bigHex = BigInt("0x1ffffffeeeeeeeeef");
console.log(bigHex); // 36893488074118328047n

// Parameter in binary format
let bigBin = BigInt("0b1010101001010101001111111111111111");
console.log(bigBin); // 11430854655n
```

**2. Creating BigInt by appending n**

```javascript
// Decimal format
let bigNum = 123422222222222222222222222222222222222n
console.log(bigNum) // 123422222222222222222222222222222222222n

// Hexadecimal format
let bigHex = 0x1ffffffeeeeeeeeefn
console.log(bigHex) // 36893488074118328047n

// Binary format
let bigBin = 0b1010101001010101001111111111111111n
console.log(bigBin) // 11430854655n
```

**3. Comparing BigInt other types**

A BigInt is similar to a Number in some ways, however, it cannot be used with methods of the builtin Math object and cannot be mixed with instances of Number in operations.

```javascript
console.log(typeof 100n === 100) // false
console.log(typeof 100n === 'bigint') // true
console.log(100n < 101) // true due to coercion
console.log(100n > 101) // Returns true due to coercion
```

**Sorting:** An array can hold both primitive data types and BigInts. This allows the sort() method to work when both normal Number and BigInt values are present in the array.

```javascript
// Number and BigInt
let arr = [4, 2, 5n, 2n]
arr.sort()
console.log(arr)  // [2, 2n, 4, 5n]
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>