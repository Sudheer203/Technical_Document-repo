# How to Promisify an Asynchronous Callback-Based Function in JavaScript

## Abstract

Promisification is the process of converting a callback-based asynchronous function into a Promise-based one. This enables developers to use modern patterns like `.then()` chaining and `async/await`, improving readability and maintainability. This paper explains how to promisify functions such as `setTimeout` and `fs.readFile`, the underlying concepts, and best practices.

---

## 1. Introduction

Before Promises, JavaScript relied heavily on callbacks for asynchronous operations. While effective, callbacks often lead to complex and hard-to-maintain code. Promisification bridges this gap by wrapping callback-based APIs into Promises, enabling cleaner and more structured code.

---

## 2. What is Promisification?

Promisification is the technique of:

Converting a function that uses a callback into a function that returns a Promise.

---

## 3. Callback-Based Function Structure

Most asynchronous callback functions follow this pattern:

```javascript
function asyncFunction(arg, callback) {
  // callback(error, result)
}
```

Example:

```javascript
fs.readFile("file.txt", (err, data) => {
  if (err) {
    console.error(err);
  } else {
    console.log(data);
  }
});
```

---

## 4. Basic Promisification Pattern

```javascript
function promisifiedFunction(arg) {
  return new Promise((resolve, reject) => {
    asyncFunction(arg, (err, result) => {
      if (err) {
        reject(err);
      } else {
        resolve(result);
      }
    });
  });
}
```

---

## 5. Example: Promisifying `setTimeout`

### Callback Version:

```javascript
setTimeout(() => {
  console.log("Executed after delay");
}, 1000);
```

### Promisified Version:

```javascript
function delay(ms) {
  return new Promise((resolve) => {
    setTimeout(resolve, ms);
  });
}

delay(1000).then(() => console.log("Executed after delay"));
```

---

## 6. Example: Promisifying `fs.readFile`

### Callback Version:

```javascript
const fs = require("fs");

fs.readFile("file.txt", "utf8", (err, data) => {
  if (err) console.error(err);
  else console.log(data);
});
```

### Promisified Version:

```javascript
const fs = require("fs");

function readFilePromise(path) {
  return new Promise((resolve, reject) => {
    fs.readFile(path, "utf8", (err, data) => {
      if (err) reject(err);
      else resolve(data);
    });
  });
}

readFilePromise("file.txt")
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

---

## 7. Using Built-in Promisify (Node.js)

Node.js provides a utility to simplify promisification:

```javascript
const { promisify } = require("util");
const fs = require("fs");

const readFileAsync = promisify(fs.readFile);

readFileAsync("file.txt", "utf8")
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

---

## 8. Using Async/Await with Promisified Functions

```javascript
async function readData() {
  try {
    const data = await readFilePromise("file.txt");
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

---

## 9. Advantages of Promisification

* Avoids callback hell
* Improves readability
* Enables chaining with `.then()`
* Works with async/await
* Centralized error handling

---

## 10. Common Mistakes

### 10.1 Not Handling Errors

```javascript
resolve(data); // ignoring error
```

### 10.2 Forgetting to Return Promise

```javascript
function fn() {
  new Promise(...); // missing return
}
```

### 10.3 Multiple Callback Calls

* Ensure callback is called only once

---

## 11. Best Practices

* Always follow `(err, result)` pattern
* Reject on error, resolve on success
* Use `util.promisify` when available
* Avoid wrapping already Promise-based APIs
* Keep functions simple and reusable

---

## 12. When to Use Promisification

* Working with legacy callback APIs
* Migrating old code to modern JavaScript
* Improving code readability
* Integrating with async/await

---

## 13. Conclusion

Promisification is a powerful technique that transforms callback-based asynchronous code into a more modern and maintainable Promise-based structure. By wrapping functions like `setTimeout` and `fs.readFile`, developers can leverage the full benefits of Promises, including chaining, centralized error handling, and compatibility with async/await. Understanding this concept is essential for writing clean and scalable JavaScript applications.

---

## 14. References

* MDN Web Docs
* Node.js Documentation
* JavaScript.info
* ECMAScript Specification

---
