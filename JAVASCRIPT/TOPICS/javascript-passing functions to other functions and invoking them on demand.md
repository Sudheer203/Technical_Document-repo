# Passing Functions to Other Functions and Invoking Them on Demand

## Introduction

In JavaScript, **functions are first-class values**.  
This means a function can be:

```

stored in a variable
passed to another function
returned from a function

```

Passing a function to another function allows **flexible and reusable code**.

---

# Basic Example

A function can be passed as an argument.

```javascript
function greet(name) {
  console.log("Hello " + name);
}

function processUser(callback) {
  callback("Sudheer");
}

processUser(greet);
```

Output

```
Hello Sudheer
```

Explanation

```
greet is passed as a function
processUser calls it when needed
```

---

# Invoking Function on Demand

The receiving function decides **when to execute the function**.

```javascript
function sayHi() {
  console.log("Hi!");
}

function runTask(task) {
  console.log("Starting task");
  task();
  console.log("Task finished");
}

runTask(sayHi);
```

Output

```
Starting task
Hi!
Task finished
```

The function is **invoked inside another function**.

---

# Using Anonymous Functions

Instead of passing a named function, we can pass an anonymous function.

```javascript
function runTask(task) {
  task();
}

runTask(function () {
  console.log("Running anonymous task");
});
```

Output

```
Running anonymous task
```

---

# Using Arrow Functions

Arrow functions are commonly used when passing functions.

```javascript
function runTask(task) {
  task();
}

runTask(() => {
  console.log("Arrow function executed");
});
```

Output

```
Arrow function executed
```

---

# Practical Example: Custom Calculator

```javascript
function calculate(a, b, operation) {
  return operation(a, b);
}

function add(x, y) {
  return x + y;
}

function multiply(x, y) {
  return x * y;
}

console.log(calculate(5, 3, add));
console.log(calculate(5, 3, multiply));
```

Output

```
8
15
```

The `operation` function is **selected and executed dynamically**.

---

# Example With Array Utility Methods

Array methods often accept functions.

```javascript
const numbers = [1, 2, 3];

numbers.forEach(function (n) {
  console.log(n);
});
```

Output

```
1
2
3
```

Here, the function is passed to `forEach`.

---

# Why This Pattern Is Useful

Passing functions enables:

```
reusable code
flexible behavior
cleaner program structure
```

Example structure

```javascript
function main(task) {
  task();
}
```

Different functions can be passed to `main`.

---

# Summary

JavaScript allows functions to be **passed as arguments** and **executed later**.

Basic pattern

```javascript
function runner(callback) {
  callback();
}

runner(myFunction);
```

This pattern is widely used in:

```
callbacks
array methods
event handling
asynchronous programming
```

It makes JavaScript **more flexible and powerful**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---