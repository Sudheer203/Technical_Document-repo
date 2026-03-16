# Spread Operator in JavaScript

## Introduction

The **spread operator (`...`)** is used to **expand elements of an array or properties of an object**.

It helps to:

- copy arrays
- merge arrays
- copy objects
- merge objects
- pass multiple arguments to functions

It improves code readability and supports **immutable operations**.

---

Example:

```javascript
const numbers = [1, 2, 3];

const newNumbers = [...numbers];

console.log(newNumbers);
```

Output

```
[1, 2, 3]
```

---

# 1. Copying an Array (Immutable)

Spread operator can create a **new copy of an array**.

```javascript
const numbers = [1, 2, 3];

const copy = [...numbers];

copy.push(4);

console.log(numbers);
console.log(copy);
```

Output

```
[1, 2, 3]
[1, 2, 3, 4]
```

The original array is **not modified**.

---

# 2. Merging Arrays

Spread operator can combine arrays.

```javascript
const arr1 = [1, 2];
const arr2 = [3, 4];

const merged = [...arr1, ...arr2];

console.log(merged);
```

Output

```
[1, 2, 3, 4]
```

---

# 3. Adding Elements to an Array

Spread can add elements while creating a new array.

```javascript
const numbers = [2, 3];

const newNumbers = [1, ...numbers, 4];

console.log(newNumbers);
```

Output

```
[1, 2, 3, 4]
```

---

# 4. Copying an Object (Immutable)

Spread operator can copy object properties.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const copyUser = { ...user };

console.log(copyUser);
```

Output

```
{ name: "Sudheer", age: 25 }
```

---

# 5. Merging Objects

Spread operator can combine objects.

```javascript
const user = {
  name: "Sudheer"
};

const details = {
  age: 25,
  city: "Hyderabad"
};

const profile = { ...user, ...details };

console.log(profile);
```

Output

```
{ name: "Sudheer", age: 25, city: "Hyderabad" }
```

---

# 6. Updating Object Properties

Spread can update values while keeping the original object unchanged.

```javascript
const user = {
  name: "Sudheer",
  age: 25
};

const updatedUser = { ...user, age: 26 };

console.log(user);
console.log(updatedUser);
```

Output

```
{ name: "Sudheer", age: 25 }
{ name: "Sudheer", age: 26 }
```

---

# 7. Using Spread with Functions

Spread can pass array elements as function arguments.

```javascript
function add(a, b, c) {
  return a + b + c;
}

const numbers = [1, 2, 3];

console.log(add(...numbers));
```

Output

```
6
```

---

# Mutable vs Immutable Behavior

Spread operator usually supports **immutable operations**.

Example:

```javascript
const arr = [1, 2, 3];

const newArr = [...arr];

newArr.push(4);

console.log(arr);
console.log(newArr);
```

Output

```
[1, 2, 3]
[1, 2, 3, 4]
```

Original data remains unchanged.

---

# Summary

The spread operator expands arrays or objects into individual elements.

Common uses:

| Use Case           | Example        |
| ------------------ | -------------- |
| Copy array         | `[...arr]`     |
| Merge arrays       | `[...a, ...b]` |
| Copy object        | `{...obj}`     |
| Merge objects      | `{...a, ...b}` |
| Function arguments | `fn(...arr)`   |

The spread operator helps write **clean, readable, and immutable JavaScript code**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---