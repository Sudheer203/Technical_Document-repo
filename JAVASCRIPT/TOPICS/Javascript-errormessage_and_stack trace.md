# Reading Error Messages and Tracing Issues from Stack Trace in JavaScript

## Introduction

When JavaScript programs fail, the runtime shows an **error message** and a **stack trace**.

A stack trace tells you:

- **What error happened**
- **Where it happened**
- **Which function calls led to the error**

Learning to read stack traces is one of the **most important debugging skills**.

Practice this **daily for 2 weeks with different errors**.

---

# Structure of an Error Message

Example error:

```text
TypeError: Cannot read properties of undefined (reading 'name')
    at getUserName (app.js:10)
    at showProfile (app.js:15)
    at main (app.js:20)
```

Parts of this error:

```
TypeError → type of error
message → what went wrong
stack trace → function call order
```

The **top line usually shows the real problem**.

---

# Example 1: Undefined Variable

```javascript
function printUser() {
  console.log(userName);
}

printUser();
```

Error:

```text
ReferenceError: userName is not defined
    at printUser (app.js:2)
    at main (app.js:5)
```

Problem:

```
userName variable does not exist
```

Fix:

```javascript
const userName = "Sudheer";

function printUser() {
  console.log(userName);
}

printUser();
```

---

# Example 2: Accessing Property of Undefined

```javascript
function getUserName(user) {
  return user.name;
}

getUserName();
```

Error:

```text
TypeError: Cannot read properties of undefined (reading 'name')
    at getUserName (app.js:2)
```

Problem:

```
user is undefined
```

Fix:

```javascript
function getUserName(user) {
  if (!user) return "No user";

  return user.name;
}
```

---

# Example 3: Error Inside Nested Functions

```javascript
function third() {
  let user = undefined;
  console.log(user.name);
}

function second() {
  third();
}

function first() {
  second();
}

first();
```

Error:

```text
TypeError: Cannot read properties of undefined (reading 'name')
    at third (app.js:3)
    at second (app.js:7)
    at first (app.js:11)
```

Reading the stack:

```
first → second → third
```

The **real issue is inside `third()`**.

---

# Example 4: JSON Parsing Error

```javascript
const data = "{ name: Sudheer }";

JSON.parse(data);
```

Error:

```text
SyntaxError: Unexpected token n in JSON
```

Problem:

```
Invalid JSON format
```

Fix:

```javascript
const data = '{"name":"Sudheer"}';

JSON.parse(data);
```

---

# Example 5: Division Error

```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("Division by zero");
  }

  return a / b;
}

function calculate() {
  divide(10, 0);
}

calculate();
```

Error:

```text
Error: Division by zero
    at divide (app.js:3)
    at calculate (app.js:9)
```

Stack trace shows the **exact call order**.

---

# Debugging Steps

When an error occurs:

```
1. Read the error type
2. Read the message
3. Find the file and line number
4. Check the function in the stack trace
5. Identify the wrong value
```

Example approach:

```
Error → TypeError
Location → app.js line 10
Function → getUserName
Cause → undefined variable
```
---

# Summary

Stack traces show the **path of function calls that caused an error**.

Important skills:

```
Read the error message
Find the line number
Follow the stack trace
Fix the root problem
```

Practicing this daily for **two weeks** will significantly improve debugging ability.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---