# States of a Promise in JavaScript: Pending, Fulfilled, and Rejected

## Abstract

Promises are a core feature of JavaScript used to manage asynchronous operations. Each Promise goes through specific states during its lifecycle. This paper explains the three states of a Promise—Pending, Fulfilled, and Rejected—their behavior, transitions, and practical significance in asynchronous programming.

---

## 1. Introduction

In JavaScript, asynchronous operations such as API calls and timers do not complete immediately. Promises provide a structured way to track the status of these operations. Understanding the states of a Promise is essential for handling results and errors effectively.

---

## 2. Lifecycle of a Promise

A Promise has a lifecycle with three main states:

1. Pending
2. Fulfilled
3. Rejected

A Promise starts in the **pending** state and eventually moves to either **fulfilled** or **rejected**.

---

## 3. Pending State

### Definition

The **pending** state is the initial state of a Promise.

### Characteristics:

* The operation is still in progress
* No result is available yet
* Neither resolved nor rejected

### Example:

```javascript
const promise = new Promise((resolve, reject) => {
  // still running
});
```

At this point, the Promise is pending because no result has been returned.

---

## 4. Fulfilled State

### Definition

A Promise is **fulfilled** when the asynchronous operation completes successfully.

### Characteristics:

* The operation is successful
* A value is returned using `resolve()`
* `.then()` method handles the result

### Example:

```javascript
const promise = new Promise((resolve, reject) => {
  resolve("Success");
});

promise.then((result) => {
  console.log(result);
});
```

### Output:

```
Success
```

---

## 5. Rejected State

### Definition

A Promise is **rejected** when the asynchronous operation fails.

### Characteristics:

* An error occurs
* `reject()` is called
* `.catch()` handles the error

### Example:

```javascript
const promise = new Promise((resolve, reject) => {
  reject("Error occurred");
});

promise.catch((error) => {
  console.log(error);
});
```

### Output:

```
Error occurred
```

---

## 6. State Transition

A Promise follows strict state transitions:

```
Pending → Fulfilled
Pending → Rejected
```

### Important Rules:

* A Promise can change state only once
* Once fulfilled or rejected, it becomes **settled**
* State cannot be changed again

---

## 7. Visual Representation

```
         Pending
        /       \
 Fulfilled     Rejected
```

---

## 8. Real-World Example

```javascript
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    const success = true;

    if (success) {
      resolve("Data fetched");
    } else {
      reject("Failed to fetch");
    }
  }, 1000);
});
```

* Initially → Pending
* After 1 second:

  * If success → Fulfilled
  * Else → Rejected

---

## 9. Importance of Promise States

* Helps track asynchronous operation status
* Enables proper success and error handling
* Improves code reliability
* Supports chaining and async flow

---

## 10. Common Mistakes

### 10.1 Ignoring Rejected State

Not handling errors can crash applications.

### 10.2 Multiple Resolve/Reject Calls

Only the first call is considered.

### 10.3 Misunderstanding Pending

Pending does not mean failure—it means "still processing".

---

## 11. Best Practices

* Always handle both success and failure
* Use `.then()` for fulfilled state
* Use `.catch()` for rejected state
* Prefer async/await for cleaner handling

---

## 12. Conclusion

The three states of a Promise—pending, fulfilled, and rejected—form the foundation of asynchronous programming in JavaScript. A clear understanding of these states helps developers manage operations effectively, handle errors properly, and write clean, maintainable code. Mastering Promise states is essential for working with modern JavaScript features like async/await.

---

## 13. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
