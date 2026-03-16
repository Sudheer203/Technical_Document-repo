# Function Hoisting in JavaScript

## Introduction

**Hoisting** in JavaScript means moving declarations to the **top of their scope during the compilation phase**.

Function declarations are **fully hoisted**, which means they can be called **before they are defined in the code**.

---

# 1. Function Declaration Hoisting

A **function declaration** is completely hoisted.

This means the function can be used **before its definition appears in the code**.

### Example

```javascript
greet();

function greet() {
  console.log("Hello JavaScript");
}
````

Output

```
Hello JavaScript
```

Even though `greet()` is called before the function definition, it works because JavaScript hoists the function.

JavaScript internally treats the code like this:

```javascript
function greet() {
  console.log("Hello JavaScript");
}

greet();
```

---

# 2. Function Expression (Not Hoisted)

Function expressions behave differently.

Only the **variable declaration** is hoisted, not the function assignment.

### Example

```javascript
sayHello();

var sayHello = function () {
  console.log("Hello World");
};
```

Output

```
TypeError: sayHello is not a function
```

JavaScript interprets this as:

```javascript
var sayHello;

sayHello();

sayHello = function () {
  console.log("Hello World");
};
```

At the time of calling `sayHello()`, the variable is `undefined`.

---

# 3. Function Expression with let or const

When `let` or `const` is used, the variable is **not initialized before declaration**.

### Example

```javascript
sayHi();

const sayHi = function () {
  console.log("Hi");
};
```

Output

```
ReferenceError
```

This happens because `let` and `const` are inside the **Temporal Dead Zone (TDZ)** until initialization.

---

# 4. Arrow Functions and Hoisting

Arrow functions behave like function expressions.

They are **not hoisted as functions**.

### Example

```javascript
add(2, 3);

const add = (a, b) => {
  return a + b;
};
```

Output

```
ReferenceError
```

---

# Example Comparing Hoisting Types

```javascript
// Function declaration
hello();

function hello() {
  console.log("Hello");
}

// Function expression
greet();

var greet = function () {
  console.log("Greet");
};
```

Output

```
Hello
TypeError
```

---

# Summary

Function hoisting allows **function declarations** to be used before they are defined.

Important rules:

* **Function declarations are fully hoisted**
* **Function expressions are not hoisted**
* **Arrow functions are not hoisted**
* `let` and `const` prevent early access due to the **Temporal Dead Zone**

Understanding hoisting helps avoid unexpected runtime errors.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

---