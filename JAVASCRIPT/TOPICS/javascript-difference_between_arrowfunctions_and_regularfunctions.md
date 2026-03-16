# Difference Between Arrow Functions and Regular Functions in JavaScript

## Introduction

JavaScript provides multiple ways to create functions.

Two common types are:

```

Regular Functions
Arrow Functions

```

Both perform similar tasks but behave differently in some situations.

---

# Regular Function

A regular function is declared using the `function` keyword.

## Example

```javascript
function add(a, b) {
  return a + b;
}

console.log(add(2, 3));
````

Output

```
5
```

---

# Arrow Function

Arrow functions use the `=>` syntax and provide a shorter way to write functions.

## Example

```javascript
const add = (a, b) => {
  return a + b;
};

console.log(add(2, 3));
```

Output

```
5
```

Shorter version:

```javascript
const add = (a, b) => a + b;
```

---

# Difference 1: Syntax

Regular functions use the `function` keyword.

```javascript
function greet(name) {
  return "Hello " + name;
}
```

Arrow functions use `=>`.

```javascript
const greet = (name) => {
  return "Hello " + name;
};
```

---

# Difference 2: Implicit Return

Arrow functions can return values without using the `return` keyword.

```javascript
const square = (x) => x * x;

console.log(square(4));
```

Output

```
16
```

Regular functions always require `return`.

```javascript
function square(x) {
  return x * x;
}
```

---

# Difference 3: `this` Behavior

Regular functions have their own `this`.

Arrow functions inherit `this` from the surrounding scope.

## Regular Function Example

```javascript
const user = {
  name: "Sudheer",

  greet: function () {
    console.log(this.name);
  }
};

user.greet();
```

Output

```
Sudheer
```

## Arrow Function Example

```javascript
const user = {
  name: "Sudheer",

  greet: () => {
    console.log(this.name);
  }
};

user.greet();
```

Output

```
undefined
```

Arrow functions do not bind their own `this`.

---

# Difference 4: Constructor Usage

Regular functions can be used as constructors.

```javascript
function Person(name) {
  this.name = name;
}

const user = new Person("Sudheer");

console.log(user.name);
```

Arrow functions cannot be used as constructors.

```javascript
const Person = (name) => {
  this.name = name;
};

const user = new Person("Sudheer");
```

This will cause an error.

---

# Difference 5: Arguments Object

Regular functions have an `arguments` object.

```javascript
function printArgs() {
  console.log(arguments);
}

printArgs(1, 2, 3);
```

Arrow functions do not have `arguments`.

Instead use rest parameters.

```javascript
const printArgs = (...args) => {
  console.log(args);
};

printArgs(1, 2, 3);
```

---

# When to Use Arrow Functions

Arrow functions are useful for:

```
Short functions
Array methods (map, filter, reduce)
Callbacks
```

Example:

```javascript
const numbers = [1, 2, 3];

const doubled = numbers.map(n => n * 2);

console.log(doubled);
```

---

# Summary

| Feature          | Regular Function   | Arrow Function  |
| ---------------- | ------------------ | --------------- |
| Syntax           | `function` keyword | `=>`            |
| this binding     | Own `this`         | Inherits `this` |
| Constructor      | Yes                | No              |
| arguments object | Available          | Not available   |
| Implicit return  | No                 | Yes             |

Both function types are useful depending on the situation.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---
