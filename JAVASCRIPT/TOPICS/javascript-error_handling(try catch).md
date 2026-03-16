# Error Handling in JavaScript (try...catch)

## Introduction

Errors can occur while running JavaScript code.  
To prevent the program from crashing, JavaScript provides **error handling** using `try...catch`.

This allows developers to **handle errors safely** and continue execution.

---

# Basic Syntax

```javascript
try {
  // code that may throw an error
} catch (error) {
  // code that handles the error
}
```

---

# Example 1: Handling an Undefined Variable

```javascript
try {
  console.log(userName);
} catch (error) {
  console.log("An error occurred");
}
```

Output

```
An error occurred
```

The program does **not stop** because the error is caught.

---

# Example 2: Logging the Error Message

```javascript
try {
  console.log(userName);
} catch (error) {
  console.log(error.message);
}
```

Possible Output

```
userName is not defined
```

`error.message` gives the **actual error description**.

---

# Example 3: try...catch with finally

`finally` runs **whether an error occurs or not**.

```javascript
try {
  console.log("Start program");
  let result = 10 / 2;
  console.log(result);
} catch (error) {
  console.log("Error occurred");
} finally {
  console.log("Execution finished");
}
```

Output

```
Start program
5
Execution finished
```

---

# Example 4: Throwing Custom Errors

You can create your own errors using `throw`.

```javascript
function withdraw(balance, amount) {
  try {
    if (amount > balance) {
      throw new Error("Insufficient balance");
    }

    return balance - amount;

  } catch (error) {
    console.log(error.message);
  }
}

withdraw(1000, 2000);
```

Output

```
Insufficient balance
```

---

# Example 5: Safe JSON Parsing

`try...catch` is commonly used when parsing JSON.

```javascript
const data = '{"name":"Sudheer"}';

try {
  const user = JSON.parse(data);
  console.log(user.name);
} catch (error) {
  console.log("Invalid JSON format");
}
```

Output

```
Sudheer
```

---

# When to Use try...catch

Use `try...catch` when:

* Working with **external data**
* Parsing **JSON**
* Running **risky operations**
* Handling **unexpected runtime errors**

Example:

```javascript
try {
  const result = riskyFunction();
  console.log(result);
} catch (error) {
  console.log("Something went wrong");
}
```

---

# Important Notes

* `try...catch` works only for **runtime errors**.
* It does **not catch syntax errors before execution**.
* Avoid wrapping **large blocks of code** inside `try`.

---

# Summary

`try...catch` helps handle runtime errors without crashing the program.

Structure:

```
try → run risky code  
catch → handle error  
finally → optional cleanup
```

Proper error handling makes programs **more stable and easier to debug**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
