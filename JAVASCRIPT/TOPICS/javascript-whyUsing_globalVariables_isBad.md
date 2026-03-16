# Why Using Global Variables Is Bad in JavaScript

## Introduction

A **global variable** is a variable declared **outside any function or block**.  
It can be accessed from **anywhere in the program**.

Example:

```javascript
let username = "Sudheer";

function showUser() {
  console.log(username);
}

showUser();
````

Global variables seem convenient, but they can create **serious problems in large applications**.

---

# 1. Accidental Modification

Any part of the program can change a global variable.

### Example

```javascript
let count = 10;

function increase() {
  count = count + 1;
}

function reset() {
  count = 0;
}

increase();
reset();

console.log(count);
```

Output

```
0
```

The value changed unexpectedly because multiple functions modified the same variable.

---

# 2. Name Conflicts

Different files or functions may create variables with the same name.

### Example

```javascript
let data = "User data";

// another file
let data = "Product data";
```

Output

```
SyntaxError: Identifier 'data' has already been declared
```

Global variables increase the chance of **variable name collisions**.

---

# 3. Hard to Debug

When a global variable changes, it is difficult to know **which part of the code changed it**.

### Example

```javascript
let score = 50;

function addPoints() {
  score += 10;
}

function removePoints() {
  score -= 5;
}

addPoints();
removePoints();

console.log(score);
```

If the value becomes incorrect, tracking the source of the change becomes difficult.

---

# 4. Poor Code Maintainability

Global variables make code **tightly coupled**.

Functions depend on external variables instead of receiving data as parameters.

### Example (Bad)

```javascript
let price = 100;

function calculateTax() {
  return price * 0.18;
}

console.log(calculateTax());
```

The function depends on a global variable.

### Better Approach

```javascript
function calculateTax(price) {
  return price * 0.18;
}

console.log(calculateTax(100));
```

Now the function is **independent and reusable**.

---

# 5. Global Scope Pollution

Too many global variables make the global environment crowded.

### Example

```javascript
let user;
let age;
let product;
let total;
let price;
let discount;
```

Large projects may have **hundreds of global variables**, which makes the code difficult to manage.

---

# Better Practices

Instead of global variables:

* Use **function parameters**
* Use **local variables**
* Use **modules**

Example:

```javascript
function calculateTotal(price, tax) {
  return price + tax;
}

console.log(calculateTotal(100, 18));
```

---

# Summary

Global variables are considered bad practice because they:

* Can be modified from anywhere
* Create name conflicts
* Make debugging difficult
* Reduce code maintainability
* Pollute the global scope

Modern JavaScript development prefers **local variables, functions, and modules instead of global variables**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types)

---