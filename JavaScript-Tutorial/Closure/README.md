<h1>Closure in JS</h1>

A closure is the combination of function bundle togather (enclosed) with references to it's surrounding state (the laxical environment).

A Function bind togather with it's laxical environment (surrounding state), forms a closure.

In other words, a closure gives you access to another's scope from inner function. In javascript, closure are created every time a function is created, at function creation time.

```javascript
function x() {
    var a = 7; // closure
    function y() {
        console.log(a)
    }
    y();
}
x();
```

**`A closure is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function’s variables`**. The closure has three scope chains

1. Own scope where variables defined between its curly brackets <br>
2. Outer function’s variables <br>
3. Global variables <br>

Let's take an example of closure concept,

```javascript
function Welcome(name) {
    var greetingInfo = function (message) {
        console.log(message + " " + name);
    };
    return greetingInfo;
}
var myFunction = Welcome("John");
myFunction("Welcome "); //Output: Welcome John
myFunction("Hello Mr."); //output: Hello Mr.John
```

As per the above code, the inner function(i.e, greetingInfo) has access to the variables in the outer function scope(i.e, Welcome) even after the outer function has returned.

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>