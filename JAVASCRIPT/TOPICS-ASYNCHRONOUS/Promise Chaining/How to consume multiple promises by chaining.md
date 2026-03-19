# How to Consume Multiple Promises by Chaining in JavaScript

## Abstract

Handling multiple asynchronous operations in sequence is a common requirement in JavaScript applications. Promise chaining provides a structured approach to consume multiple Promises one after another. This paper explains how to chain multiple Promises, how data flows between them, internal behavior, advantages, and best practices.

---

## 1. Introduction

Modern applications often depend on multiple asynchronous operations such as fetching user data, processing it, and then making additional requests. Managing these operations sequentially using callbacks leads to complexity. Promise chaining solves this by enabling a clean, readable flow of execution using `.then()`.

---

## 2. What Does Consuming Multiple Promises Mean?

Consuming multiple Promises by chaining means:

Executing asynchronous operations **one after another**, where
the output of one Promise becomes the input to the next.

---

## 3. Basic Chaining Concept

```javascript
promise1()
  .then(result1 => {
    return promise2(result1);
  })
  .then(result2 => {
    return promise3(result2);
  })
  .then(result3 => {
    console.log(result3);
  })
  .catch(error => {
    console.error(error);
  });
```

---

## 4. Step-by-Step Example

```javascript
function step1() {
  return Promise.resolve(10);
}

function step2(value) {
  return Promise.resolve(value * 2);
}

function step3(value) {
  return Promise.resolve(value + 5);
}

step1()
  .then(result1 => step2(result1))
  .then(result2 => step3(result2))
  .then(finalResult => console.log(finalResult))
  .catch(err => console.error(err));
```

### Output:

```
25
```

### Flow:

* step1 → 10
* step2 → 20
* step3 → 25

---

## 5. Returning Promises in `.then()`

Each `.then()` must return a Promise for proper chaining.

```javascript
.then(result => {
  return anotherPromise(result);
});
```

If a Promise is returned, the next `.then()` waits for it.

---

## 6. Mixing Values and Promises

```javascript
Promise.resolve(5)
  .then(num => num * 2)          // returns value
  .then(num => Promise.resolve(num + 3)) // returns Promise
  .then(result => console.log(result));
```

* Values are automatically wrapped into Promises
* Chain continues seamlessly

---

## 7. Real-World Example

```javascript
getUser()
  .then(user => getOrders(user.id))
  .then(orders => getOrderDetails(orders[0]))
  .then(details => display(details))
  .catch(err => console.error(err));
```

### Flow:

1. Fetch user
2. Fetch orders using user ID
3. Fetch order details
4. Display result

---

## 8. Error Handling in Chaining

```javascript
step1()
  .then(step2)
  .then(() => {
    throw new Error("Error occurred");
  })
  .then(step3)
  .catch(err => console.error(err.message));
```

* Any error stops execution
* Control moves to `.catch()`

---

## 9. Internal Working

* Each `.then()` returns a new Promise
* Results are passed to the next `.then()`
* Promises are resolved via the **Microtask Queue**
* Execution is sequential

---

## 10. Advantages of Chaining Multiple Promises

* Avoids callback hell
* Maintains sequential flow
* Improves readability
* Simplifies error handling
* Encourages modular code

---

## 11. Common Mistakes

### 11.1 Not Returning Promises

```javascript
.then(result => {
  step2(result); // missing return
});
```

### 11.2 Nested `.then()` Instead of Chaining

```javascript
.then(result => {
  step2(result).then(data => console.log(data));
});
```

### 11.3 Missing `.catch()`

Leads to unhandled errors

---

## 12. Best Practices

* Always return Promises in `.then()`
* Keep chain flat (avoid nesting)
* Use meaningful function names
* Place `.catch()` at the end
* Prefer async/await for complex flows

---

## 13. Chaining vs Parallel Execution

| Feature    | Chaining (Sequential) | Parallel (`Promise.all`) |
| ---------- | --------------------- | ------------------------ |
| Execution  | One after another     | All at once              |
| Dependency | Dependent tasks       | Independent tasks        |
| Speed      | Slower                | Faster                   |

---

## 14. Conclusion

Consuming multiple Promises by chaining is a fundamental technique in JavaScript for handling dependent asynchronous operations. By returning Promises at each step and passing results forward, developers can build clean, readable, and maintainable workflows. Proper understanding of chaining ensures better control over execution flow and error handling.

---

## 15. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
