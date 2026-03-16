# let, var, const in JavaScript

## Introduction

JavaScript provides three keywords to declare variables:

```
var
let
const
````

They differ in **scope, redeclaration, reassignment, and hoisting behavior**.

---

# 1. var

`var` is the **old way** to declare variables in JavaScript.

It is **function scoped**, not block scoped.

### Example

```javascript
var name = "Sudheer";
console.log(name);
````

### Function Scope

```javascript
function test() {
  var x = 10;
  console.log(x);
}

test();
console.log(x); 
```

Output

```
10
ReferenceError
```

### No Block Scope

```javascript
if (true) {
  var number = 100;
}

console.log(number);
```

Output

```
100
```

### Redeclaration Allowed

```javascript
var city = "Delhi";
var city = "Mumbai";

console.log(city);
```

---

# 2. let

`let` was introduced in **ES6 (2015)**.

It follows **block scope**.

### Example

```javascript
let age = 25;
console.log(age);
```

### Block Scope

```javascript
if (true) {
  let score = 90;
  console.log(score);
}

console.log(score);
```

Output

```
90
ReferenceError
```

### Reassignment Allowed

```javascript
let count = 5;
count = 10;

console.log(count);
```

### Redeclaration Not Allowed

```javascript
let value = 10;
let value = 20;
```

Output

```
SyntaxError
```

---

# 3. const

`const` declares **constant variables**.

The value **cannot be reassigned**.

### Example

```javascript
const pi = 3.14;
console.log(pi);
```

### Reassignment Not Allowed

```javascript
const number = 10;
number = 20;
```

Output

```
TypeError
```

### Must Be Initialized

```javascript
const age;
```

Output

```
SyntaxError
```

### Objects with const

The reference cannot change, but properties can.

```javascript
const user = {
  name: "Sudheer"
};

user.name = "Ravi";

console.log(user);
```

Output

```
{ name: "Ravi" }
```

---

# Hoisting Behavior

### var

`var` is **hoisted and initialized with undefined**.

```javascript
console.log(a);
var a = 10;
```

Output

```
undefined
```

### let and const

`let` and `const` are hoisted but **not initialized**.

```javascript
console.log(b);
let b = 20;
```

Output

```
ReferenceError
```

---

# Comparison

| Feature       | var      | let         | const       |
| ------------- | -------- | ----------- | ----------- |
| Scope         | Function | Block       | Block       |
| Redeclaration | Allowed  | Not Allowed | Not Allowed |
| Reassignment  | Allowed  | Allowed     | Not Allowed |
| Hoisting      | Yes      | Yes (TDZ)   | Yes (TDZ)   |

---

# Example Using All Three

```javascript
var a = 1;
let b = 2;
const c = 3;

function demo() {
  var x = 10;

  if (true) {
    let y = 20;
    const z = 30;

    console.log(x, y, z);
  }
}

demo();
```

---

# Summary

`var`, `let`, and `const` are used to declare variables in JavaScript.

* `var` → function scoped and older syntax
* `let` → block scoped and reassignable
* `const` → block scoped and cannot be reassigned

Modern JavaScript mostly uses **let and const**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

