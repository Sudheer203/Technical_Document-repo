# Truthy and Falsy Values in JavaScript

## Introduction

In **JavaScript**, every value is evaluated as **true** or **false** when used in a condition.

Values that behave like **true** are called **truthy values**.  
Values that behave like **false** are called **falsy values**.

Example:

```javascript
if ("hello") {
  console.log("This runs");
}
````

The string `"hello"` is **truthy**, so the code runs.

---

# Falsy Values

JavaScript has **only a few falsy values**.

```
false
0
-0
0n
""
null
undefined
NaN
```

If any of these values are used in a condition, they behave like `false`.

### Example

```javascript
if (0) {
  console.log("This will not run");
}
```

Example:

```javascript
if ("") {
  console.log("This will not run");
}
```

Example:

```javascript
if (null) {
  console.log("This will not run");
}
```

---

# Truthy Values

All values that are **not falsy** are considered **truthy**.

Common truthy values include:

```
true
"hello"
"0"
[]
{}
1
-5
Infinity
```

### Example

```javascript
if ("JavaScript") {
  console.log("This runs");
}
```

Output

```
This runs
```

Example:

```javascript
if ([]) {
  console.log("Arrays are truthy");
}
```

Example:

```javascript
if ({}) {
  console.log("Objects are truthy");
}
```

---

# Example with Conditions

```javascript
let username = "Sudheer";

if (username) {
  console.log("User exists");
}
```

Output

```
User exists
```

If the value were empty:

```javascript
let username = "";

if (username) {
  console.log("User exists");
} else {
  console.log("No user");
}
```

Output

```
No user
```

---

# Boolean Conversion

JavaScript converts values to boolean automatically.

We can also convert manually using `Boolean()`.

Example:

```javascript
console.log(Boolean(1));
console.log(Boolean(0));
console.log(Boolean("hello"));
console.log(Boolean(""));
console.log(Boolean(null));
```

Output

```
true
false
true
false
false
```

---

# Practical Example

Checking if a user entered a value.

```javascript
function login(username) {
  if (!username) {
    console.log("Username required");
    return;
  }

  console.log("Welcome " + username);
}

login("");
login("Sudheer");
```

Output

```
Username required
Welcome Sudheer
```

---

# Summary

Truthy and falsy values control how JavaScript evaluates conditions.

Falsy values are limited and include:

```
false
0
""
null
undefined
NaN
```

All other values are **truthy**.

Understanding truthy and falsy values helps write **clean and concise conditional code**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)

---
