# Difference Between `null` and `undefined` in JavaScript

## Introduction

`null` and `undefined` both represent **absence of value** in JavaScript, but they are used in **different situations**.

```

undefined → value not assigned
null → value intentionally set to empty

```

Understanding the difference helps avoid **logical errors in programs**.

---

# undefined

`undefined` means a variable **has been declared but not assigned a value**.

## Example

```javascript
let user;

console.log(user);
```

Output

```
undefined
```

JavaScript automatically assigns `undefined`.

---

## Example: Missing Function Argument

```javascript
function greet(name) {
  console.log(name);
}

greet();
```

Output

```
undefined
```

Because no argument was passed.

---

## Example: Accessing Missing Object Property

```javascript
const user = {
  name: "Sudheer"
};

console.log(user.age);
```

Output

```
undefined
```

The property `age` does not exist.

---

# null

`null` means **no value**, but it is **intentionally assigned by the developer**.

## Example

```javascript
let user = null;

console.log(user);
```

Output

```
null
```

This means the value is **empty on purpose**.

---

## Example: Resetting a Value

```javascript
let session = {
  user: "Sudheer"
};

session.user = null;

console.log(session);
```

Output

```
{ user: null }
```

The user value was intentionally cleared.

---

# Type Difference

```javascript
console.log(typeof undefined);
console.log(typeof null);
```

Output

```
undefined
object
```

Note: `typeof null` returning `"object"` is a **historical JavaScript bug**, but it remains for compatibility.

---

# Comparison Example

```javascript
console.log(null == undefined);
console.log(null === undefined);
```

Output

```
true
false
```

Explanation

```
== allows type conversion
=== checks both type and value
```

---

# Practical Example

```javascript
function getUser(user) {
  if (user === undefined) {
    console.log("User not provided");
  } else if (user === null) {
    console.log("User intentionally empty");
  } else {
    console.log("User exists");
  }
}

getUser();
getUser(null);
getUser("Sudheer");
```

Output

```
User not provided
User intentionally empty
User exists
```

---

# Key Differences

| Feature       | undefined          | null                      |
| ------------- | ------------------ | ------------------------- |
| Meaning       | value not assigned | value intentionally empty |
| Set by        | JavaScript         | Developer                 |
| Type          | undefined          | object                    |
| Default value | Yes                | No                        |

---

# Summary

`undefined` means **a variable exists but has no assigned value**.

`null` means **the value is intentionally empty**.

Best practice:

```
Use undefined for uninitialized variables.
Use null when you intentionally want an empty value.
```

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---