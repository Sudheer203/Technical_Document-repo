# Mutable and Immutable Methods in JavaScript

## Introduction

In JavaScript, some methods **modify the original data**, while others **return new data without changing the original**.

These behaviors are called:

```

Mutable
Immutable

```

Understanding the difference helps avoid **unexpected bugs** and improves code reliability.

---

# Mutable Methods

**Mutable methods change the original array or object.**

After calling a mutable method, the original data is modified.

## Example: Array.push()

```javascript
const numbers = [1, 2, 3];

numbers.push(4);

console.log(numbers);
```

Output

```id="p3z3tp"
[1, 2, 3, 4]
```

The original array changed.

---

## Example: Array.pop()

```javascript id="a9ywhg"
const numbers = [1, 2, 3];

numbers.pop();

console.log(numbers);
```

Output

```id="92wstq"
[1, 2]
```

---

## Example: Array.splice()

```javascript id="f2r6z0"
const numbers = [1, 2, 3, 4];

numbers.splice(1, 2);

console.log(numbers);
```

Output

```id="ycnm1b"
[1, 4]
```

---

## Example: Array.sort()

```javascript id="96zhru"
const numbers = [4, 1, 3, 2];

numbers.sort();

console.log(numbers);
```

Output

```id="lce2y1"
[1, 2, 3, 4]
```

---

# Immutable Methods

**Immutable methods do not modify the original data.**
Instead, they return **a new array or value**.

---

## Example: Array.map()

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(num => num * 2);

console.log(result);
console.log(numbers);
```

Output

```id="6cnit2"
[2, 4, 6]
[1, 2, 3]
```

The original array remains unchanged.

---

## Example: Array.filter()

```javascript id="o5qpo6"
const numbers = [1, 2, 3, 4];

const even = numbers.filter(num => num % 2 === 0);

console.log(even);
console.log(numbers);
```

Output

```id="feyu5m"
[2, 4]
[1, 2, 3, 4]
```

---

## Example: Array.slice()

```javascript id="56bnt1"
const numbers = [10, 20, 30, 40];

const part = numbers.slice(1, 3);

console.log(part);
console.log(numbers);
```

Output

```id="53bxny"
[20, 30]
[10, 20, 30, 40]
```

---

## Example: Array.concat()

```javascript id="j3zo9s"
const arr1 = [1, 2];
const arr2 = [3, 4];

const result = arr1.concat(arr2);

console.log(result);
console.log(arr1);
```

Output

```id="bzk5mw"
[1, 2, 3, 4]
[1, 2]
```

---

# Quick Comparison

| Type      | Behavior              | Example Methods            |
| --------- | --------------------- | -------------------------- |
| Mutable   | Changes original data | push, pop, splice, sort    |
| Immutable | Returns new data      | map, filter, slice, concat |

---

# Practical Example

```javascript
const numbers = [1, 2, 3];

// immutable operation
const doubled = numbers.map(n => n * 2);

// mutable operation
numbers.push(4);

console.log(doubled);
console.log(numbers);
```

Output

```id="c9nqaa"
[2, 4, 6]
[1, 2, 3, 4]
```

---

# Summary

Mutable methods **change the original data**, while immutable methods **return new data without modifying the original**.

Modern JavaScript development often prefers **immutable methods** because they make code **predictable and easier to debug**.

---

# Reference

MDN Web Docs
[https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---