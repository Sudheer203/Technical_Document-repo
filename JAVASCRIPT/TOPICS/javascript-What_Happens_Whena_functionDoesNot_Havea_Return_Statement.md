# What Happens When a Function Does Not Have a Return Statement

## Introduction

- In JavaScript, a function may or may not return a value.

- If a function **does not contain a `return` statement**, JavaScript automatically returns **`undefined`**.

---

# 1. Function Without Return

When a function has no `return`, the result is `undefined`.

### Example

```javascript
function greet() {
  console.log("Hello");
}

let result = greet();

console.log(result);
````
Output

```
Hello
undefined
```
Explanation:

* The function prints `"Hello"`
* Since there is no `return`, JavaScript returns `undefined`.

---
# 2. Function With Return

If a function uses `return`, the value after `return` becomes the result.

### Example

```javascript
function add(a, b) {
  return a + b;
}

let result = add(2, 3);

console.log(result);
```

Output

```
5
```

---

# 3. Empty Return Statement

A function may contain `return` without a value.

In this case, JavaScript still returns `undefined`.

### Example

```javascript
function test() {
  return;
}

let result = test();

console.log(result);
```

Output

```
undefined
```

---

# 4. Using a Function Without Return in Expressions

If a function without return is used in an expression, the result becomes `undefined`.

### Example

```javascript
function multiply(a, b) {
  let result = a * b;
}

let value = multiply(3, 4);

console.log(value);
```

Output

```
undefined
```

The function calculates the value but **does not return it**.

Correct version:

```javascript
function multiply(a, b) {
  return a * b;
}

let value = multiply(3, 4);

console.log(value);
```

Output

```
12
```

---

# 5. Common Beginner Mistake

Sometimes developers compute a value but forget to return it.

### Example

```javascript
function square(n) {
  n * n;
}

console.log(square(5));
```

Output

```
undefined
```

Correct version:

```javascript
function square(n) {
  return n * n;
}

console.log(square(5));
```

Output

```
25
```

---

# Summary

When a JavaScript function does not have a `return` statement:

* JavaScript automatically returns **`undefined`**
* Any calculated value inside the function is **not returned**
* To send a value outside the function, **`return` must be used**

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return)

---