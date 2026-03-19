# How to Consume Multiple Promises Using `Promise.all()` in JavaScript

## Abstract

Handling multiple asynchronous operations efficiently is a key requirement in modern JavaScript applications. `Promise.all()` provides a powerful way to execute multiple Promises in parallel and consume their results collectively. This paper explains how `Promise.all()` works, its syntax, behavior, advantages, limitations, and best practices.

---

## 1. Introduction

In real-world applications, developers often need to perform multiple independent asynchronous tasks, such as fetching data from multiple APIs. Executing these tasks sequentially can be inefficient. `Promise.all()` allows these operations to run in parallel, improving performance and simplifying code.

---

## 2. What is `Promise.all()`?

`Promise.all()` is a static method that takes an array (or iterable) of Promises and returns a single Promise.

In simple words:
It runs all Promises **at the same time** and waits for all of them to complete.

---

## 3. Syntax

```javascript
Promise.all([promise1, promise2, promise3])
  .then(results => {
    // array of results
  })
  .catch(error => {
    // if any promise fails
  });
```

---

## 4. Basic Example

```javascript
const p1 = Promise.resolve(10);
const p2 = Promise.resolve(20);
const p3 = Promise.resolve(30);

Promise.all([p1, p2, p3])
  .then(results => {
    console.log(results);
  })
  .catch(err => console.error(err));
```

### Output:

```
[10, 20, 30]
```

---

## 5. How It Works

* Accepts multiple Promises
* Executes them in parallel
* Waits until **all are fulfilled**
* Returns results as an array (in order)

---

## 6. Real-World Example

```javascript
Promise.all([
  fetchUser(),
  fetchOrders(),
  fetchProducts()
])
  .then(([user, orders, products]) => {
    console.log(user, orders, products);
  })
  .catch(err => console.error(err));
```

### Flow:

1. All API calls start together
2. Wait for all responses
3. Process results together

---

## 7. Important Behavior

### 7.1 Order is Preserved

Even if Promises resolve at different times, results maintain input order.

### 7.2 Fail Fast Behavior

If **any Promise fails**, `Promise.all()` immediately rejects.

```javascript
const p1 = Promise.resolve(10);
const p2 = Promise.reject("Error");
const p3 = Promise.resolve(30);

Promise.all([p1, p2, p3])
  .then(console.log)
  .catch(err => console.log(err));
```

### Output:

```
Error
```

---

## 8. Handling Errors

* Single `.catch()` handles failure
* No partial results returned
* All other Promises are ignored after rejection

---

## 9. Using Non-Promise Values

```javascript
Promise.all([1, Promise.resolve(2), 3])
  .then(results =>
```
# How to Do Error Handling When Using Promises in JavaScript

## Abstract

Error handling is a crucial aspect of working with Promises in JavaScript. Since asynchronous operations can fail for various reasons, developers must implement robust mechanisms to detect, propagate, and handle errors effectively. This paper explains different ways to handle errors in Promises, including `.catch()`, error propagation, chaining strategies, and best practices.

---

## 1. Introduction

Promises provide a structured way to manage asynchronous operations and their outcomes. Unlike traditional callbacks, Promises offer a unified and predictable approach to error handling. Understanding how to properly handle errors ensures stability, maintainability, and better debugging in applications.

---

## 2. Types of Errors in Promises

Errors in Promises generally occur in two ways:

### 2.1 Rejected Promises

```javascript
Promise.reject("Something failed");
```

### 2.2 Thrown Errors

```javascript
Promise.resolve()
  .then(() => {
    throw new Error("Unexpected error");
  });
```

👉 Both result in a **rejected Promise**

---

## 3. Using `.catch()` for Error Handling

The primary way to handle errors is using `.catch()`.

```javascript
doTask()
  .then(result => console.log(result))
  .catch(error => console.error(error));
```

* Catches all errors from previous `.then()` blocks
* Acts as a centralized error handler

---

## 4. Error Propagation (Bubbling)

Errors automatically propagate down the chain until handled.

```javascript
Promise.resolve(10)
  .then(num => num * 2)
  .then(() => {
    throw new Error("Error occurred");
  })
  .then(() => console.log("Skipped"))
  .catch(err => console.log(err.message));
```

---

## 5. Handling Errors at Specific Steps

You can handle errors at intermediate steps:

```javascript
step1()
  .then(step2)
  .catch(err => {
    console.log("Handled step2 error");
    return defaultValue;
  })
  .then(step3)
  .catch(err => console.error("Final error:", err));
```

---

## 6. Using `.then()` Second Argument

`.then()` can also accept an error handler:

```javascript
promise.then(
  result => console.log(result),
  error => console.error(error)
);
```

⚠️ Not recommended for complex chains because it breaks error flow.

---

## 7. Throwing Errors for Control

```javascript
.then(data => {
  if (!data) {
    throw new Error("Invalid data");
  }
  return data;
})
```

* Helps validate data
* Passes error to `.catch()`

---

## 8. Recovery After Error

You can recover and continue execution:

```javascript
Promise.reject("Error")
  .catch(err => {
    console.log("Recovered");
    return 100;
  })
  .then(value => console.log(value));
```

---

## 9. Using `.finally()` for Cleanup

```javascript
fetchData()
  .then(data => process(data))
  .catch(err => console.error(err))
  .finally(() => console.log("Operation completed"));
```

* Executes regardless of success or failure

---

## 10. Global Error Handling

### Browser:

```javascript
window.onunhandledrejection = function(event) {
  console.error(event.reason);
};
```

### Node.js:

```javascript
process.on("unhandledRejection", (reason) => {
  console.error(reason);
});
```

---

## 11. Common Mistakes

### 11.1 Missing `.catch()`

Leads to unhandled promise rejections

### 11.2 Silent Errors

```javascript
.catch(() => {})
```

### 11.3 Not Returning Values

Breaks the chain

### 11.4 Mixing `.then()` and `try/catch` Incorrectly

---

## 12. Best Practices

* Always add `.catch()` at the end
* Use meaningful error messages
* Avoid swallowing errors silently
* Re-throw errors when necessary
* Keep error handling centralized
* Use `.finally()` for cleanup

---

## 13. Using Async/Await for Error Handling

```javascript
async function getData() {
  try {
    const result = await fetchData();
    console.log(result);
  } catch (error) {
    console.error(error);
  } finally {
    console.log("Done");
  }
}
```

---

## 14. Advantages of Proper Error Handling

* Prevents crashes
* Improves debugging
* Ensures consistent behavior
* Enhances user experience

---

## 15. Conclusion

Error handling in Promises is essential for building reliable JavaScript applications. By using `.catch()`, understanding error propagation, and following best practices, developers can effectively manage failures in asynchronous workflows. Combining Promises with modern constructs like async/await further enhances clarity and control.

---

## 16. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
