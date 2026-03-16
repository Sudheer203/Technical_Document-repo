# JavaScript Scopes

## Introduction

Scope in JavaScript defines **where a variable can be accessed in a program**.

JavaScript mainly has these scopes:

1. Global Scope
2. Function Scope
3. Block Scope
4. Lexical Scope

---

# 1. Global Scope

A variable declared **outside any function or block** belongs to the global scope.

It can be accessed **anywhere in the program**.

Example:

```javascript
let message = "Hello World";

function showMessage() {
  console.log(message);
}

showMessage();
console.log(message);
````

Output:

```
Hello World
Hello World
```

Global variables should be used **carefully** because they can be changed from anywhere.

---

# 2. Function Scope

Variables declared inside a **function** can only be accessed inside that function.

Example:

```javascript
function greet() {
  let name = "Sudheer";
  console.log(name);
}

greet();
console.log(name);
```

Output:

```
Sudheer
ReferenceError: name is not defined
```

The variable `name` exists **only inside the function**.

---

# 3. Block Scope

Variables declared with **let** and **const** follow block scope.

A block is defined using `{ }`.

Example:

```javascript
{
  let age = 25;
  console.log(age);
}

console.log(age);
```

Output:

```
25
ReferenceError: age is not defined
```

Block scope is common in:

```javascript
if
for
while
```

Example:

```javascript
if (true) {
  const city = "Bangalore";
  console.log(city);
}

console.log(city);
```
---

# 4. Lexical Scope

JavaScript uses **lexical scope**, meaning a function can access variables from its **parent scope**.

Example:

```javascript
function outer() {
  let language = "JavaScript";

  function inner() {
    console.log(language);
  }

  inner();
}

outer();
```

Output:

```
JavaScript
```

The inner function accesses the variable from the outer function.

---

# Example Combining Scopes

```javascript
let globalVar = "I am global";

function test() {
  let functionVar = "I am inside function";

  if (true) {
    let blockVar = "I am inside block";

    console.log(globalVar);
    console.log(functionVar);
    console.log(blockVar);
  }
}

test();
```

Output:

```
I am global
I am inside function
I am inside block
```

---

# Summary

JavaScript scope controls **variable visibility and access**.

Main scopes:

* Global Scope
* Function Scope
* Block Scope
* Lexical Scope

Using correct scope helps **avoid bugs and keeps code clean**.

---

# Reference

MDN Web Docs

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

---