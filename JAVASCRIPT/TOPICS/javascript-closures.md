# Closures in JavaScript

## Introduction

A **closure** happens when a function remembers variables from its **outer scope**, even after the outer function has finished executing.

Closures allow functions to **access and preserve data** from their surrounding environment.

---

# Basic Example

```javascript
function outer() {
  const message = "Hello from closure";

  function inner() {
    console.log(message);
  }

  return inner;
}

const fn = outer();
fn();
```

Output

```
Hello from closure
```

Explanation

```
inner() remembers the variable message
even after outer() has finished running
```

---

# Example 2: Counter Using Closure

Closures are often used to **maintain private state**.

```javascript
function createCounter() {
  let count = 0;

  return function () {
    count++;
    console.log(count);
  };
}

const counter = createCounter();

counter();
counter();
counter();
```

Output

```
1
2
3
```

Explanation

```
count is preserved inside the closure
each function call updates the same variable
```

---

# Example 3: Data Privacy

Closures help hide variables from the global scope.

```javascript
function createUser() {
  let password = "12345";

  return {
    checkPassword(input) {
      return input === password;
    }
  };
}

const user = createUser();

console.log(user.checkPassword("12345"));
```

Output

```
true
```

The variable `password` is **private** and cannot be accessed directly.

---

# Example 4: Closure with Function Parameters

```javascript
function multiply(x) {
  return function (y) {
    return x * y;
  };
}

const double = multiply(2);

console.log(double(5));
```

Output

```
10
```

Explanation

```
inner function remembers the value of x
```

---

# Example 5: Closure in Loops

```javascript
function createFunctions() {
  const funcs = [];

  for (let i = 0; i < 3; i++) {
    funcs.push(function () {
      console.log(i);
    });
  }

  return funcs;
}

const list = createFunctions();

list[0]();
list[1]();
list[2]();
```

Output

```
0
1
2
```

Each function **remembers its own value of `i`**.

---

# How Closures Work

```
Function created
↓
Function remembers outer variables
↓
Outer function finishes
↓
Inner function still accesses those variables
```

---

# Common Use Cases

Closures are used for:

```
private variables
function factories
data encapsulation
callbacks and event handlers
```

Example:

```javascript
function greeting(name) {
  return function () {
    console.log("Hello " + name);
  };
}

const greetSudheer = greeting("Sudheer");

greetSudheer();
```

Output

```
Hello Sudheer
```

---

# Summary

A **closure** is a function that remembers variables from its outer scope.

Key idea

```
Function + its lexical environment = closure
```

Closures help create:

```
private data
stateful functions
clean modular code
```

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---

