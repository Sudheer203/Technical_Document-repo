# How to Chain Promises Using `.then()` in JavaScript

## Abstract

Promise chaining is a powerful technique in JavaScript that allows multiple asynchronous operations to be executed in sequence. This paper explains how to chain Promises using the `.then()` method, how it works internally, its advantages, common mistakes, and best practices.

---

## 1. Introduction

Asynchronous operations are common in JavaScript applications, such as API calls and database queries. Handling multiple async tasks sequentially can become complex with callbacks. Promise chaining using `.then()` provides a clean and structured way to manage such workflows.

---

## 2. What is Promise Chaining?

Promise chaining is the process of linking multiple `.then()` methods so that the output of one operation becomes the input of the next.

In simple words:
Each `.then()` passes its result to the next `.then()`.

---

## 3. Basic Syntax

```javascript
promise
  .then(result1 => {
    return result2;
  })
  .then(result2 => {
    return result3;
  })
  .then(result3 => {
    console.log(result3);
  })
  .catch(error => {
    console.error(error);
  });
```

---

## 4. Simple Example

```javascript
Promise.resolve(2)
  .then(num => num * 2)
  .then(num => num * 3)
  .then(num => console.log(num));
```

### Output:

```
12
```

### Explanation:

* First `.then()` → 2 × 2 = 4
* Second `.then()` → 4 × 3 = 12
* Final `.then()` → prints result

---

## 5. Returning Values vs Returning Promises

### Returning a Value:

```javascript
.then(value => value + 1)
```

* Automatically wrapped in a resolved Promise

### Returning a Promise:

```javascript
.then(value => {
  return new Promise(resolve => {
    setTimeout(() => resolve(value + 1), 1000);
  });
})
```

* Next `.then()` waits for it to resolve

---

## 6. Real-World Example

```javascript
getUser()
  .then(user => getOrders(user.id))
  .then(orders => getOrderDetails(orders[0]))
  .then(details => console.log(details))
  .catch(error => console.error(error));
```

### Flow:

1. Get user
2. Get orders using user ID
3. Get order details
4. Display result

---

## 7. Error Handling in Chains

Errors in any step are passed to `.catch()`.

```javascript
Promise.resolve(10)
  .then(num => {
    throw new Error("Something went wrong");
  })
  .then(num => console.log(num))
  .catch(err => console.error(err.message));
```

---

## 8. Internal Working

* Each `.then()` returns a new Promise
* Results are passed to the next `.then()`
* Errors skip to the nearest `.catch()`
* Execution is handled via the **Microtask Queue**

---

## 9. Advantages of Promise Chaining

* Avoids callback hell
* Improves readability
* Enables sequential execution
* Centralized error handling

---

## 10. Common Mistakes

### 10.1 Not Returning Values

```javascript
.then(num => {
  num * 2; // missing return
})
```

### 10.2 Nested `.then()` Instead of Chaining

```javascript
.then(result => {
  anotherPromise().then(data => console.log(data));
});
```

### 10.3 Missing Error Handling

Not using `.catch()` leads to unhandled errors.

---

## 11. Best Practices

* Always return values or Promises in `.then()`
* Avoid nesting `.then()`
* Use `.catch()` at the end
* Keep chains clean and readable
* Prefer async/await for complex flows

---

## 12. Promise Chaining vs Async/Await

| Feature        | Promise Chaining | Async/Await |
| -------------- | ---------------- | ----------- |
| Syntax         | `.then()`        | `await`     |
| Readability    | Medium           | High        |
| Error Handling | `.catch()`       | try/catch   |

---

## 13. Conclusion

Promise chaining using `.then()` is a fundamental technique for managing sequential asynchronous operations in JavaScript. By returning values or Promises at each step, developers can create clean, readable, and maintainable workflows. While async/await offers a more modern approach, understanding `.then()` chaining is essential for mastering Promises.

---

## 14. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
