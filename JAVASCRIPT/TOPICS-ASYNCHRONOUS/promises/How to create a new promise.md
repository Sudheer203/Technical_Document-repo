# How to Create a New Promise in JavaScript

## Abstract

Creating a Promise is a fundamental skill in modern JavaScript for handling asynchronous operations. This paper explains how to create a new Promise, its syntax, internal working, parameters, and best practices for writing clean and reliable asynchronous code.

---

## 1. Introduction

JavaScript applications frequently deal with asynchronous operations such as API calls, file handling, and timers. Promises provide a structured way to handle these operations. Understanding how to create a Promise is essential for building scalable and maintainable applications.

---

## 2. What is Creating a Promise?

Creating a Promise means defining an asynchronous operation and specifying what should happen when it succeeds or fails.

A Promise is created using the `Promise` constructor.

---

## 3. Promise Constructor Syntax

```javascript
const promise = new Promise((resolve, reject) => {
  // asynchronous operation
});
```

### Parameters:

* **resolve** → function to call when operation is successful
* **reject** → function to call when operation fails

---

## 4. Basic Example

```javascript
const myPromise = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("Operation successful");
  } else {
    reject("Operation failed");
  }
});
```

### Explanation:

* If `success` is true → Promise is fulfilled
* If false → Promise is rejected

---

## 5. Example with Asynchronous Operation

```javascript
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    const data = "Data received";

    if (data) {
      resolve(data);
    } else {
      reject("Error fetching data");
    }
  }, 1000);
});
```

---

## 6. Consuming the Created Promise

After creating a Promise, it must be handled using `.then()` and `.catch()`.

```javascript
fetchData
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

---

## 7. Internal Working

* Promise starts executing immediately after creation
* Inside the executor function:

  * `resolve()` → moves Promise to fulfilled state
  * `reject()` → moves Promise to rejected state
* Result is sent to the **Microtask Queue**
* Event loop processes it after current execution

---

## 8. Rules for Creating Promises

1. Call **resolve or reject only once**
2. Do not call both resolve and reject
3. Handle errors properly
4. Keep executor function simple

---

## 9. Error Handling in Promise Creation

```javascript
const myPromise = new Promise((resolve, reject) => {
  try {
    let result = riskyOperation();
    resolve(result);
  } catch (error) {
    reject(error);
  }
});
```

---

## 10. Common Mistakes

### 10.1 Not Handling Errors

Ignoring `.catch()` can lead to unhandled promise rejections.

### 10.2 Multiple Calls

Calling `resolve()` or `reject()` multiple times has no effect after the first call.

### 10.3 Heavy Logic Inside Executor

Avoid complex logic inside the Promise constructor.

---

## 11. Best Practices

* Keep Promise creation simple
* Use meaningful resolve/reject messages
* Always handle errors
* Prefer async/await when consuming Promises
* Avoid unnecessary Promise wrapping

---

## 12. Real-World Use Cases

* API calls
* Database queries
* File operations
* Delayed tasks (timers)

---

## 13. Conclusion

Creating a Promise in JavaScript is straightforward using the Promise constructor with `resolve` and `reject` functions. It allows developers to define asynchronous operations clearly and handle success or failure efficiently. Mastering Promise creation is essential for working with modern JavaScript features like async/await and building scalable applications.

---

## 14. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
