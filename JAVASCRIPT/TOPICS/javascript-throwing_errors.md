# Throwing Errors in JavaScript

## Introduction

JavaScript allows developers to **manually create errors** using the `throw` statement.

Throwing errors helps when:

- Input is invalid
- A required value is missing
- A rule in the program is broken

Instead of letting the program fail silently, we **explicitly signal the problem**.

---

# Basic Syntax

```javascript
throw error
```

Usually we throw an **Error object**.

```javascript
throw new Error("Something went wrong");
```

---

# Example 1: Basic Error Throwing

```javascript
function checkAge(age) {
  if (age < 18) {
    throw new Error("Age must be 18 or above");
  }

  console.log("Access granted");
}

checkAge(16);
```

Output

```
Error: Age must be 18 or above
```

---

# Example 2: Using try...catch with throw

Errors should usually be handled using `try...catch`.

```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("Division by zero is not allowed");
  }

  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (error) {
  console.log(error.message);
}
```

Output

```
Division by zero is not allowed
```

---

# Example 3: Validating Function Input

```javascript
function createUser(name) {
  if (!name) {
    throw new Error("Name is required");
  }

  return {
    name: name
  };
}

try {
  createUser("");
} catch (error) {
  console.log(error.message);
}
```

Output

```
Name is required
```

---

# Example 4: Throwing Different Error Types

JavaScript provides built-in error types.

Common ones:

* `Error`
* `TypeError`
* `ReferenceError`
* `RangeError`

Example:

```javascript
function setAge(age) {
  if (typeof age !== "number") {
    throw new TypeError("Age must be a number");
  }

  if (age < 0) {
    throw new RangeError("Age cannot be negative");
  }

  return age;
}

try {
  setAge("twenty");
} catch (error) {
  console.log(error.message);
}
```

Output

```
Age must be a number
```

---

# Example 5: Custom Error Check

```javascript
function withdraw(balance, amount) {
  if (amount > balance) {
    throw new Error("Insufficient balance");
  }

  return balance - amount;
}

try {
  const result = withdraw(500, 1000);
  console.log(result);
} catch (error) {
  console.log(error.message);
}
```

Output

```
Insufficient balance
```

---

# When to Throw Errors

Throw errors when:

* Function arguments are invalid
* Required data is missing
* A rule in the application is violated
* An operation cannot continue safely

Example:

```javascript
if (!userId) {
  throw new Error("User ID is required");
}
```

---

# Summary

The `throw` statement allows developers to **create and signal errors manually**.

Key points:

```
throw → creates an error
try → runs risky code
catch → handles the error
```

Throwing errors improves **validation, debugging, and program safety**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---