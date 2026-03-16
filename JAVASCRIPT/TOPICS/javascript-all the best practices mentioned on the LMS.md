# JavaScript Best Practices

## Introduction

Best practices help developers write **clean, readable, and maintainable code**.  
Following these practices reduces bugs and improves collaboration.

---

# 1. Proper Indentation

Indentation makes code easier to read.

Bad example

```javascript
function greet(name){
console.log("Hello " + name);
if(name){
console.log("User exists");
}
}
```

Good example

```javascript
function greet(name) {
  console.log("Hello " + name);

  if (name) {
    console.log("User exists");
  }
}
```

Best practice

```
Use consistent indentation (usually 2 spaces)
Keep code blocks clearly aligned
```

---

# 2. Meaningful Variable Names

Variable names should clearly describe the data.

Bad example

```javascript
let x = 25;
let y = "Sudheer";
```

Good example

```javascript
let age = 25;
let userName = "Sudheer";
```

Best practice

```
Use descriptive names
Avoid single-letter variables
```

---

# 3. Loop Variable Naming

Use clear loop variable names when possible.

Basic loop

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

Better example with data

```javascript
const users = ["A", "B", "C"];

for (let index = 0; index < users.length; index++) {
  console.log(users[index]);
}
```

Using descriptive variable names improves readability.

---

# 4. Use `const` by Default

Prefer `const` unless the value changes.

```javascript
const name = "Sudheer";
```

Use `let` only when reassignment is needed.

```javascript
let score = 10;
score = 20;
```

Avoid using `var`.

---

# 5. Keep Functions Small

Functions should do **one task only**.

Bad example

```javascript
function processUser(user) {
  console.log(user);
  saveUser(user);
  sendEmail(user);
}
```

Better approach

```javascript
function printUser(user) {
  console.log(user);
}

function saveUser(user) {
  // save logic
}

function sendEmail(user) {
  // email logic
}
```

---

# 6. Use Clear Function Names

Function names should describe their action.

Bad example

```javascript
function doThing(data) {
  return data.length;
}
```

Good example

```javascript
function getUserCount(users) {
  return users.length;
}
```

---

# 7. Avoid Global Variables

Global variables can cause unexpected bugs.

Bad example

```javascript
let total = 0;

function add(value) {
  total += value;
}
```

Better example

```javascript
function add(a, b) {
  return a + b;
}
```

---

# 8. Use Strict Equality (`===`)

Avoid loose equality (`==`).

Bad example

```javascript
console.log(5 == "5");
```

Good example

```javascript
console.log(5 === "5");
```

Strict equality prevents unexpected type conversions.

---

# 9. Use Array Methods Instead of Loops When Possible

Array methods improve readability.

Example using `map`

```javascript
const numbers = [1, 2, 3];

const doubled = numbers.map(n => n * 2);

console.log(doubled);
```

---

# 10. Write Readable Conditions

Avoid complex conditions.

Bad example

```javascript
if (!user || user === null || user === undefined) {
  console.log("Invalid user");
}
```

Better example

```javascript
if (user === undefined || user === null) {
  console.log("Invalid user");
}
```

---

# 11. Consistent Code Formatting

Keep formatting consistent.

Example

```javascript
const user = {
  name: "Sudheer",
  age: 25
};
```

Avoid inconsistent formatting.

---

# 12. Comment When Necessary

Comments should explain **why**, not obvious code.

Example

```javascript
// calculate total price including tax
const total = price + price * tax;
```

Avoid unnecessary comments.

Bad example

```javascript
// add two numbers
let sum = a + b;
```

---

# Summary

Good coding practices improve **readability, maintainability, and collaboration**.

Key practices

```
use proper indentation
use meaningful variable names
avoid global variables
prefer const over let
avoid var
use strict equality
write small functions
keep formatting consistent
```

Following these practices leads to **clean and professional JavaScript code**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---

