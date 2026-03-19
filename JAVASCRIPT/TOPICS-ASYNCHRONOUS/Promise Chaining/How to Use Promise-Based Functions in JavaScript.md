# How to Use Promise-Based Functions in JavaScript

## Abstract

JavaScript provides several built-in Promise utility methods that simplify asynchronous programming. These include `Promise.resolve`, `Promise.reject`, `Promise.all`, `Promise.allSettled`, `Promise.any`, and `Promise.race`. This paper explains how each of these functions works, their use cases, behavior, and best practices.

---

## 1. Introduction

Promises are essential for handling asynchronous operations in JavaScript. In addition to creating and consuming Promises, JavaScript provides static helper methods that allow developers to manage multiple Promises efficiently. Understanding these methods is crucial for writing clean and performant code.

---

## 2. `Promise.resolve()`

### Definition

Returns a Promise that is already resolved with a given value.

### Syntax

```javascript
Promise.resolve(value);
```

### Example

```javascript
Promise.resolve(10)
  .then(result => console.log(result));
```

### Use Cases

* Wrapping non-Promise values
* Returning immediate success
* Normalizing return types

---

## 3. `Promise.reject()`

### Definition

Returns a Promise that is already rejected with a given reason.

### Syntax

```javascript
Promise.reject(error);
```

### Example

```javascript
Promise.reject("Error occurred")
  .catch(err => console.log(err));
```

### Use Cases

* Returning immediate failure
* Testing error handling
* Propagating errors

---

## 4. `Promise.all()`

### Definition

Executes multiple Promises in parallel and resolves when all are fulfilled.

### Syntax

```javascript
Promise.all([p1, p2, p3]);
```

### Example

```javascript
Promise.all([
  Promise.resolve(1),
  Promise.resolve(2),
  Promise.resolve(3)
])
.then(results => console.log(results))
.catch(err => console.error(err));
```

### Behavior

* Returns array of results
* Fails immediately if any Promise rejects

---

## 5. `Promise.allSettled()`

### Definition

Executes multiple Promises and returns results after all have settled (fulfilled or rejected).

### Syntax

```javascript
Promise.allSettled([p1, p2, p3]);
```

### Example

```javascript
Promise.allSettled([
  Promise.resolve(1),
  Promise.reject("Error"),
  Promise.resolve(3)
])
.then(results => console.log(results));
```

### Output Format

```javascript
[
  { status: "fulfilled", value: 1 },
  { status: "rejected", reason: "Error" },
  { status: "fulfilled", value: 3 }
]
```

### Use Cases

* When all results are needed
* Handling partial success

---

## 6. `Promise.any()`

### Definition

Resolves as soon as any one Promise is fulfilled.

### Syntax

```javascript
Promise.any([p1, p2, p3]);
```

### Example

```javascript
Promise.any([
  Promise.reject("Error1"),
  Promise.resolve("Success"),
  Promise.reject("Error2")
])
.then(result => console.log(result))
.catch(err => console.error(err));
```

### Behavior

* Returns first fulfilled result
* Rejects only if all Promises fail

---

## 7. `Promise.race()`

### Definition

Returns the result of the first Promise that settles (fulfilled or rejected).

### Syntax

```javascript
Promise.race([p1, p2, p3]);
```

### Example

```javascript
Promise.race([
  new Promise(resolve => setTimeout(() => resolve("First"), 100)),
  new Promise(resolve => setTimeout(() => resolve("Second"), 200))
])
.then(result => console.log(result));
```

### Behavior

* First settled Promise wins
* Can return success or failure

---

## 8. Comparison of Methods

| Method             | Waits For All | Returns on First | Handles Errors                  |
| ------------------ | ------------- | ---------------- | ------------------------------- |
| Promise.resolve    | No            | Immediate        | No                              |
| Promise.reject     | No            | Immediate        | Yes                             |
| Promise.all        | Yes           | No               | Fails fast                      |
| Promise.allSettled | Yes           | No               | Collects all                    |
| Promise.any        | No            | First success    | Ignores failures until all fail |
| Promise.race       | No            | First settle     | Returns first result            |

---

## 9. Best Practices

* Use `Promise.all()` for independent parallel tasks
* Use `Promise.allSettled()` when all results matter
* Use `Promise.any()` for fallback strategies
* Use `Promise.race()` for timeout logic
* Always include error handling with `.catch()`

---

## 10. Real-World Example

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

---

## 11. Conclusion

Promise utility methods provide powerful tools to manage asynchronous operations efficiently. Each method serves a specific purpose, from handling immediate values to managing multiple concurrent tasks. Understanding when and how to use these functions enables developers to write scalable, efficient, and maintainable JavaScript applications.

---

## 12. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
