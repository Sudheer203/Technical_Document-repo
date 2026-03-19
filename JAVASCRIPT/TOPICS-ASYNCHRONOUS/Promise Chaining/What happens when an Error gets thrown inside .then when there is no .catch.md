# What Happens When an Error is Thrown Inside `.then()` When There is No `.catch()`

## Abstract

In JavaScript Promise chains, errors thrown inside `.then()` blocks are automatically converted into rejected Promises. When no `.catch()` handler is present, these errors result in **unhandled promise rejections**, which can lead to warnings, unexpected behavior, or application crashes. This paper explains how such errors propagate, what happens internally, and the consequences of not handling them.

---

## 1. Introduction

Promises simplify asynchronous programming by providing structured error handling. However, when developers fail to include a `.catch()` block, errors thrown inside `.then()` can become problematic. Understanding this behavior is essential for writing robust and reliable applications.

---

## 2. Throwing an Error Inside `.then()`

```javascript
Promise.resolve(10)
  .then(num => {
    throw new Error("Something went wrong");
  });
```

### Observation:

* No `.catch()` is provided
* Error is not handled explicitly

---

## 3. What Happens Internally

When an error is thrown inside `.then()`:

1. The current Promise becomes **rejected**
2. The error becomes the rejection reason
3. The Promise chain looks for a `.catch()`
4. Since no `.catch()` exists → error remains **unhandled**

---

## 4. Unhandled Promise Rejection

An unhandled error in a Promise results in:

**Unhandled Promise Rejection**

### Behavior:

* Browser: Logs warning in console
* Node.js: May log warning or terminate process (in strict modes)

### Example Output:

```
Uncaught (in promise) Error: Something went wrong
```

---

## 5. Example with Multiple `.then()`

```javascript
Promise.resolve(5)
  .then(num => num * 2)
  .then(num => {
    throw new Error("Error occurred");
  })
  .then(num => {
    console.log(num); // skipped
  });
```

### Explanation:

* Error is thrown
* Next `.then()` is skipped
* No `.catch()` → error is unhandled

---

## 6. Event Loop and Error Handling

* Promise errors are handled in the **Microtask Queue**
* If no `.catch()` is found after execution
* JavaScript runtime reports the error asynchronously

---

## 7. Node.js vs Browser Behavior

### In Browsers:

* Displays warning in console
* Application continues running

### In Node.js:

* Emits `UnhandledPromiseRejectionWarning`
* Future versions may terminate the process

---

## 8. Why This is Dangerous

* Hard to debug
* Silent failures in production
* May crash applications
* Breaks program flow

---

## 9. Late Error Handling

Sometimes `.catch()` is added later:

```javascript
const p = Promise.resolve(10)
  .then(() => {
    throw new Error("Error");
  });

setTimeout(() => {
  p.catch(err => console.log(err.message));
}, 1000);
```

### Behavior:

* Runtime may already report unhandled rejection
* Later handling may not prevent warning

---

## 10. Best Practices

* Always attach `.catch()` to Promise chains
* Use global handlers if needed:

  * `window.onunhandledrejection`
  * `process.on('unhandledRejection')`
* Avoid leaving Promises unhandled
* Use async/await with try/catch

---

## 11. Prevention Using `.catch()`

```javascript
Promise.resolve(10)
  .then(() => {
    throw new Error("Error handled");
  })
  .catch(err => console.log(err.message));
```

---

## 12. Visual Flow

```
.then() → .then() → (Error Thrown) → No .catch() → Unhandled Rejection
```

---

## 13. Conclusion

When an error is thrown inside a `.then()` block without a corresponding `.catch()`, the Promise becomes rejected and results in an unhandled promise rejection. This can lead to warnings, unstable behavior, or application crashes depending on the environment. Proper error handling using `.catch()` or async/await is essential to ensure reliable and maintainable JavaScript applications.

---

## 14. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
