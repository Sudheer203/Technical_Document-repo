# Importing and Exporting Modules using `require` and `module.exports`

## Introduction

In Node.js, code can be divided into **modules**.  
Modules help organize code into **separate files**.

To share code between files we use:

```

module.exports → export from a file
require() → import into another file

```

---

# Basic Module Structure

Project example:

```

project/
│
├── math.js
└── app.js

```

---

# Exporting a Function

### math.js

```javascript
function add(a, b) {
  return a + b;
}

module.exports = add;
````

Here we export the `add` function so other files can use it.

---

# Importing the Module

### app.js

```javascript
const add = require("./math");

const result = add(5, 3);

console.log(result);
```

Output

```
8
```

`require("./math")` loads the module.

---

# Exporting Multiple Functions

You can export multiple functions using an object.

### math.js

```javascript
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

module.exports = {
  add,
  subtract
};
```

---

# Importing Multiple Functions

### app.js

```javascript
const math = require("./math");

console.log(math.add(10, 5));
console.log(math.subtract(10, 5));
```

Output

```
15
5
```

---

# Destructuring Import

Instead of accessing methods through an object, we can destructure.

### app.js

```javascript
const { add, subtract } = require("./math");

console.log(add(4, 2));
console.log(subtract(4, 2));
```

Output

```
6
2
```

---

# Exporting Variables

Modules can also export variables.

### config.js

```javascript
const appName = "My App";
const version = "1.0";

module.exports = {
  appName,
  version
};
```

---

# Importing Variables

### app.js

```javascript
const config = require("./config");

console.log(config.appName);
console.log(config.version);
```

Output

```
My App
1.0
```

---

# Important Notes

```
require() loads a module
module.exports defines what the module exposes
each file in Node.js is treated as a module
```

---

# Example: Simple Utility Module

### utils.js

```javascript
function greet(name) {
  return "Hello " + name;
}

function square(n) {
  return n * n;
}

module.exports = {
  greet,
  square
};
```

### index.js

```javascript
const { greet, square } = require("./utils");

console.log(greet("Sudheer"));
console.log(square(5));
```

Output

```
Hello Sudheer
25
```

---

# Summary

Node.js modules allow developers to **split code into reusable files**.

Basic pattern:

```javascript
// export
module.exports = something;

// import
const something = require("./file");
```

Using modules improves:

```
code organization
reusability
maintainability
```

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---