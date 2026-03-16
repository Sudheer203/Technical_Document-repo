# Why `value === undefined` Is Better Than `!value` in JavaScript

## Introduction

When checking if a variable is **undefined**, developers sometimes use:

```

!value

```

But the correct and safer way is:

```

value === undefined

```

Because `!value` checks **many falsy values**, not just `undefined`.

---

# Falsy Values in JavaScript

JavaScript treats several values as **false in boolean context**.

```

false
0
""
null
undefined
NaN

```

Using `!value` will return **true for all of these**, not just `undefined`.

---

# Problem With `!value`

## Example

```javascript
let value = 0;

if (!value) {
  console.log("Value is missing");
}
````

Output

```
Value is missing
```

But `0` is **not undefined**.
The condition gives the **wrong result**.

---

# Another Example

```javascript
let value = "";

if (!value) {
  console.log("Value is missing");
}
```

Output

```
Value is missing
```

But an empty string may be **valid input**.

---

# Correct Approach: `value === undefined`

This checks **only one specific value**.

## Example

```javascript
let value = 0;

if (value === undefined) {
  console.log("Value is undefined");
}
```

Output

```
(no output)
```

This works correctly because `0` is not `undefined`.

---

# Example With Real Undefined Value

```javascript
let value;

if (value === undefined) {
  console.log("Value is undefined");
}
```

Output

```
Value is undefined
```

---

# Practical Example: Function Input Validation

### Using `!value` (Problem)

```javascript
function printPrice(price) {
  if (!price) {
    console.log("Price is missing");
  }
}

printPrice(0);
```

Output

```
Price is missing
```

But `0` could be a valid price.

---

### Using `value === undefined` (Correct)

```javascript
function printPrice(price) {
  if (price === undefined) {
    console.log("Price is missing");
  }
}

printPrice(0);
```

Output

```
(no output)
```

---

# When `!value` Is Useful

`!value` is useful when checking **any falsy value**.

Example:

```javascript
let username = "";

if (!username) {
  console.log("Username required");
}
```

Output

```
Username required
```

---

# Comparison

| Check                 | Meaning                    |
| --------------------- | -------------------------- |
| `!value`              | value is any falsy value   |
| `value === undefined` | value is exactly undefined |

---

# Summary

`!value` checks **multiple falsy values**, which can cause bugs.

```
false
0
""
null
undefined
NaN
```

Using `value === undefined` ensures the condition **only checks for undefined**.

Best practice:

```
Use `value === undefined` when checking if a variable is undefined.
```

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---