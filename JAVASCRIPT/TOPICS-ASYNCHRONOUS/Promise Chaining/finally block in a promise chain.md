# The `finally` Block in a Promise Chain

## Abstract

The `finally` block in JavaScript Promises provides a way to execute code after a Promise is settled, regardless of whether it is fulfilled or rejected. This paper explains the purpose, syntax, behavior, and practical usage of `.finally()` in promise chains, along with examples, advantages, and best practices.

---

## 1. Introduction

In asynchronous programming, certain operations such as cleaning up resources, stopping loaders, or closing connections must run regardless of success or failure. Traditionally, this required duplicating code in both `.then()` and `.catch()` blocks. The `.finally()` method simplifies this by providing a single place for such logic.

---

## 2. What is `.finally()`?

The `.finally()` method is used to execute a callback after a Promise is settled (either fulfilled or rejected).

In simple words:
It runs **no matter what happens** — success or error.

---

## 3. Syntax

```javascript
promise
  .then(result => {
    // success
  })
  .catch(error => {
    // error
  })
  .finally(() => {
    // always runs
  });
```

---

## 4. Basic Example

```javascript
Promise.resolve("Success")
  .then(data => console.log(data))
  .catch(err => console.error(err))
  .finally(() => console.log("Operation completed"));
```

### Output:

```
Success
Operation completed
```

---

## 5. Example with Error

```javascript
Promise.reject("Failure")
  .then(data => console.log(data))
  .catch(err => console.log(err))
  .finally(() => console.log("Cleanup done"));
```

### Output:

```
Failure
Cleanup done
```

---

## 6. Key Characteristics

### 6.1 Executes Always

* Runs after both success and failure

### 6.2 No Arguments

```javascript
.finally(() => {
  console.log("No access to result or error");
});
```

* Does not receive resolved value or error

### 6.3 Pass-through Behavior

* Does not modify the result unless it throws an error

---

## 7. Internal Working

* `.finally()` returns a new Promise
* It waits for the previous Promise to settle
* After execution, the original value/error is passed forward

---

## 8. Practical Use Cases

### 8.1 Cleaning Resources

```javascript
connectDB()
  .then(() => fetchData())
  .catch(err => console.error(err))
  .finally(() => disconnectDB());
```

### 8.2 Loader/Spinner Handling

```javascript
showLoader();

fetchData()
  .then(data => display(data))
  .catch(err => showError(err))
  .finally(() => hideLoader());
```

---

## 9. Difference Between `.then()` and `.finally()`

| Feature          | `.then()`     | `.finally()`  |
| ---------------- | ------------- | ------------- |
| Runs on success  | Yes           | Yes           |
| Runs on error    | No            | Yes           |
| Gets value/error | Yes           | No            |
| Purpose          | Handle result | Cleanup logic |

---

## 10. Common Mistakes

### 10.1 Expecting Data in `.finally()`

```javascript
.finally((data) => {
  console.log(data); // undefined
});
```

### 10.2 Throwing Errors Unintentionally

```javascript
.finally(() => {
  throw new Error("New error");
});
```

* Overrides previous result

---

## 11. Best Practices

* Use `.finally()` only for cleanup logic
* Avoid modifying results inside `.finally()`
* Do not depend on data inside `.finally()`
* Keep it simple and side-effect focused

---

## 12. `.finally()` vs `try...finally`

| Feature | `.finally()`      | `try...finally`      |
| ------- | ----------------- | -------------------- |
| Context | Promises          | Sync / async-await   |
| Syntax  | Method-based      | Block-based          |
| Usage   | Cleanup in chains | Cleanup in functions |

---

## 13. Conclusion

The `.finally()` method enhances Promise chains by providing a clean and reliable way to execute code after completion, regardless of the outcome. It is especially useful for cleanup operations and improves code readability by avoiding duplication. Understanding `.finally()` is essential for writing robust and maintainable asynchronous JavaScript code.

---

## 14. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
