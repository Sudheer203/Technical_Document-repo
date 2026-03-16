# Differences Between Named Functions and Anonymous Functions in JavaScript

## Introduction

Functions in JavaScript can be written **with a name** or **without a name**.

```

Named Function → function has a name
Anonymous Function → function has no name

```

Both are commonly used, but they are used in **different situations**.

---

# Named Functions

A **named function** has a specific name.

## Syntax

```javascript
function greet(name) {
  console.log("Hello " + name);
}
```

Call the function using its name.

```javascript
greet("Sudheer");
```

Output

```
Hello Sudheer
```

---

## Example

```javascript
function add(a, b) {
  return a + b;
}

const result = add(5, 3);

console.log(result);
```

Output

```
8
```

Named functions are **easy to reuse and debug**.

---

# Anonymous Functions

An **anonymous function** has no name.

It is usually **stored in a variable or passed as an argument**.

## Syntax

```javascript
const greet = function(name) {
  console.log("Hello " + name);
};
```

Call the function using the variable.

```javascript
greet("Sudheer");
```

Output

```
Hello Sudheer
```

---

# Example: Passing Anonymous Function

Anonymous functions are often used as **callbacks**.

```javascript
setTimeout(function() {
  console.log("Task executed");
}, 1000);
```

Output

```
Task executed
```

The function runs after 1 second.

---

# Example With Array Method

Anonymous functions are commonly used in array methods.

```javascript
const numbers = [1, 2, 3];

numbers.forEach(function(n) {
  console.log(n);
});
```

Output

```
1
2
3
```

---

# Arrow Function (Modern Anonymous Function)

Arrow functions are a shorter form of anonymous functions.

```javascript
const greet = (name) => {
  console.log("Hello " + name);
};

greet("Sudheer");
```

Output

```
Hello Sudheer
```

---

# Key Differences

| Feature       | Named Function  | Anonymous Function        |
| ------------- | --------------- | ------------------------- |
| Function name | Has a name      | No name                   |
| Reusability   | Easy to reuse   | Usually used once         |
| Debugging     | Easier to trace | Harder to trace           |
| Common usage  | General logic   | Callbacks and short tasks |

---

# Practical Comparison

Named function

```javascript
function square(n) {
  return n * n;
}

console.log(square(4));
```

Anonymous function

```javascript
const square = function(n) {
  return n * n;
};

console.log(square(4));
```

Both produce the same output.

```
16
```

---

# Summary

Named functions and anonymous functions both define behavior in JavaScript.

```
Named functions → reusable and easier to debug
Anonymous functions → useful for callbacks and short operations
```

Modern JavaScript often uses **anonymous arrow functions** for concise code.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
