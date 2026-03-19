# What Happens When an Error is Thrown Inside `.then()` When There is a `.catch()`

## Abstract

Error handling is a fundamental aspect of Promise-based asynchronous programming in JavaScript. When an error is thrown inside a `.then()` block, it affects the execution flow of the Promise chain. This paper explains how such errors propagate, how `.catch()` handles them, and the internal mechanics behind this behavior.

---

## 1. Introduction

Promises provide a structured way to manage asynchronous operations. One of their key features is automatic error propagation. When an error occurs inside a `.then()` block, it does not crash the program immediately but is instead passed down the chain until a `.catch()` handler is encountered.

---

## 2. Throwing an Error Inside `.then()`

Errors inside `.then()` can be created using the `throw` statement.

### Example:

```javascript
Promise.resolve(10)
  .then(num => {
    throw new Error("Something went wrong");
  })
  .catch(err => {
    console.log(err.message);
  });
```

### Output:

```
Something went wrong
```

---

## 3. What Actually Happens Internally

When an error is thrown inside `.then()`:

1. The current Promise is immediately **rejected**
2. The error becomes the rejection reason
3. All subsequent `.then()` blocks are **skipped**
4. Control moves to the nearest `.catch()`

---

## 4. Error Propagation in Promise Chain

```javascript
Promise.resolve(5)
  .then(num => {
    return num * 2;
  })
  .then(num => {
    throw new Error("Error occurred here");
  })
  .then(num => {
    console.log(num); // skipped
  })
  .catch(err => {
    console.log("Caught:", err.message);
  });
```

### Explanation:

* First `.then()` executes normally
* Second `.then()` throws an error
* Third `.then()` is skipped
* `.catch()` handles the error

---

## 5. Equivalent to Promise Rejection

Throwing an error inside `.then()` is equivalent to returning a rejected Promise.

```javascript
.then(() => {
  return Promise.reject("Error");
});
```

Both approaches produce the same result.

---

## 6. Multiple `.then()` and Single `.catch()`

A single `.catch()` can handle errors from any previous `.then()`.

```javascript
doTask1()
  .then(doTask2)
  .then(doTask3)
  .catch(err => console.error(err));
```

* Error in any step → handled by `.catch()`

---

## 7. What If There is No `.catch()`?

If no `.catch()` is present:

* The error becomes an **unhandled promise rejection**
* May produce warnings or crash (depending on environment)

---

## 8. Recovery After `.catch()`

`.catch()` can recover and allow the chain to continue.

```javascript
Promise.resolve(10)
  .then(() => {
    throw new Error("Error");
  })
  .catch(err => {
    console.log("Handled:", err.message);
    return 20;
  })
  .then(num => {
    console.log("Recovered value:", num);
  });
```

---

## 9. Chaining Behavior

* `.then()` returns a new Promise
* `.catch()` also returns a new Promise
* Flow continues after error handling

---

## 10. Common Mistakes

### 10.1 Assuming `.then()` Runs After Error

It does not execute after an error unless handled.

### 10.2 Forgetting `.catch()`

Leads to unhandled errors.

### 10.3 Not Returning After Handling

May break expected flow.

---

## 11. Best Practices

* Always include a `.catch()` at the end
* Use meaningful error messages
* Handle or rethrow errors properly
* Avoid silent failures
* Keep chains clean and readable

---

## 12. Visual Flow

```
.then() → .then() → (Error Thrown) → skip .then() → .catch()
```

---

## 13. Conclusion

When an error is thrown inside a `.then()` block, the Promise is immediately rejected, and control is transferred to the nearest `.catch()` handler. This automatic error propagation simplifies asynchronous error handling and ensures that failures can be managed in a centralized and predictable manner. Understanding this behavior is essential for writing reliable and maintainable Promise-based code.

---

## 14. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
