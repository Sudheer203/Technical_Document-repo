# How JavaScript Executes Code

## Abstract

JavaScript is a single-threaded, synchronous programming language with powerful asynchronous capabilities. Understanding how JavaScript executes code is essential for writing efficient, bug-free applications. This paper explains the internal working of the JavaScript engine, including execution context, call stack, memory management, and the event loop.

---

## 1. Introduction

JavaScript is widely used for building web applications. Although it appears simple, its execution model is complex. Behind the scenes, JavaScript uses an execution engine that manages memory, processes code, and handles asynchronous operations.

---

## 2. JavaScript Engine

A JavaScript engine is a program that executes JavaScript code. Examples include V8 (used in Chrome and Node.js) and SpiderMonkey (used in Firefox).

### Components of JavaScript Engine:

1. **Memory Heap** – Stores variables and objects.
2. **Call Stack** – Keeps track of function execution.

---

## 3. Execution Context

Execution context is the environment in which JavaScript code is evaluated and executed.

### Types of Execution Context:

1. **Global Execution Context (GEC)**

   * Created when the program starts.
   * Contains global variables and functions.

2. **Function Execution Context (FEC)**

   * Created whenever a function is invoked.

3. **Eval Execution Context**

   * Created when `eval()` is used (rarely used).

---

## 4. Phases of Execution Context

Each execution context goes through two phases:

### 4.1 Memory Creation Phase (Creation Phase)

* Variables are allocated memory.
* Variables declared with `var` are initialized as `undefined`.
* Functions are stored in memory completely.

### 4.2 Code Execution Phase

* Code is executed line by line.
* Variables get their actual values.
* Functions are invoked.

---

## 5. Call Stack

The call stack is a data structure that keeps track of function calls.

### Working:

* When a function is called → pushed onto the stack.
* When a function finishes → popped from the stack.

### Example:

```javascript
function a() {
  console.log("A");
}
function b() {
  a();
  console.log("B");
}
b();
```

### Execution Flow:

1. Global Execution Context pushed.
2. `b()` pushed.
3. `a()` pushed.
4. `a()` executed and popped.
5. `b()` continues and popped.

---

## 6. Hoisting

Hoisting is JavaScript's default behavior of moving declarations to the top.

### Example:

```javascript
console.log(x); // undefined
var x = 10;
```

* `var` is hoisted as `undefined`.
* Functions are fully hoisted.

---

## 7. Scope and Scope Chain

### Scope:

Determines where variables are accessible.

### Types:

* Global Scope
* Local Scope
* Block Scope (`let`, `const`)

### Scope Chain:

JavaScript searches variables in the current scope, then outer scopes.

---

## 8. Closures

A closure is a function that remembers its outer scope even after the outer function has finished execution.

### Example:

```javascript
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}
const fn = outer();
fn();
fn();
```

---

## 9. Asynchronous JavaScript

JavaScript can handle asynchronous operations using:

* Callbacks
* Promises
* Async/Await

---

## 10. Event Loop

JavaScript uses an event loop to handle asynchronous code.

### Components:

1. Call Stack
2. Web APIs (Browser APIs)
3. Callback Queue
4. Event Loop

### Working:

1. Async task goes to Web API.
2. After completion → moved to Callback Queue.
3. Event Loop checks if Call Stack is empty.
4. Moves task from queue to stack.

### Example:

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```

### Output:

```
Start
End
Timeout
```

---

## 11. Microtasks vs Macrotasks

### Microtasks:

* Promises
* MutationObserver

### Macrotasks:

* setTimeout
* setInterval

### Priority:

Microtasks execute before macrotasks.

---

## 12. Conclusion

JavaScript execution is based on execution contexts, call stack, and the event loop. Even though it is single-threaded, it efficiently handles asynchronous operations using the event loop and callback queues. A clear understanding of these concepts helps developers write optimized and predictable code.

---

## 13. References

* MDN Web Docs
* JavaScript.info
* ECMAScript Specification

---
