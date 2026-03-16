# Debugging Strategies in JavaScript

## Introduction

Debugging is the process of **finding and fixing errors in code**.

Good debugging strategies help developers:

```

find bugs faster
understand program behavior
fix issues correctly

```

---

# 1. Read the Error Message Carefully

Error messages usually tell:

```

what went wrong
which file
which line number

```

Example

```javascript
const user = { name: "Sudheer" };

console.log(user.age.toUpperCase());
```

Error

```
TypeError: Cannot read properties of undefined
```

Explanation

```
user.age is undefined
toUpperCase() cannot run on undefined
```

---

# 2. Use `console.log()` to Inspect Values

Printing values helps understand program flow.

Example

```javascript
function divide(a, b) {
  console.log("a:", a);
  console.log("b:", b);

  return a / b;
}

divide(10, 0);
```

Output

```
a: 10
b: 0
```

This helps identify **unexpected values**.

---

# 3. Check Inputs to Functions

Sometimes bugs happen because **wrong inputs are passed**.

Example

```javascript
function greet(name) {
  console.log("Hello " + name.toUpperCase());
}

greet();
```

Error

```
TypeError: Cannot read properties of undefined
```

Fix

```javascript
function greet(name) {
  if (name === undefined) {
    console.log("Name required");
    return;
  }

  console.log("Hello " + name.toUpperCase());
}
```

---

# 4. Break the Problem into Small Parts

Large code blocks are harder to debug.

Bad example

```javascript
const result = numbers.filter(n => n > 10).map(n => n * 2).reduce((a,b) => a + b);
```

Better approach

```javascript
const filtered = numbers.filter(n => n > 10);
console.log(filtered);

const doubled = filtered.map(n => n * 2);
console.log(doubled);

const result = doubled.reduce((a, b) => a + b);
```

Each step can be inspected.

---

# 5. Use `console.table()` for Arrays and Objects

Helps visualize structured data.

```javascript
const users = [
  { name: "A", age: 20 },
  { name: "B", age: 25 }
];

console.table(users);
```

Output

```
(index)  name  age
0        A     20
1        B     25
```

---

# 6. Check Loop Conditions

Incorrect loop conditions often cause bugs.

Example

```javascript
const numbers = [1,2,3];

for (let i = 0; i <= numbers.length; i++) {
  console.log(numbers[i]);
}
```

Problem

```
numbers[3] is undefined
```

Fix

```javascript
for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
}
```

---

# 7. Use Try-Catch for Error Handling

This prevents the program from crashing.

```javascript
try {
  const data = JSON.parse("invalid json");
} catch (error) {
  console.error(error.message);
}
```

---

# 8. Test Small Pieces of Code

Instead of running a full application, test **small functions**.

Example

```javascript
function square(n) {
  return n * n;
}

console.log(square(5));
```

Testing small units helps isolate problems.

---

# 9. Reproduce the Error

Always try to **repeat the bug**.

Example steps

```
run the program
observe when error appears
repeat the same input
```

This helps identify the cause.

---

# 10. Practice Reading Stack Traces

Stack traces show **where the error occurred**.

Example

```
TypeError: Cannot read properties of undefined
    at greet (app.js:10)
    at main (app.js:20)
```

Meaning

```
Error occurred in greet function
at line 10 in app.js
```

---

# Summary

Good debugging requires a systematic approach.

Key strategies

```
read error messages carefully
use console logs
check function inputs
break code into smaller steps
inspect loops
use try-catch
read stack traces
```

Consistent debugging practice improves **problem-solving skills and code quality**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
