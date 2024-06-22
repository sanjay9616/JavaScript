<h1>this keyword in Javascript</h1>

represents the current context, or it can access variable, properties, and methods within it's scope.

```javascript
let user = {
    name: "Sanjay",
    salary: 21,
    welcomeMsg: function() {
        console.log(`Welcome ${this.name}`);
    }
}
user.welcomeMsg() // Welcome Sanjay
user.name = "Anurag"
user.welcomeMsg() // Welcome Anurag
```

```javascript
let user = {
    name: "Sanjay",
    printThis: function() {
        console.log(this);
    }
}
user.printThis() // { name: 'Sanjay', printThis: [Function: printThis] }
user.name = "Anurag"
user.printThis() // { name: 'Anurag', printThis: [Function: printThis] }
```

<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>