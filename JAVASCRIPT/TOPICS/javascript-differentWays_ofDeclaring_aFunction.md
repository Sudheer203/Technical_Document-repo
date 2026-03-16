# Different Ways of Declaring a Function in JavaScript

## Introduction

Functions are reusable blocks of code used to perform tasks.

JavaScript allows functions to be declared in **multiple ways**.  
Each method has different behavior and use cases.

Common ways to declare functions:

```

1. Function Declaration
2. Function Expression
3. Arrow Function
4. Anonymous Function
5. Immediately Invoked Function Expression (IIFE)

```
---

# 1. Function Declaration

A **function declaration** defines a named function using the `function` keyword.

### Example

```javascript
function greet() {
  console.log("Hello World");
}

greet();
```
### With Parameters

```javascript
function add(a, b) {
  return a + b;
}

console.log(add(3, 4));
```

* Has a name
* Can be called before definition (hoisted)

---

# 2. Function Expression

A **function expression** stores a function inside a variable.

### Example

```javascript
const greet = function () {
  console.log("Hello JavaScript");
};

greet();
```

### With Parameters

```javascript
const multiply = function (a, b) {
  return a * b;
};

console.log(multiply(3, 5));
```

* Function is assigned to a variable
* Not hoisted like function declarations

---

# 3. Arrow Function

Arrow functions were introduced in **ES6**.
They provide a shorter syntax for writing functions.

### Example

```javascript
const greet = () => {
  console.log("Hello");
};

greet();
```

### Single Line Function

```javascript
const add = (a, b) => a + b;

console.log(add(2, 6));
```

* Short syntax
* Common in modern JavaScript

---

# 4. Anonymous Function

An **anonymous function** is a function **without a name**.

Usually used inside other functions.

### Example

```javascript
setTimeout(function () {
  console.log("Executed after 1 second");
}, 1000);
```

Anonymous functions are often used in:

```
callbacks
event handlers
array methods
```

---

# 5. Immediately Invoked Function Expression (IIFE)

An **IIFE** runs immediately after it is defined.

### Example

```javascript
(function () {
  console.log("I run immediately");
})();
```

### Example with Parameters

```javascript
(function (name) {
  console.log("Hello " + name);
})("Sudheer");
```

IIFE is useful for creating **private scope**.

---

# Example Comparing Different Function Types

```javascript
// Function Declaration
function sayHello() {
  console.log("Hello");
}

// Function Expression
const sayHi = function () {
  console.log("Hi");
};

// Arrow Function
const sayBye = () => {
  console.log("Bye");
};

sayHello();
sayHi();
sayBye();
```

---

# Summary

JavaScript provides multiple ways to declare functions.

```
Function Declaration → traditional method
Function Expression → function stored in a variable
Arrow Function → modern and shorter syntax
Anonymous Function → function without a name
IIFE → function executed immediately
```

Understanding these different methods helps developers write **clean and flexible JavaScript code**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

---
