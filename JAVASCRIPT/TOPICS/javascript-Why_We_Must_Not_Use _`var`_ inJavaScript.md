# Why We Must Not Use `var` in JavaScript

## Introduction

- `var` was the original keyword used to declare variables in JavaScript.

- Modern JavaScript provides **`let` and `const`**, which fix many problems caused by `var`.

- Because of these issues, developers usually **avoid using `var`** in modern code.

---

# 1. No Block Scope

`var` does **not follow block scope**.  
It only follows **function scope**.

### Example

```javascript
if (true) {
  var count = 10;
}

console.log(count);
````

Output

```
10
```

Even though `count` is inside the `if` block, it is still accessible outside.

### Using `let` (Correct Behavior)

```javascript
if (true) {
  let count = 10;
}

console.log(count);
```

Output

```
ReferenceError
```

`let` correctly limits the variable to the block.

---

# 2. Redeclaration is Allowed

`var` allows **redeclaring the same variable**, which can create bugs.

### Example

```javascript
var city = "Delhi";
var city = "Mumbai";

console.log(city);
```

Output

```
Mumbai
```

The previous value is overwritten without warning.

### Using `let`

```javascript
let city = "Delhi";
let city = "Mumbai";
```

Output

```
SyntaxError
```

`let` prevents accidental redeclaration.

---

# 3. Hoisting Can Cause Confusion

Variables declared with `var` are **hoisted and initialized with `undefined`**.

### Example

```javascript
console.log(score);

var score = 50;
```

Output

```
undefined
```

JavaScript internally treats the code like this:

```javascript
var score;

console.log(score);

score = 50;
```

This behavior can confuse developers.

---

# 4. Loop Variable Problems

Using `var` inside loops can cause unexpected behavior.

### Example

```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 100);
}
```

Output

```
3
3
3
```

Because `var` shares the same variable for all iterations.

### Using `let`

```javascript
for (let i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 100);
}
```

Output

```
0
1
2
```

`let` creates a new variable for each iteration.

---

# 5. Global Scope Pollution

When `var` is used globally, it attaches the variable to the global object.

### Example

```javascript
var name = "Sudheer";

console.log(window.name);
```

This can accidentally overwrite other global variables.

Using `let` or `const` avoids this problem.

---

# Recommended Practice

Modern JavaScript usually follows this rule:

```
Use const by default
Use let if the value must change
Avoid var
```

Example

```javascript
const pi = 3.14;

let counter = 0;
counter++;
```

---

# Summary

`var` creates several problems in JavaScript:

* No block scope
* Allows redeclaration
* Confusing hoisting behavior
* Loop bugs
* Global scope pollution

Because of these issues, modern JavaScript uses **`let` and `const` instead of `var`**.

---

# Reference

MDN Web Docs

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)

---
