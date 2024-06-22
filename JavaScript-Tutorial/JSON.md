<h1>JavaScript JSON</h1>

**JSON** is a text-based data format following JavaScript object syntax, which was popularized by Douglas Crockford. It is useful when you want to transmit data across a network. It is basically just a text file with an extension of .json, and a MIME type of application/json.

**Example:**

```javascript
{
    "employees":[
        {"firstName":"John", "lastName":"Doe"},
        {"firstName":"Anna", "lastName":"Smith"},
        {"firstName":"Peter", "lastName":"Jones"}
    ]
}

{ "firstName": "John", "lastName": "Doe" }
```

**JSON Syntax Rules:**
1. Data is in name/value pairs, A name/value pair consists of a field name (in double quotes), followed by a colon `"firstName":"John"` </br>
2. Data is separated by commas </br>
3. Curly braces hold objects </br>
4. Square brackets hold arrays </br>

<h2>Common Operations</h2>

**Parsing:** Converting a string to a native object

```javascript
JSON.parse(text);
```

**Stringification:** Converting a native object to a string so that it can be transmitted across the network

```javascript
JSON.stringify(object);
```

**Examples**

```javascript
const myObj = {name: "John", age: 31, city: "New York"};
const myJSON = JSON.stringify(myObj)
console.log(myJSON, typeof myJSON) // {"name":"John","age":31,"city":"New York"} string

const myJSON = '{"name":"John", "age":31, "city":"New York"}';
const myObj = JSON.parse(myJSON);
console.log(myObj, typeof myObj) // { name: 'John', age: 31, city: 'New York' } object
```


<h2><a href="https://github.com/sanjay9616/JavaScript/blob/master/JavaScript-Tutorial/README.md"> 🔙 Back</a></h2>
