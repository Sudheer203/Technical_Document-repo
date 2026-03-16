# Difference Between `throw new Error()` and `throw "message"` in JavaScript

## Introduction

JavaScript allows throwing errors in multiple ways.  
Two common approaches are:

```

throw new Error("message")
throw "message"

```

Both stop execution and send an error to `catch`, but they behave differently.

---

# 1. throw new Error("message")

This creates a **proper Error object**.

It includes useful properties like:

- message
- name
- stack trace

### Example

```javascript
function checkAge(age) {
  if (age < 18) {
    throw new Error("Age must be 18 or above");
  }
}

try {
  checkAge(15);
} catch (error) {
  console.log(error.message);
}
```

Output

```
Age must be 18 or above
```

---

### Accessing Error Properties

```javascript
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.log(error.name);
  console.log(error.message);
}
```

Output

```
Error
Something went wrong
```

---

# 2. `throw "message"`

This throws a **simple string**, not an Error object.

### Example

```javascript
function checkAge(age) {
  if (age < 18) {
    throw "Age must be 18 or above";
  }
}

try {
  checkAge(15);
} catch (error) {
  console.log(error);
}
```

Output

```
Age must be 18 or above
```

---

### Limitation

A string does **not contain extra error information**.

```javascript
try {
  throw "Something went wrong";
} catch (error) {
  console.log(error.message);
}
```

Output

```
undefined
```

Because a string has **no `message` property**.

---

# Comparison

| Feature           | `throw new Error()` | `throw "message"` |
| ----------------- | ------------------- | ----------------- |
| Type              | Error object        | String            |
| message property  | Yes                 | No                |
| stack trace       | Yes                 | No                |
| debugging support | Better              | Poor              |

---

# Best Practice

Modern JavaScript prefers using **Error objects**.

```javascript
throw new Error("Invalid input");
```

Example:

```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("Division by zero is not allowed");
  }

  return a / b;
}
```

---

# Summary

Two ways to throw errors exist:

```
throw new Error("message") → recommended
throw "message" → not recommended
```

Using `Error` objects improves **debugging, readability, and error handling**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
