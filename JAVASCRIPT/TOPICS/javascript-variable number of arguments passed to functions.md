# Variable Number of Arguments Passed to Functions in JavaScript

## Introduction

Sometimes a function needs to accept **any number of arguments**.

JavaScript provides two common ways to handle this.

```

arguments object
rest parameters (...)

```

These allow a function to work with **variable input values**.

---

# Using the `arguments` Object

The `arguments` object is available inside regular functions.  
It contains **all arguments passed to the function**.

## Example

```javascript
function printArguments() {
  console.log(arguments);
}

printArguments(1, 2, 3);
```

Output

```
{ '0': 1, '1': 2, '2': 3 }
```

---

## Example: Sum Function

```javascript
function sum() {
  let total = 0;

  for (let i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }

  return total;
}

console.log(sum(1, 2, 3, 4));
```

Output

```
10
```

The function works with **any number of inputs**.

---

# Using Rest Parameters (`...`)

Rest parameters collect multiple arguments into **an array**.

## Syntax

```javascript
function functionName(...values) {
}
```

---

## Example

```javascript
function printNumbers(...numbers) {
  console.log(numbers);
}

printNumbers(10, 20, 30);
```

Output

```
[10, 20, 30]
```

---

## Example: Sum Using Rest Parameters

```javascript
function sum(...numbers) {
  let total = 0;

  for (let i = 0; i < numbers.length; i++) {
    total += numbers[i];
  }

  return total;
}

console.log(sum(5, 10, 15));
```

Output

```
30
```

---

# Combining Parameters with Rest

A function can have normal parameters and a rest parameter.

```javascript
function order(product, ...items) {
  console.log(product);
  console.log(items);
}

order("Laptop", "Mouse", "Keyboard", "Charger");
```

Output

```
Laptop
["Mouse", "Keyboard", "Charger"]
```

---

# Using Array Methods

Rest parameters allow using array methods easily.

```javascript
function multiply(...numbers) {
  return numbers.reduce((total, n) => total * n, 1);
}

console.log(multiply(2, 3, 4));
```

Output

```
24
```

---

# Difference Between `arguments` and Rest Parameters

| Feature                | arguments         | Rest Parameters  |
| ---------------------- | ----------------- | ---------------- |
| Type                   | array-like object | real array       |
| Available in           | regular functions | modern functions |
| Supports array methods | no                | yes              |
| Syntax                 | automatic         | uses `...`       |

---

# Summary

Functions can accept **variable numbers of arguments**.

Common approaches:

```
arguments object
rest parameters (...)
```

Modern JavaScript prefers **rest parameters** because they are cleaner and behave like real arrays.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
